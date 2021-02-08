---
description: '자세한 정보: 엔터프라이즈 서비스 트랜잭션 구성 요소 통합'
title: 엔터프라이즈 서비스 트랜잭션 구성 요소 통합
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 67b3a58900d2842c304d76ff6dd1325e961d8394
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802829"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="2609c-103">엔터프라이즈 서비스 트랜잭션 구성 요소 통합</span><span class="sxs-lookup"><span data-stu-id="2609c-103">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="2609c-104">WCF (Windows Communication Foundation)는 엔터프라이즈 서비스와 통합 하기 위한 자동 메커니즘을 제공 합니다 ( [COM + 응용 프로그램과 통합](integrating-with-com-plus-applications.md)참조).</span><span class="sxs-lookup"><span data-stu-id="2609c-104">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="2609c-105">하지만 엔터프라이즈 서비스에 호스팅된 트랜잭션 구성 요소를 내부적으로 사용하는 서비스를 개발하기 위한 유연성이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-105">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="2609c-106">WCF 트랜잭션 기능은 인프라를 기반으로 하기 때문에, 엔터프라이즈 서비스를 <xref:System.Transactions> WCF와 통합 하는 프로세스는 <xref:System.Transactions> 엔터프라이즈 서비스 [및 com + 트랜잭션과의 상호 운용성](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))에 설명 된 대로 및 엔터프라이즈 서비스 간의 상호 운용성을 지정 하는 프로세스와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-106">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="2609c-107">들어오는 흐름의 트랜잭션과 COM+ 컨텍스트 트랜잭션 간에 필요한 수준의 상호 운용성을 제공하려면 서비스 구현에서 <xref:System.Transactions.TransactionScope> 인스턴스를 만들고 적절한 <xref:System.Transactions.EnterpriseServicesInteropOption> 열거형 값을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-107">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="2609c-108">엔터프라이즈 서비스와 서비스 작업 통합</span><span class="sxs-lookup"><span data-stu-id="2609c-108">Integrating Enterprise Services with a Service Operation</span></span>  

 <span data-ttu-id="2609c-109">다음 코드에서는 <xref:System.Transactions.TransactionScope> 옵션으로 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>을 만드는 트랜잭션 흐름이 Allowed인 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-109">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="2609c-110">이 시나리오에는 다음 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-110">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="2609c-111">클라이언트에서 트랜잭션을 이동하면 엔터프라이즈 서비스 구성 요소 호출을 비롯한 작업이 해당 트랜잭션 범위 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-111">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="2609c-112"><xref:System.Transactions.EnterpriseServicesInteropOption.Full>을 사용하면 트랜잭션이 <xref:System.EnterpriseServices> 컨텍스트와 동기화되어 <xref:System.Transactions>에 대한 앰비언트 트랜잭션과 <xref:System.EnterpriseServices>가 같게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-112">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="2609c-113">클라이언트에서 트랜잭션을 이동하지 않을 때 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>를 `true`로 설정하면 작업에 대한 새 트랜잭션 범위가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-113">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="2609c-114">마찬가지로 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>을 사용하면 작업의 트랜잭션이 <xref:System.EnterpriseServices> 구성 요소의 컨텍스트 내부에 사용되는 트랜잭션과 같게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-114">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="2609c-115">동일한 작업의 트랜잭션 범위 내에서는 추가적인 메서드 호출도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-115">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="2609c-116">작업의 현재 트랜잭션과 트랜잭션 엔터프라이즈 서비스 구성 요소 호출 간에 동기화가 필요하지 않을 때에는 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 인스턴스를 인스턴스화할 때 <xref:System.Transactions.TransactionScope> 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-116">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="2609c-117">엔터프라이즈 서비스와 클라이언트 통합</span><span class="sxs-lookup"><span data-stu-id="2609c-117">Integrating Enterprise Services with a Client</span></span>  

 <span data-ttu-id="2609c-118">다음 코드에서는  설정 상태인 인스턴스를 사용하는 클라이언트 코드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-118">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="2609c-119">이 시나리오에서 트랜잭션 흐름을 지원하는 서비스 작업에 대한 호출은 엔터프라이즈 서비스 구성 요소 호출과 동일한 트랜잭션 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2609c-119">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2609c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2609c-120">See also</span></span>

- [<span data-ttu-id="2609c-121">COM + 응용 프로그램과 통합</span><span class="sxs-lookup"><span data-stu-id="2609c-121">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="2609c-122">COM 애플리케이션과 통합</span><span class="sxs-lookup"><span data-stu-id="2609c-122">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
