---
description: '자세히 알아보기: ICorProfilerInfo5 인터페이스'
title: ICorProfilerInfo5 인터페이스
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: c89faf3db08adeee3ffcfbb755a5da5ae44b3c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737274"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="045ed-103">ICorProfilerInfo5 인터페이스</span><span class="sxs-lookup"><span data-stu-id="045ed-103">ICorProfilerInfo5 Interface</span></span>

<span data-ttu-id="045ed-104">[.NET Framework 4.5.2 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="045ed-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="045ed-105">코드 프로파일러가 CLR (공용 언어 런타임)과 통신 하 여 이벤트 모니터링을 제어 하는 데 사용할 메서드를 제공 하는 [ICorProfilerInfo4](icorprofilerinfo4-interface.md) 의 서브 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="045ed-105">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="045ed-106">메서드</span><span class="sxs-lookup"><span data-stu-id="045ed-106">Methods</span></span>  
  
|<span data-ttu-id="045ed-107">메서드</span><span class="sxs-lookup"><span data-stu-id="045ed-107">Method</span></span>|<span data-ttu-id="045ed-108">설명</span><span class="sxs-lookup"><span data-stu-id="045ed-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="045ed-109">GetEventMask2 메서드</span><span class="sxs-lookup"><span data-stu-id="045ed-109">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="045ed-110">프로파일러가 CLR에서 알림을 받으려는 현재 이벤트 범주를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="045ed-110">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="045ed-111">SetEventMask2 메서드</span><span class="sxs-lookup"><span data-stu-id="045ed-111">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="045ed-112">프로파일러가 CLR에서 이벤트 알림을 받으려는 이벤트 형식을 지정하는 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="045ed-112">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="045ed-113">설명</span><span class="sxs-lookup"><span data-stu-id="045ed-113">Remarks</span></span>  

 <span data-ttu-id="045ed-114">이 인터페이스에서 사용할 수 있는 메서드는 [ICorProfilerInfo:: geteventmask](icorprofilerinfo-geteventmask-method.md) 및 [ICorProfilerInfo:: seteventmask](icorprofilerinfo-seteventmask-method.md) 메서드를 대체 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="045ed-114">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045ed-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="045ed-115">Requirements</span></span>  

 <span data-ttu-id="045ed-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045ed-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045ed-117">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="045ed-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="045ed-118">**.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045ed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045ed-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="045ed-119">See also</span></span>

- [<span data-ttu-id="045ed-120">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="045ed-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
