---
title: IGCThreadControl::ThreadIsBlockingForSuspension 메서드
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: 39834ba868a21ead3113f2f0d9157cd210d9798c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721649"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="a669d-102">IGCThreadControl::ThreadIsBlockingForSuspension 메서드</span><span class="sxs-lookup"><span data-stu-id="a669d-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="a669d-103">호출을 수행 하는 스레드가 차단 하려고 함을 호스트에 알립니다 (가비지 수집 또는 기타 일시 중단의 경우).</span><span class="sxs-lookup"><span data-stu-id="a669d-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a669d-104">구문</span><span class="sxs-lookup"><span data-stu-id="a669d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a669d-105">설명</span><span class="sxs-lookup"><span data-stu-id="a669d-105">Remarks</span></span>  

 <span data-ttu-id="a669d-106">호스트는 스레드를 다시 `ThreadIsBlockingForSuspension` 예약할 지 여부에 관계 없이 콜백 내에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a669d-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a669d-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a669d-107">Requirements</span></span>  

 <span data-ttu-id="a669d-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a669d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a669d-109">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a669d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a669d-110">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a669d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a669d-111">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a669d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a669d-112">참조</span><span class="sxs-lookup"><span data-stu-id="a669d-112">See also</span></span>

- [<span data-ttu-id="a669d-113">IGCThreadControl 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a669d-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
