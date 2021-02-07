---
description: '자세히 알아보기: ICorDebug:: CanLaunchOrAttach 메서드'
title: ICorDebug::CanLaunchOrAttach 메서드
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: cb813c4bae968941de731d9d5b74d8f804b3c8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723246"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="fe87a-103">ICorDebug::CanLaunchOrAttach 메서드</span><span class="sxs-lookup"><span data-stu-id="fe87a-103">ICorDebug::CanLaunchOrAttach Method</span></span>

<span data-ttu-id="fe87a-104">현재 컴퓨터 및 런타임 구성의 컨텍스트 내에서 새 프로세스를 시작 하거나 지정 된 기존 프로세스에 연결할 수 있는지 여부를 나타내는 HRESULT를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-104">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe87a-105">구문</span><span class="sxs-lookup"><span data-stu-id="fe87a-105">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe87a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe87a-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="fe87a-107">진행 기존 프로세스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-107">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="fe87a-108">진행 `true` Win32 디버깅을 사용 하도록 설정 하 여를 시작 하거나 win32 디버깅을 사용 하도록 설정 하 여 연결 하려면를 전달 하 고, 그렇지 않으면를 전달 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-108">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe87a-109">Return Value</span><span class="sxs-lookup"><span data-stu-id="fe87a-109">Return Value</span></span>  

 <span data-ttu-id="fe87a-110">현재 컴퓨터와 런타임 구성에 대 한 정보를 고려 하 여 디버깅 서비스에서 새 프로세스를 시작 하거나 지정 된 프로세스에 연결 하는 것이 가능한 지 확인 하는 경우에 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-110">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="fe87a-111">가능한 HRESULT 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-111">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="fe87a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe87a-112">S_OK</span></span>  
  
- <span data-ttu-id="fe87a-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="fe87a-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="fe87a-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="fe87a-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="fe87a-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="fe87a-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe87a-116">설명</span><span class="sxs-lookup"><span data-stu-id="fe87a-116">Remarks</span></span>  

 <span data-ttu-id="fe87a-117">이 메서드는 전적으로 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-117">This method is purely informational.</span></span> <span data-ttu-id="fe87a-118">인터페이스는에서 반환 된 값에 관계 없이 프로세스를 시작 하거나 프로세스에 연결 하는 것을 중지 하지 않습니다 `CanLaunchOrAttach` .</span><span class="sxs-lookup"><span data-stu-id="fe87a-118">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="fe87a-119">Win32 디버깅을 사용 하도록 설정 하거나 Win32 디버깅을 사용 하도록 설정한 상태에서를 시작 하려는 경우 `true` 에는를 전달 `win32DebuggingEnabled` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-119">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="fe87a-120">이 옵션을 사용 하는 경우에 의해 반환 되는 HRESULT는 `CanLaunchOrAttach` 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe87a-120">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe87a-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="fe87a-121">Requirements</span></span>  

 <span data-ttu-id="fe87a-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe87a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe87a-123">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe87a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe87a-124">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe87a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe87a-125">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe87a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe87a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe87a-126">See also</span></span>

- [<span data-ttu-id="fe87a-127">ICorDebug 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe87a-127">ICorDebug Interface</span></span>](icordebug-interface.md)
