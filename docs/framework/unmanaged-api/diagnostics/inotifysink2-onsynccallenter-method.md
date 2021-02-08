---
description: '자세히 알아보기: INotifySink2:: OnSyncCallEnter 메서드'
title: INotifySink2::OnSyncCallEnter 메서드
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: e7537b16ec8ea8d92ad92498c1bfdac5a9de6475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800281"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="85a55-103">INotifySink2::OnSyncCallEnter 메서드</span><span class="sxs-lookup"><span data-stu-id="85a55-103">INotifySink2::OnSyncCallEnter Method</span></span>

<span data-ttu-id="85a55-104">호출을 입력할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a55-104">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a55-105">구문</span><span class="sxs-lookup"><span data-stu-id="85a55-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85a55-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="85a55-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="85a55-107">진행 입력 하는 호출의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="85a55-107">[in] ID of the call being entered.</span></span> <span data-ttu-id="85a55-108">[CALL_ID 구조체](call-id-structure.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85a55-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="85a55-109">진행 버퍼를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a55-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="85a55-110">진행 호출 버퍼의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="85a55-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85a55-111">Return Value</span><span class="sxs-lookup"><span data-stu-id="85a55-111">Return Value</span></span>  

 <span data-ttu-id="85a55-112">메서드가 성공 하면 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a55-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85a55-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="85a55-113">Requirements</span></span>  

 <span data-ttu-id="85a55-114">**헤더:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="85a55-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a55-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85a55-115">See also</span></span>

- [<span data-ttu-id="85a55-116">INotifySink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="85a55-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="85a55-117">INotifySource2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="85a55-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="85a55-118">INotifyConnection2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="85a55-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
