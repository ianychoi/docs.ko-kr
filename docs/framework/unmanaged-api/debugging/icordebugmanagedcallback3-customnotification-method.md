---
description: '자세히 알아보기: ICorDebugManagedCallback3:: CustomNotification 메서드'
title: ICorDebugManagedCallback3::CustomNotification 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 18210e9c65afa0655374fb038d30516cfed02052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691720"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="89048-103">ICorDebugManagedCallback3::CustomNotification 메서드</span><span class="sxs-lookup"><span data-stu-id="89048-103">ICorDebugManagedCallback3::CustomNotification Method</span></span>

<span data-ttu-id="89048-104">사용자 지정 디버거 알림이 발생 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="89048-104">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89048-105">구문</span><span class="sxs-lookup"><span data-stu-id="89048-105">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89048-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="89048-106">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="89048-107">진행 알림을 발생 시킨 스레드에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="89048-107">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="89048-108">진행 알림을 발생 시킨 스레드를 포함 하는 응용 프로그램 도메인에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="89048-108">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89048-109">Return Value</span><span class="sxs-lookup"><span data-stu-id="89048-109">Return Value</span></span>  

 <span data-ttu-id="89048-110">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="89048-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89048-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89048-111">HRESULT</span></span>|<span data-ttu-id="89048-112">설명</span><span class="sxs-lookup"><span data-stu-id="89048-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89048-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="89048-113">S_OK</span></span>|<span data-ttu-id="89048-114">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="89048-114">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="89048-115">예외</span><span class="sxs-lookup"><span data-stu-id="89048-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89048-116">설명</span><span class="sxs-lookup"><span data-stu-id="89048-116">Remarks</span></span>  

 <span data-ttu-id="89048-117">[ICorDebugThread4:: GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) 메서드에 대 한 후속 호출에서는 메서드에 전달 된 스레드 개체를 검색 합니다 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="89048-117">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="89048-118">[ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) 메서드를 호출 하 여 스레드 개체의 형식을 이전에 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89048-118">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="89048-119">디버거는 스레드 개체의 필드에서 유형별 매개 변수를 읽을 수 있으며 응답을 필드에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89048-119">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="89048-120">[ICorDebug](icordebug-interface.md) 인터페이스는 알림 또는 해당 콘텐츠 형식에 대 한 정책을 적용 하지 않으며, 알림의 의미 체계는 디버거, 응용 프로그램 및 .NET Framework 간의 계약을 엄격히 부과 합니다.</span><span class="sxs-lookup"><span data-stu-id="89048-120">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89048-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="89048-121">Requirements</span></span>  

 <span data-ttu-id="89048-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89048-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89048-123">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89048-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89048-124">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89048-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89048-125">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89048-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89048-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89048-126">See also</span></span>

- [<span data-ttu-id="89048-127">ICorDebugManagedCallback3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="89048-127">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="89048-128">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="89048-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="89048-129">디버깅</span><span class="sxs-lookup"><span data-stu-id="89048-129">Debugging</span></span>](index.md)
