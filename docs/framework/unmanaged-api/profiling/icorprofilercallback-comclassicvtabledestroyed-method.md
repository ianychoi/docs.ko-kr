---
title: ICorProfilerCallback::COMClassicVTableDestroyed 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: aa02b4def015d5badfd0003e08bea5289fe58e17
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700186"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="1e3b6-102">ICorProfilerCallback::COMClassicVTableDestroyed 메서드</span><span class="sxs-lookup"><span data-stu-id="1e3b6-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="1e3b6-103">COM interop vtable이 제거 중임을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e3b6-104">Vtables의 소멸이 종료와 매우 근접 하 게 발생 하기 때문에이 콜백은 발생 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3b6-105">구문</span><span class="sxs-lookup"><span data-stu-id="1e3b6-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e3b6-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e3b6-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="1e3b6-107">\[in]이 vtable이 생성 된 클래스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="1e3b6-108">\[in] 클래스에서 구현 하는 인터페이스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1e3b6-109">인터페이스가 내부 전용 이면이 값은 NULL 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="1e3b6-110">\[in] vtable의 시작에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e3b6-111">설명</span><span class="sxs-lookup"><span data-stu-id="1e3b6-111">Remarks</span></span>  

 <span data-ttu-id="1e3b6-112">스택은 가비지 수집을 허용 하는 상태가 아닐 수 있으므로 선점형 가비지 수집을 사용 하도록 설정할 수 없기 때문에 프로파일러는이 메서드의 구현에서 차단 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1e3b6-113">프로파일러가 여기에서 차단 되 고 가비지 수집이 시도 되는 경우이 콜백이 반환 될 때까지 런타임이 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1e3b6-114">이 메서드의 프로파일러 구현은 관리 코드를 호출 하거나 관리 되는 메모리 할당을 발생 시 키 지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e3b6-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1e3b6-115">Requirements</span></span>  

 <span data-ttu-id="1e3b6-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e3b6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e3b6-117">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e3b6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e3b6-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e3b6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e3b6-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e3b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3b6-120">참조</span><span class="sxs-lookup"><span data-stu-id="1e3b6-120">See also</span></span>

- [<span data-ttu-id="1e3b6-121">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1e3b6-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1e3b6-122">COMClassicVTableCreated 메서드</span><span class="sxs-lookup"><span data-stu-id="1e3b6-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
