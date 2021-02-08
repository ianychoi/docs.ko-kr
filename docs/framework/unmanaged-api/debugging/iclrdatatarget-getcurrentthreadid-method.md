---
description: '자세히 알아보기: ICLRDataTarget:: GetCurrentThreadID 메서드'
title: ICLRDataTarget::GetCurrentThreadID 메서드
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: ae1ef00fd6afbecf741d1e4ed215c816dcf6af8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801360"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="03ab1-103">ICLRDataTarget::GetCurrentThreadID 메서드</span><span class="sxs-lookup"><span data-stu-id="03ab1-103">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="03ab1-104">현재 스레드에 대 한 운영 체제 식별자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="03ab1-104">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ab1-105">구문</span><span class="sxs-lookup"><span data-stu-id="03ab1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03ab1-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="03ab1-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="03ab1-107">제한이 대상 프로세스에 대 한 현재 스레드의 운영 체제 식별자에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="03ab1-107">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ab1-108">설명</span><span class="sxs-lookup"><span data-stu-id="03ab1-108">Remarks</span></span>  

 <span data-ttu-id="03ab1-109">대상 프로세스에 대 한 현재 스레드가 없으면 `GetCurrentThreadID` 메서드가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03ab1-109">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ab1-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="03ab1-110">Requirements</span></span>  

 <span data-ttu-id="03ab1-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03ab1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ab1-112">**헤더:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="03ab1-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="03ab1-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03ab1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03ab1-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ab1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ab1-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03ab1-115">See also</span></span>

- [<span data-ttu-id="03ab1-116">ICLRDataTarget 인터페이스</span><span class="sxs-lookup"><span data-stu-id="03ab1-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
