---
title: 오케스트레이션 패턴 - 서버리스 앱
description: Azure Durable Functions pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 6c5f6aaedbc13c47289e102bb59f7b066525b107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171665"
---
# <a name="orchestration-patterns"></a>오케스트레이션 패턴

Durable Functions를 사용하면 서버리스 환경에서 장기 불연속 작업으로 구성된 상태 저장 워크플로를 쉽게 만들 수 있습니다. Durable Functions는 워크플로의 진행률을 추적하고 정기적으로 실행 기록의 검사점을 설정할 수 있으므로, 몇 가지 흥미로운 패턴을 구현하는 데 적합합니다.

## <a name="function-chaining"></a>함수 체이닝

일반적인 순차적 프로세스에서 작업은 특정 순서로 실행해야 합니다. 선택적으로, 이후 작업이 이전 함수의 출력을 필요로 할 수 있습니다. 작업 순서 지정에 대한 이 종속성은 함수 실행 체인을 만듭니다.

Durable Functions를 사용하여 이 워크플로 패턴을 구현하는 이점은 검사점 설정을 수행할 수 있다는 것입니다. 서버에서 충돌이 발생하거나 네트워크 시간이 초과되거나 다른 문제가 발생하는 경우 Durable Functions는 마지막으로 알려진 상태에서 다시 시작하고 다른 서버에 있는 경우에도 워크플로를 계속 실행할 수 있습니다.

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

위의 코드 샘플에서 `CallActivityAsync` 함수는 데이터 센터의 가상 머신에서 지정된 작업을 실행하는 작업을 담당합니다. await가 반환되고 기본 작업이 완료되면 기록 테이블에 실행이 기록됩니다. 오케스트레이터 함수의 코드는 작업 병렬 라이브러리의 친숙한 구문과 async/await 키워드를 사용할 수 있습니다.

다음 코드는 `ProcessPayment` 메서드를 간단하게 보여 주는 예제입니다.

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a>비동기 HTTP API

경우에 따라 워크플로는 완료하는 데 비교적 오랜 시간이 걸리는 작업을 포함할 수 있습니다. Blob 스토리지로 미디어 파일 백업을 시작하는 프로세스를 상상해 보세요. 미디어 파일의 크기와 용량에 따라이 백업 프로세스를 완료하는 데 몇 시간이 걸릴 수 있습니다.

이 시나리오에서는 실행 중인 워크플로의 상태를 확인하는 `DurableOrchestrationClient`의 기능이 유용합니다. `HttpTrigger`를 사용하여 워크플로를 시작하는 경우 `CreateCheckStatusResponse` 메서드를 사용하여 `HttpResponseMessage` 인스턴스를 반환할 수 있습니다. 이 응답은 실행 중인 프로세스의 상태를 확인하는 데 사용할 수 있는 페이로드의 URI를 클라이언트에 제공합니다.

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

아래 결과 예제는 응답 페이로드의 구조를 보여줍니다.

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

기본 설정된 HTTP 클라이언트를 사용하여 statusQueryGetUri의 URI에 GET 요청을 수행하여 실행 중인 워크플로의 상태를 검사할 수 있습니다. 반환된 상태 응답은 다음 코드와 유사합니다.

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

프로세스가 계속되면 상태 응답이 **실패** 또는 **완료**로 변경됩니다. 성공적으로 완료되면 페이로드의 **출력** 속성에 반환된 데이터가 포함됩니다.

## <a name="monitoring"></a>모니터링

간단한 되풀이 작업의 경우 Azure Functions는 CRON 식을 기반으로 예약할 수 있는 `TimerTrigger`를 제공합니다. 타이머가 간단하고 수명이 짧은 작업에 적합하지만, 보다 유연한 일정 예약을 수행해야 하는 시나리오가 있을 수 있습니다. 이 시나리오에서는 모니터링 패턴 및 Durable Functions가 유용할 수 있습니다.

Durable Functions를 사용하면 유연한 일정 예약 간격과 수명 관리가 가능하고 단일 오케스트레이션 함수에서 여러 모니터 프로세스를 만들 수 있습니다. 이 기능에 대한 한 가지 사용 사례는 특정 임계값이 충족되면 완료되는 주가 변동 감시자를 만드는 것입니다.

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

`DurableOrchestrationContext`의 `CreateTimer` 메서드는 다음 번 루프 호출 일정을 설정하여 주가 변동 여부를 확인합니다. `DurableOrchestrationContext`에는 UTC의 현재 DateTime 값을 가져오기 위한 `CurrentUtcDateTime` 속성도 있습니다. 이 속성은 테스트를 위해 쉽게 모의할 수 있으므로 `DateTime.UtcNow` 대신 사용하는 것이 좋습니다.

## <a name="recommended-resources"></a>권장되는 리소스

- [Azure Durable Functions](/azure/azure-functions/durable-functions-overview)
- [.NET Core 및 .NET Standard의 유닛 테스트](../../core/testing/index.md)

>[!div class="step-by-step"]
>[이전](durable-azure-functions.md)
>[다음](serverless-business-scenarios.md)
