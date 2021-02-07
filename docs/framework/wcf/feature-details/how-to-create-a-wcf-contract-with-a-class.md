---
description: '자세한 정보: 방법: 클래스를 사용 하 여 Windows Communication Foundation 계약 만들기'
title: '방법: 클래스를 사용하여 Windows Communication Foundation 계약 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 63a5cc4e6a7966af69f2d5f3c7db0c7f4e313faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756164"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="71447-103">방법: 클래스를 사용하여 Windows Communication Foundation 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="71447-103">How to: Create a Windows Communication Foundation Contract with a Class</span></span>

<span data-ttu-id="71447-104">WCF (Windows Communication Foundation) 계약을 만드는 기본 방법은 인터페이스를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="71447-104">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="71447-105">자세한 내용은 [방법: 서비스 계약 정의](../how-to-define-a-wcf-service-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71447-105">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="71447-106">또는 다음에 요약한 대로 클래스를 만든 후 <xref:System.ServiceModel.ServiceContractAttribute> 특성을 직접 해당 클래스에 적용하고 <xref:System.ServiceModel.OperationContractAttribute> 특성을 계약의 일부인 클래스의 각 메서드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="71447-106">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="71447-107">`[ServiceContract]` 및 `[ServiceContractAttribute]` 에 대해 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="71447-107">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="71447-108">및의 경우에도 마찬가지 `[OperationContract]` 입니다 `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="71447-108">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="71447-109">각 경우에서 전자는 후자를 위한 축약형입니다.</span><span class="sxs-lookup"><span data-stu-id="71447-109">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="71447-110">서비스 계약에 대 한 자세한 내용은 [서비스 계약 디자인](../designing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71447-110">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="71447-111">클래스를 사용하여 Windows Communication Foundation 계약 만들기</span><span class="sxs-lookup"><span data-stu-id="71447-111">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="71447-112">Visual Basic, c # 또는 기타 공용 언어 런타임 언어를 사용 하 여 새 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71447-112">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="71447-113">이 클래스에 <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="71447-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="71447-114">클래스에 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71447-114">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="71447-115"><xref:System.ServiceModel.OperationContractAttribute>공용 WCF 계약의 일부로 노출 되어야 하는 각 메서드에 클래스를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="71447-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71447-116">예제</span><span class="sxs-lookup"><span data-stu-id="71447-116">Example</span></span>  

 <span data-ttu-id="71447-117">다음 코드 예제에서는 서비스 계약을 정의하는 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="71447-117">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="71447-118"><xref:System.ServiceModel.OperationContractAttribute> 클래스가 적용된 메서드는 기본적으로 요청-회신 메시지 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="71447-118">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="71447-119">이 메시지 패턴에 대 한 자세한 내용은 [방법: Request-Reply 계약 만들기](how-to-create-a-request-reply-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71447-119">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="71447-120">특성의 속성을 설정하여 다른 메시지 패턴을 만들고 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71447-120">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="71447-121">더 많은 예제 [는 방법: One-Way 계약 만들기](how-to-create-a-one-way-contract.md) 및 [방법: 이중 계약 만들기](how-to-create-a-duplex-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71447-121">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71447-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71447-122">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
