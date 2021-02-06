---
description: '자세히 알아보기: ICLRValidator:: FormatEventInfo 메서드'
title: ICLRValidator::FormatEventInfo 메서드
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 3d8d1eff8c638517e201905d0313ee824490acf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636795"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="f2e2c-103">ICLRValidator::FormatEventInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="f2e2c-103">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="f2e2c-104">지정 된 유효성 검사 오류에 대 한 자세한 메시지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-104">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e2c-105">구문</span><span class="sxs-lookup"><span data-stu-id="f2e2c-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2e2c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f2e2c-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="f2e2c-107">진행 유효성 검사 오류 처리기에 전달 된 HRESULT 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="f2e2c-108">진행 `VEContext` 유효성 검사 오류에 대 한 컨텍스트 정보를 포함 하는 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-108">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="f2e2c-109">[in, out] 친숙 한 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-109">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="f2e2c-110">진행 오류 메시지의 최대 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="f2e2c-111">진행 메시지에 사용할 안전한 추가 매개 변수 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-111">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2e2c-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="f2e2c-112">Return Value</span></span>  
  
|<span data-ttu-id="f2e2c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2e2c-113">HRESULT</span></span>|<span data-ttu-id="f2e2c-114">설명</span><span class="sxs-lookup"><span data-stu-id="f2e2c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2e2c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2e2c-115">S_OK</span></span>|<span data-ttu-id="f2e2c-116">`FormatEventInfo` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-116">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="f2e2c-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2e2c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2e2c-118">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2e2c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2e2c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2e2c-120">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-120">The call timed out.</span></span>|  
|<span data-ttu-id="f2e2c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2e2c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2e2c-122">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2e2c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2e2c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2e2c-124">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2e2c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2e2c-125">E_FAIL</span></span>|<span data-ttu-id="f2e2c-126">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2e2c-127">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2e2c-128">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2e2c-129">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f2e2c-129">Requirements</span></span>  

 <span data-ttu-id="f2e2c-130">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e2c-131">**헤더:** IValidator, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="f2e2c-131">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="f2e2c-132">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e2c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2e2c-133">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e2c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e2c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2e2c-134">See also</span></span>

- [<span data-ttu-id="f2e2c-135">ICLRErrorReportingManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f2e2c-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="f2e2c-136">ICLRValidator 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f2e2c-136">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
