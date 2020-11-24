---
title: ICorDebugThread4::HadUnhandledException 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: 4e368b2c63e8e43b5c392bec4b79daac8bae249d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678540"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="71884-102">ICorDebugThread4::HadUnhandledException 메서드</span><span class="sxs-lookup"><span data-stu-id="71884-102">ICorDebugThread4::HadUnhandledException Method</span></span>

<span data-ttu-id="71884-103">스레드에 처리 되지 않은 예외가 발생 했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="71884-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71884-104">구문</span><span class="sxs-lookup"><span data-stu-id="71884-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="71884-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="71884-105">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="71884-106">제한이 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 구조체의 정렬 된 열거 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="71884-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71884-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="71884-107">Return Value</span></span>  

 <span data-ttu-id="71884-108">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="71884-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="71884-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71884-109">HRESULT</span></span>|<span data-ttu-id="71884-110">설명</span><span class="sxs-lookup"><span data-stu-id="71884-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71884-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="71884-111">S_OK</span></span>|<span data-ttu-id="71884-112">스레드의 생성 후에 처리 되지 않은 예외가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="71884-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="71884-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="71884-113">S_FALSE</span></span>|<span data-ttu-id="71884-114">스레드에 처리 되지 않은 예외가 발생 한 적이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71884-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71884-115">설명</span><span class="sxs-lookup"><span data-stu-id="71884-115">Remarks</span></span>  

 <span data-ttu-id="71884-116">이 메서드는 스레드에 처리 되지 않은 예외가 발생 했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="71884-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="71884-117">처리 되지 않은 예외 콜백이 트리거하거나 네이티브 JIT 연결이 시작 될 때이 메서드는 S_OK 반환 하도록 보장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71884-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="71884-118">[ICorDebugThread 예외](icordebugthread-getcurrentexception-method.md) 메서드에서 처리 되지 않은 예외를 반환 한다는 보장이 없습니다. 그러나 처리 되지 않은 예외 콜백을 가져온 후 또는 네이티브 JIT 연결에 프로세스를 아직 계속 하지 않은 경우에는이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71884-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="71884-119">또한 네이티브 JIT 연결이 트리거되는 동안 처리 되지 않은 예외가 있는 스레드가 둘 이상 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71884-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="71884-120">이러한 경우 JIT 연결을 트리거한 예외를 확인할 수 있는 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71884-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71884-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="71884-121">Requirements</span></span>  

 <span data-ttu-id="71884-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71884-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71884-123">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71884-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71884-124">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71884-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71884-125">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71884-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71884-126">참조</span><span class="sxs-lookup"><span data-stu-id="71884-126">See also</span></span>

- [<span data-ttu-id="71884-127">ICorDebugThread4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="71884-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="71884-128">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="71884-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="71884-129">디버깅</span><span class="sxs-lookup"><span data-stu-id="71884-129">Debugging</span></span>](index.md)
