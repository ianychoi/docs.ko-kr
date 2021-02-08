---
description: '자세한 정보: 방법: 서비스 인스턴스 제어'
title: '방법: 서비스 인스턴스 만들기 제어'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 014d7fb4b054a1b52c1fea671cd099267fba468c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779922"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="a2c40-103">방법: 서비스 인스턴스 만들기 제어</span><span class="sxs-lookup"><span data-stu-id="a2c40-103">How to: Control Service Instancing</span></span>

<span data-ttu-id="a2c40-104">서비스의 인스턴스 모드를 설정하면 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>(및 연결된 사용자 정의 서비스 개체)가 만들어지는 시기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2c40-104">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="a2c40-105">가능한 모드에 대해서는 <xref:System.ServiceModel.InstanceContextMode> 열거형을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2c40-105">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="a2c40-106">동작에 대 한 자세한 내용은 [동작을 사용 하 여 런타임 구성 및 확장](../extending/configuring-and-extending-the-runtime-with-behaviors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2c40-106">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="a2c40-107">작업 예제를 보려면 [동작](../samples/behaviors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2c40-107">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="a2c40-108">코드를 사용하여 서비스 인스턴스 수명을 제어하려면</span><span class="sxs-lookup"><span data-stu-id="a2c40-108">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="a2c40-109">서비스 클래스에 <xref:System.ServiceModel.ServiceBehaviorAttribute>를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2c40-109">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="a2c40-110"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 속성을 <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession> 또는 <xref:System.ServiceModel.InstanceContextMode.Single> 값 중 하나로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2c40-110">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a2c40-111">예제</span><span class="sxs-lookup"><span data-stu-id="a2c40-111">Example</span></span>  

 <span data-ttu-id="a2c40-112">다음 코드 예제에서는 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 특성의 <xref:System.ServiceModel.ServiceBehaviorAttribute> 속성을 <xref:System.ServiceModel.InstanceContextMode.PerCall>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2c40-112">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a2c40-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2c40-113">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="a2c40-114">서비스: 동작 샘플</span><span class="sxs-lookup"><span data-stu-id="a2c40-114">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
