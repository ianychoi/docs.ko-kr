---
description: '자세한 정보: 방법: Request-Reply 계약 만들기'
title: '방법: 요청-회신 계약 만들기'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: f5e63538a405aa451ffd3be114485604c00fa407
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734700"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="eb391-103">방법: 요청-회신 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="eb391-103">How to: Create a Request-Reply Contract</span></span>

<span data-ttu-id="eb391-104">요청-회신 계약에서는 회신을 반환하는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-104">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="eb391-105">회신은 이 계약 조건 하의 요청에 따라 전송되고 상호 관련되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-105">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="eb391-106">메서드가 회신을 반환하지 않는 경우(C#에서는 `void`, Visual Basic에서는 `Sub`)에도 인프라에서 빈 메시지를 만들어 호출자에게 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-106">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="eb391-107">빈 회신 메시지가 전송되지 않도록 하려면 작업에 대한 단방향 계약을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-107">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="eb391-108">요청-회신 계약을 만들려면</span><span class="sxs-lookup"><span data-stu-id="eb391-108">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="eb391-109">선택한 프로그래밍 언어로 인터페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-109">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="eb391-110">인터페이스에 <xref:System.ServiceModel.ServiceContractAttribute> 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="eb391-111">클라이언트가 호출할 수 있는 각 메서드에 <xref:System.ServiceModel.OperationContractAttribute> 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="eb391-112">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-112">Optional.</span></span> <span data-ttu-id="eb391-113">빈 회신 메시지가 전송되지 않도록 하려면 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성의 값을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-113">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="eb391-114">기본적으로 모든 작업은 요청-회신 계약 하에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-114">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb391-115">예제</span><span class="sxs-lookup"><span data-stu-id="eb391-115">Example</span></span>  

 <span data-ttu-id="eb391-116">다음 샘플에서는 `Add` 및 `Subtract` 메서드를 제공하는 계산기 서비스에 대한 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-116">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="eb391-117">`Multiply` 메서드는 <xref:System.ServiceModel.OperationContractAttribute> 클래스에 의해 표시되지 않으므로 계약의 일부가 아니며, 따라서 클라이언트에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-117">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="eb391-118">작업 계약을 지정 하는 방법에 대 한 자세한 내용은 <xref:System.ServiceModel.OperationContractAttribute> 클래스 및 속성을 참조 하세요 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> .</span><span class="sxs-lookup"><span data-stu-id="eb391-118">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="eb391-119"><xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute> 특성을 적용하면 서비스를 배포한 후에 WSDL(웹 서비스 기술 언어) 문서에서 서비스 계약 정의가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-119">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="eb391-120">서비스의 HTTP 기본 주소에 `?wsdl`을 추가하면 문서가 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-120">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="eb391-121">예를 들면 `http://microsoft/CalculatorService?wsdl`과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb391-121">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb391-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb391-122">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="eb391-123">서비스 계약 디자인</span><span class="sxs-lookup"><span data-stu-id="eb391-123">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="eb391-124">방법: 이중 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="eb391-124">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
