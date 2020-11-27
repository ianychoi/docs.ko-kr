---
title: 서비스 계약 구현
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 121922e3de62653babdac084d6bd226f7263e33c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262738"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="1f930-102">서비스 계약 구현</span><span class="sxs-lookup"><span data-stu-id="1f930-102">Implementing Service Contracts</span></span>

<span data-ttu-id="1f930-103">서비스는 클라이언트에서 사용할 수 있는 기능을 하나 이상의 엔드포인트에 노출하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="1f930-104">서비스를 만들려면 WCF (Windows Communication Foundation) 계약을 구현 하는 클래스를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="1f930-105">이 작업은 다음 두 가지 방법 중 한 가지로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-105">You can do this in one of two ways.</span></span> <span data-ttu-id="1f930-106">계약을 인터페이스로 따로 정의한 다음 해당 인터페이스를 구현하는 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="1f930-107">또는 클래스 자체에 <xref:System.ServiceModel.ServiceContractAttribute> 특성을 두고 서비스 클라이언트에서 사용할 수 있는 메서드에 <xref:System.ServiceModel.OperationContractAttribute> 특성을 두어 클래스와 계약을 직접 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="1f930-108">서비스 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="1f930-108">Creating a service class</span></span>  

 <span data-ttu-id="1f930-109">다음은 별도로 정의된 `IMath` 계약을 구현하는 서비스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="1f930-110">또는 서비스에서 직접 계약을 노출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="1f930-111">다음은 `MathService` 계약을 정의 및 구현하는 서비스 클래스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="1f930-112">계약 이름이 다르기 때문에 앞의 서비스에서 다른 계약을 노출한다는 것에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="1f930-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="1f930-113">첫째 경우에서 노출되는 계약의 이름은 "`IMath`"인데 둘째 경우에서 계약의 이름은 "`MathService`"입니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="1f930-114">서비스 및 작업 구현 수준에서 동시성 및 인스턴스 등을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="1f930-115">자세한 내용은 [서비스 디자인 및 구현](designing-and-implementing-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f930-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="1f930-116">서비스 계약을 구현하고 나면 서비스에 하나 이상의 엔드포인트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f930-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="1f930-117">자세한 내용은 [끝점 만들기 개요](endpoint-creation-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f930-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="1f930-118">서비스를 실행 하는 방법에 대 한 자세한 내용은 [호스팅 서비스](hosting-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f930-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f930-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f930-119">See also</span></span>

- [<span data-ttu-id="1f930-120">서비스 디자인 및 구현</span><span class="sxs-lookup"><span data-stu-id="1f930-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="1f930-121">방법: Contract 클래스를 사용하여 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="1f930-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="1f930-122">방법: Contract 인터페이스를 사용하여 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="1f930-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="1f930-123">서비스 런타임 동작 지정</span><span class="sxs-lookup"><span data-stu-id="1f930-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
