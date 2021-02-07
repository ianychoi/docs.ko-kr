---
description: '자세히 알아보기: IGCHost2:: SetGCStartupLimitsEx 메서드'
title: IGCHost2::SetGCStartupLimitsEx 메서드
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 32d3bcbb467a1a418c7123779c881c46e983edef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709310"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="3b772-103">IGCHost2::SetGCStartupLimitsEx 메서드</span><span class="sxs-lookup"><span data-stu-id="3b772-103">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="3b772-104">0 세대의 세그먼트 크기와 최대 크기를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b772-105">구문</span><span class="sxs-lookup"><span data-stu-id="3b772-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b772-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3b772-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="3b772-107">진행 가비지 수집 시스템에서 사용 하는 세그먼트의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="3b772-108">진행 0 세대의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b772-109">설명</span><span class="sxs-lookup"><span data-stu-id="3b772-109">Remarks</span></span>  

 <span data-ttu-id="3b772-110">를 설정 하는 값은 `SetGCStartupLimitsEx` 호스트를 시작 하기 전에만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-110">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="3b772-111">이러한 값은 나중에 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b772-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3b772-112">Requirements</span></span>  

 <span data-ttu-id="3b772-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b772-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b772-114">**헤더:** GCHost, GCHost</span><span class="sxs-lookup"><span data-stu-id="3b772-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3b772-115">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b772-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b772-116">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b772-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b772-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b772-117">See also</span></span>

- [<span data-ttu-id="3b772-118">IGCHost2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3b772-118">IGCHost2 Interface</span></span>](igchost2-interface.md)
