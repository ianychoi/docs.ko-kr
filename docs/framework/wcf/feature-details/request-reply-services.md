---
title: 요청-회신 서비스
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 10b82e859369dae4f57e0e13782e2375a304ab02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295524"
---
# <a name="request-reply-services"></a><span data-ttu-id="4a825-102">요청-회신 서비스</span><span class="sxs-lookup"><span data-stu-id="4a825-102">Request-Reply Services</span></span>

<span data-ttu-id="4a825-103">요청-회신 서비스는 WCF (Windows Communication Foundation)의 기본 작업 계약 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4a825-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4a825-104">클라이언트는 서비스 작업에 대한 호출을 만들고 서비스로부터 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4a825-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="4a825-105">사용자는 서비스 작업에 대한 호출을 동기적으로(클라이언트가 서비스 또는 호출 시간으로부터 응답을 받을 때까지 차단하는 경우) 또는 비동기적으로(클라이언트가 서비스 작업에 대한 호출을 만들고, 작업을 계속하고, 다른 스레드의 서비스로부터 응답을 받는 경우) 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a825-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="4a825-106">요청-회신 서비스 계약을 만들려면 다음 샘플 코드에서처럼 서비스 계약을 정의하고 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 각 작업에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a825-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="4a825-107">기본 동작이므로 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성을 `false`로 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a825-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a825-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a825-108">See also</span></span>

- [<span data-ttu-id="4a825-109">단방향 서비스</span><span class="sxs-lookup"><span data-stu-id="4a825-109">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="4a825-110">이중 서비스</span><span class="sxs-lookup"><span data-stu-id="4a825-110">Duplex Services</span></span>](duplex-services.md)
