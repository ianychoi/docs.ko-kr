---
description: '자세히 알아보기: ICorProfilerCallback:: ManagedToUnmanagedTransition 메서드'
title: ICorProfilerCallback::ManagedToUnmanagedTransition 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: bf7f45ae576f9812dee24cd3799a3a87678f7c61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705583"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="c4576-103">ICorProfilerCallback::ManagedToUnmanagedTransition 메서드</span><span class="sxs-lookup"><span data-stu-id="c4576-103">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="c4576-104">관리 코드에서 비관리 코드로의 전환이 발생 했음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-104">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4576-105">구문</span><span class="sxs-lookup"><span data-stu-id="c4576-105">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4576-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c4576-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="c4576-107">진행 호출 되는 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="c4576-108">진행 관리 코드에서 비관리 코드를 호출 하거나 관리 되지 않는 함수에서 호출 된 관리 되는 함수의 반환 때문에 전환이 발생 했는지 여부를 나타내는 [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4576-109">설명</span><span class="sxs-lookup"><span data-stu-id="c4576-109">Remarks</span></span>  

 <span data-ttu-id="c4576-110">의 값 `reason` 이 COR_PRF_TRANSITION_CALL 경우 함수 ID는 관리 되지 않는 함수의 함수 ID 이며 just-in-time 컴파일러를 사용 하 여 컴파일되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-110">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="c4576-111">관리 되지 않는 함수에는 이름 및 일부 메타 데이터와 같은 기본 정보가 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-111">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="c4576-112">PInvoke (암시적 플랫폼 호출)를 사용 하 여 관리 되지 않는 함수를 호출한 경우 런타임에서 호출 대상을 확인할 수 없으며의 값 `functionId` 이 null이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4576-112">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="c4576-113">암시적 PInvoke에 대 한 자세한 내용은 [c + + Interop 사용 (암시적 pinvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4576-113">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4576-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c4576-114">Requirements</span></span>  

 <span data-ttu-id="c4576-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4576-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4576-116">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4576-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4576-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4576-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4576-118">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4576-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4576-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4576-119">See also</span></span>

- [<span data-ttu-id="c4576-120">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c4576-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c4576-121">UnmanagedToManagedTransition 메서드</span><span class="sxs-lookup"><span data-stu-id="c4576-121">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="c4576-122">C + +에서 명시적 PInvoke 사용 (DllImport 특성)</span><span class="sxs-lookup"><span data-stu-id="c4576-122">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
