---
title: '방법: 매개 변수 검사 또는 수정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: e8b2674d8efc0ef3ac2f1dd6ab0df559195c274c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249035"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="d5b0e-102">방법: 매개 변수 검사 또는 수정</span><span class="sxs-lookup"><span data-stu-id="d5b0e-102">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="d5b0e-103">인터페이스를 구현 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 하 여 클라이언트 또는 서비스 런타임에 삽입 하 여 wcf (Windows Communication Foundation) 클라이언트 개체 또는 wcf 서비스에서 단일 작업에 대해 들어오거나 나가는 메시지를 검사 하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="d5b0e-104">일반적으로 작업 동작을 사용하여 단일 작업에 매개 변수 검사자를 추가하지만, 다른 동작을 사용하여 더 넓은 범위의 런타임에 쉬운 액세스를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="d5b0e-105">자세한 내용은 [클라이언트 확장](extending-clients.md) 및 [디스패처 확장](extending-dispatchers.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-105">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="d5b0e-106">매개 변수 검사 또는 수정</span><span class="sxs-lookup"><span data-stu-id="d5b0e-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="d5b0e-107"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="d5b0e-108">필요한 범위에 따라 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>를 구현하여 매개 변수 검사자를 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> 속성에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="d5b0e-109"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>에서 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 메서드를 호출하기 전에 동작을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d5b0e-110">자세한 내용은 [동작을 사용 하 여 런타임 구성 및 확장](configuring-and-extending-the-runtime-with-behaviors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b0e-111">예제</span><span class="sxs-lookup"><span data-stu-id="d5b0e-111">Example</span></span>  

 <span data-ttu-id="d5b0e-112">다음 코드 예제는 아래 순서대로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="d5b0e-113">매개 변수 검사자 구현.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="d5b0e-114"><xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 및 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>를 사용하여 매개 변수 검사자를 삽입하는 동작 구현.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="d5b0e-115">클라이언트 애플리케이션에서 엔드포인트 동작을 로드하고 실행하여 클라이언트에 매개 변수 검사자를 삽입하는 구성 파일.</span><span class="sxs-lookup"><span data-stu-id="d5b0e-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d5b0e-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5b0e-116">See also</span></span>

- [<span data-ttu-id="d5b0e-117">동작을 사용하여 런타임 구성 및 확장</span><span class="sxs-lookup"><span data-stu-id="d5b0e-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
