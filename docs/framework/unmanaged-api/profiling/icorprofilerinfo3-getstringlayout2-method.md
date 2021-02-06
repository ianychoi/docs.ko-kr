---
description: '자세히 알아보기: ICorProfilerInfo3:: GetStringLayout2 메서드'
title: ICorProfilerInfo3::GetStringLayout2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 398d06dc62245e6a2201feacb62ebbb1e4839ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646675"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="d4d6e-103">ICorProfilerInfo3::GetStringLayout2 메서드</span><span class="sxs-lookup"><span data-stu-id="d4d6e-103">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="d4d6e-104">문자열 개체의 레이아웃 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="d4d6e-105">이 메서드는 [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-105">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d6e-106">구문</span><span class="sxs-lookup"><span data-stu-id="d4d6e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4d6e-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d4d6e-107">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="d4d6e-108">제한이 `ObjectID` 문자열 자체의 길이를 저장 하는 포인터를 기준으로 하는 위치의 오프셋에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="d4d6e-109">길이는로 저장 됩니다 `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="d4d6e-109">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="d4d6e-110">제한이 와이드 문자 문자열을 저장 하는 포인터를 기준으로 하는 버퍼의 오프셋에 대 한 포인터 `ObjectID` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-110">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d6e-111">설명</span><span class="sxs-lookup"><span data-stu-id="d4d6e-111">Remarks</span></span>  

 <span data-ttu-id="d4d6e-112">문자열이 null로 종료 될 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-112">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d6e-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d4d6e-113">Requirements</span></span>  

 <span data-ttu-id="d4d6e-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d6e-115">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4d6e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4d6e-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4d6e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4d6e-117">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d6e-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d6e-118">See also</span></span>

- [<span data-ttu-id="d4d6e-119">ICorProfilerInfo3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d4d6e-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d4d6e-120">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d4d6e-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
