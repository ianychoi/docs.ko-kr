---
description: '자세한 정보: 사용자 지정 추적 레코드'
title: 사용자 지정 추적 레코드
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 9d6988465fa3afca4302c86e0c2cad2778f2beae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742695"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="0ebd4-103">사용자 지정 추적 레코드</span><span class="sxs-lookup"><span data-stu-id="0ebd4-103">Custom Tracking Records</span></span>

<span data-ttu-id="0ebd4-104">이 항목에서는 사용자 지정 추적 레코드를 만들고 이 레코드와 함께 내보내질 데이터로 이 레코드를 채우는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ebd4-104">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="0ebd4-105">사용자 지정 추적 레코드 내보내기</span><span class="sxs-lookup"><span data-stu-id="0ebd4-105">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="0ebd4-106">다음 예제에 표시된 것처럼 코드 활동에서 사용자 지정 추적 레코드를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ebd4-106">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="0ebd4-107"><xref:System.Activities.Tracking.CustomTrackingRecord>에서 <xref:System.Activities.NativeActivityContext.Track%2A> 메서드를 호출하여 코드 활동에서 `ActivityContext`를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0ebd4-107">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ebd4-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ebd4-108">See also</span></span>

- <span data-ttu-id="0ebd4-109">[Windows Server App Fabric 모니터링](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0ebd4-109">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="0ebd4-110">[App Fabric을 사용 하 여 응용 프로그램 모니터링](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0ebd4-110">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
