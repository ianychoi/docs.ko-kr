---
title: '방법: 채널 팩터리를 사용하여 비동기적으로 작업 호출'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: c288df6059cfe1cd1f4ff35cebffafd3fddb38d1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257537"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="d2b51-102">방법: 채널 팩터리를 사용하여 비동기적으로 작업 호출</span><span class="sxs-lookup"><span data-stu-id="d2b51-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>

<span data-ttu-id="d2b51-103">이 항목에서는 <xref:System.ServiceModel.ChannelFactory%601> 기반 클라이언트 애플리케이션을 사용하여 클라이언트에서 서비스 작업에 비동기적으로 액세스하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="d2b51-104">서비스를 호출하기 위해 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 개체를 사용하는 경우 이벤트 구동 비동기 호출 모델을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="d2b51-105">자세한 내용은 [방법: 비동기적으로 서비스 작업 호출](how-to-call-wcf-service-operations-asynchronously.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2b51-105">For more information, see [How to: Call Service Operations Asynchronously](how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="d2b51-106">이벤트 기반 비동기 호출 모델에 대 한 자세한 내용은 [EAP (이벤트 기반 비동기 패턴](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2b51-106">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="d2b51-107">이 항목에서 설명하는 서비스에서는 `ICalculator` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="d2b51-108">클라이언트는 이 인터페이스의 작업을 비동기적으로 호출할 수 있는데, 이는 `Add` 등의 작업이 호출을 시작하는 `BeginAdd`와 작업 완료 시 결과를 검색하는 `EndAdd`라는 두 개의 메서드로 나뉨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="d2b51-109">서비스에서 비동기적으로 작업을 구현 하는 방법을 보여 주는 예제는 [방법: 비동기 서비스 작업 구현](../how-to-implement-an-asynchronous-service-operation.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2b51-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="d2b51-110">동기 및 비동기 작업에 대 한 자세한 내용은 [동기 및 비동기 작업](../synchronous-and-asynchronous-operations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2b51-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d2b51-111">절차</span><span class="sxs-lookup"><span data-stu-id="d2b51-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="d2b51-112">WCF 서비스 작업을 비동기적으로 호출하려면</span><span class="sxs-lookup"><span data-stu-id="d2b51-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="d2b51-113">다음 명령에 표시 된 것과 같은 옵션을 사용 하 여 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 도구를 실행 `/async` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="d2b51-114">그러면 작업에 서비스 계약의 비동기 클라이언트 버전이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2. <span data-ttu-id="d2b51-115">다음 샘플 코드와 같이 비동기 작업이 완료될 때 호출할 콜백 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. <span data-ttu-id="d2b51-116">서비스 작업에 비동기적으로 액세스하려면 다음 샘플 코드에서와 같이, 클라이언트를 만들고 `Begin[Operation]`(예: `BeginAdd`)을 호출하며 콜백 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="d2b51-117">콜백 함수가 실행될 때 클라이언트는 결과를 검색하기 위해 `End<operation>`(예: `EndAdd`)을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b51-118">예제</span><span class="sxs-lookup"><span data-stu-id="d2b51-118">Example</span></span>  

 <span data-ttu-id="d2b51-119">이전 절차에 사용된 클라이언트 코드와 함께 사용되는 서비스는 다음 코드에서와 같이 `ICalculator` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="d2b51-120">서비스 쪽에서는 `Add` `Subtract` 이전 클라이언트 단계가 클라이언트에서 비동기적으로 호출 되는 경우에도 계약의 및 작업이 WCF (Windows Communication Foundation) 런타임에 의해 동기적으로 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="d2b51-121">클라이언트가 `Multiply` 및 `Divide` 작업을 비동기적으로 호출하더라도 서비스 쪽에서는 이 작업을 사용하여 비동기적으로 서비스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="d2b51-122">다음 예제에서는 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="d2b51-123">.NET Framework 비동기 패턴 구현과 함께이 속성 설정은 런타임에 작업을 비동기적으로 호출 하도록 런타임에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2b51-123">This property setting, in combination with the implementation of the .NET Framework asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
