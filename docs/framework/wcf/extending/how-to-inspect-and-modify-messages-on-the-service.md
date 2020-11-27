---
title: '방법: 서비스에서 메시지 검사 및 수정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 8d1ce6ef00462adb38e3d59c3d9bd35694c4dbe9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249061"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="4c904-102">방법: 서비스에서 메시지 검사 및 수정</span><span class="sxs-lookup"><span data-stu-id="4c904-102">How to: Inspect and Modify Messages on the Service</span></span>

<span data-ttu-id="4c904-103">을 구현 하 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> 고 서비스 런타임에 삽입 하 여 WCF (Windows Communication Foundation) 클라이언트에서 들어오거나 나가는 메시지를 검사 하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="4c904-104">자세한 내용은 [디스패처 확장](extending-dispatchers.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c904-104">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="4c904-105">서비스의 해당 기능은 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>입니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="4c904-106">메시지를 검사하거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4c904-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="4c904-107"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="4c904-108">서비스 메시지 검사자를 쉽게 삽입하려는 범위에 따라 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="4c904-109"><xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>에서 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 메서드를 호출하기 전에 동작을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c904-110">자세한 내용은 [동작을 사용 하 여 런타임 구성 및 확장](configuring-and-extending-the-runtime-with-behaviors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c904-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c904-111">예제</span><span class="sxs-lookup"><span data-stu-id="4c904-111">Example</span></span>  

 <span data-ttu-id="4c904-112">다음 코드 예제는 아래 순서대로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c904-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="4c904-113">서비스 검사자 구현</span><span class="sxs-lookup"><span data-stu-id="4c904-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="4c904-114">검사자를 삽입하는 서비스 동작</span><span class="sxs-lookup"><span data-stu-id="4c904-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="4c904-115">서비스 애플리케이션에서 동작을 로드 및 실행하는 구성 파일</span><span class="sxs-lookup"><span data-stu-id="4c904-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4c904-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c904-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="4c904-117">동작을 사용하여 런타임 구성 및 확장</span><span class="sxs-lookup"><span data-stu-id="4c904-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
