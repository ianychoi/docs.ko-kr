---
description: '자세한 정보: 쿼리에 주석 사용'
title: 쿼리에 주석 사용
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 97423fe8ea7d90522a5f469adda5f645aa7e4485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698026"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="e7bf7-103">쿼리에 주석 사용</span><span class="sxs-lookup"><span data-stu-id="e7bf7-103">Using Annotation in Queries</span></span>

<span data-ttu-id="e7bf7-104">주석을 사용하여 빌드 시간 후에 구성될 수 있는 값으로 추적 레코드에 임의 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-104">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="e7bf7-105">예를 들어 여러 워크플로 간에 여러 추적 레코드를 "Mail Server" = = "Mail Server1"로 태그를 지정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-105">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="e7bf7-106">이렇게 하면 나중에 추적 레코드를 쿼리할 때 이 태그를 사용하여 모든 레코드를 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-106">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="e7bf7-107">주석 추가</span><span class="sxs-lookup"><span data-stu-id="e7bf7-107">Adding Annotations</span></span>  

 <span data-ttu-id="e7bf7-108">다음 예제와 같이 추적 쿼리에 주석을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-108">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> <span data-ttu-id="e7bf7-109">이러한 추적 쿼리 요소를 사용하여 추적 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-109">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="e7bf7-110">추적 프로필은 구성이나 코드를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf7-110">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bf7-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7bf7-111">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="e7bf7-112">워크플로 추적</span><span class="sxs-lookup"><span data-stu-id="e7bf7-112">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7bf7-113">추적 프로필</span><span class="sxs-lookup"><span data-stu-id="e7bf7-113">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
