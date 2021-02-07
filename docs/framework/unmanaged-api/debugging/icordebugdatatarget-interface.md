---
description: '자세히 알아보기: ICorDebugDataTarget 인터페이스'
title: ICorDebugDataTarget 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 34121b56080a8adc17543ce5716962c17c1a156d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764426"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="aa78c-103">ICorDebugDataTarget 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa78c-103">ICorDebugDataTarget Interface</span></span>

<span data-ttu-id="aa78c-104">특정 대상 프로세스에 대한 액세스를 제공하는 콜백 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-104">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa78c-105">메서드</span><span class="sxs-lookup"><span data-stu-id="aa78c-105">Methods</span></span>  
  
|<span data-ttu-id="aa78c-106">메서드</span><span class="sxs-lookup"><span data-stu-id="aa78c-106">Method</span></span>|<span data-ttu-id="aa78c-107">설명</span><span class="sxs-lookup"><span data-stu-id="aa78c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa78c-108">GetPlatform 메서드</span><span class="sxs-lookup"><span data-stu-id="aa78c-108">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="aa78c-109">대상 프로세스가 실행 되는 프로세서 아키텍처 및 운영 체제를 포함 하 여 플랫폼에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-109">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="aa78c-110">ReadVirtual 메서드</span><span class="sxs-lookup"><span data-stu-id="aa78c-110">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="aa78c-111">지정 된 주소에서 시작 하는 연속 메모리 블록을 가져와 제공 된 버퍼에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-111">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="aa78c-112">GetThreadContext 메서드</span><span class="sxs-lookup"><span data-stu-id="aa78c-112">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="aa78c-113">지정 된 스레드에 대 한 현재 스레드 컨텍스트를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-113">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa78c-114">설명</span><span class="sxs-lookup"><span data-stu-id="aa78c-114">Remarks</span></span>  

 <span data-ttu-id="aa78c-115">`ICorDebugDataTarget` 및 해당 메서드의 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-115">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="aa78c-116">디버깅 서비스는이 인터페이스의 메서드를 호출 하 여 대상 프로세스의 메모리 및 기타 데이터에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-116">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="aa78c-117">디버거 클라이언트는 특정 대상에 적합 하 게이 인터페이스를 구현 해야 합니다 (예: 라이브 프로세스 또는 메모리 덤프).</span><span class="sxs-lookup"><span data-stu-id="aa78c-117">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="aa78c-118">`ICorDebugDataTarget`메서드는 다른 인터페이스에 구현 된 메서드 내 에서만 호출할 수 있습니다 `ICorDebug*` .</span><span class="sxs-lookup"><span data-stu-id="aa78c-118">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="aa78c-119">이렇게 하면 디버거 클라이언트에서 호출 되는 스레드 및 시기를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-119">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="aa78c-120">`ICorDebugDataTarget`구현은 항상 대상에 대 한 최신 정보를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-120">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="aa78c-121">`ICorDebug*`인터페이스 (및 `ICorDebugDataTarget` 메서드)를 호출 하는 동안에는 대상 프로세스를 중지 하 고 변경 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-121">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="aa78c-122">대상이 라이브 프로세스이 고 상태가 변경 되 면 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) 메서드를 다시 호출 하 여 대체 ICorDebugProcess 인스턴스를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-122">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa78c-123">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa78c-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa78c-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="aa78c-124">Requirements</span></span>  

 <span data-ttu-id="aa78c-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa78c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa78c-126">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa78c-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa78c-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa78c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa78c-128">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa78c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa78c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa78c-129">See also</span></span>

- [<span data-ttu-id="aa78c-130">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa78c-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="aa78c-131">디버깅</span><span class="sxs-lookup"><span data-stu-id="aa78c-131">Debugging</span></span>](index.md)
