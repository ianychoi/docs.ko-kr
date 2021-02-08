---
description: '자세히 알아보기: INotifySink2:: OnSyncCallExit 메서드'
title: INotifySink2::OnSyncCallExit 메서드
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 2de55c3b7956576049e4ad65b2cb6fbc69fa84af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800268"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="13d1f-103">INotifySink2::OnSyncCallExit 메서드</span><span class="sxs-lookup"><span data-stu-id="13d1f-103">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="13d1f-104">호출을 종료할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13d1f-104">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d1f-105">구문</span><span class="sxs-lookup"><span data-stu-id="13d1f-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13d1f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="13d1f-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="13d1f-107">진행 종료 되는 호출의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="13d1f-107">[in] ID of the call being exited.</span></span> <span data-ttu-id="13d1f-108">[CALL_ID 구조체](call-id-structure.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="13d1f-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="13d1f-109">제한이 버퍼를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d1f-109">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="13d1f-110">제한이 호출 버퍼의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="13d1f-110">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13d1f-111">Return Value</span><span class="sxs-lookup"><span data-stu-id="13d1f-111">Return Value</span></span>  

 <span data-ttu-id="13d1f-112">메서드가 성공 하면 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d1f-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d1f-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="13d1f-113">Requirements</span></span>  

 <span data-ttu-id="13d1f-114">**헤더:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="13d1f-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d1f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13d1f-115">See also</span></span>

- [<span data-ttu-id="13d1f-116">INotifySink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="13d1f-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="13d1f-117">INotifySource2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="13d1f-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="13d1f-118">INotifyConnection2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="13d1f-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
