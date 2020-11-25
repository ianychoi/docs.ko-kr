---
title: INotifySink2::OnSyncCallOut 메서드
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: 00f6032f41caf54d7366de30a449f1ae76e8bbd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719985"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="d55e3-102">INotifySink2::OnSyncCallOut 메서드</span><span class="sxs-lookup"><span data-stu-id="d55e3-102">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="d55e3-103">호출이 호출 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d55e3-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d55e3-104">구문</span><span class="sxs-lookup"><span data-stu-id="d55e3-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d55e3-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d55e3-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="d55e3-106">진행 Out 호출의 ID입니다. [CALL_ID 구조체](call-id-structure.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d55e3-106">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="d55e3-107">제한이 버퍼를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55e3-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="d55e3-108">제한이 호출 버퍼의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="d55e3-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d55e3-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="d55e3-109">Return Value</span></span>  

 <span data-ttu-id="d55e3-110">메서드가 성공 하면 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="d55e3-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d55e3-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d55e3-111">Requirements</span></span>  

 <span data-ttu-id="d55e3-112">**헤더:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="d55e3-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55e3-113">참조</span><span class="sxs-lookup"><span data-stu-id="d55e3-113">See also</span></span>

- [<span data-ttu-id="d55e3-114">INotifySink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d55e3-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="d55e3-115">INotifySource2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d55e3-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="d55e3-116">INotifyConnection2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d55e3-116">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
