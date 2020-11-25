---
title: ICLRRuntimeInfo::GetProcAddress 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 028cfd51a713d8598598566a5b1edcf3fc70ecfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732062"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="75e91-102">ICLRRuntimeInfo::GetProcAddress 메서드</span><span class="sxs-lookup"><span data-stu-id="75e91-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="75e91-103">이 인터페이스와 연결 된 CLR (공용 언어 런타임)에서 내보낸 지정 된 함수의 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="75e91-104">이 메서드는 [GetRealProcAddress](getrealprocaddress-function.md) 함수를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e91-105">구문</span><span class="sxs-lookup"><span data-stu-id="75e91-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e91-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="75e91-106">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="75e91-107">진행 내보낸 함수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="75e91-108">제한이 내보낸 함수의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75e91-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="75e91-109">Return Value</span></span>  

 <span data-ttu-id="75e91-110">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75e91-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75e91-111">HRESULT</span></span>|<span data-ttu-id="75e91-112">설명</span><span class="sxs-lookup"><span data-stu-id="75e91-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75e91-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="75e91-113">S_OK</span></span>|<span data-ttu-id="75e91-114">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="75e91-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="75e91-115">E_POINTER</span></span>|<span data-ttu-id="75e91-116">`pszProcName` 또는 `ppProc`가 null입니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="75e91-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="75e91-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="75e91-118">지정한 함수는 내보낸 함수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75e91-119">설명</span><span class="sxs-lookup"><span data-stu-id="75e91-119">Remarks</span></span>  

 <span data-ttu-id="75e91-120">이 메서드로 인해 CLR이 로드 되지만 초기화 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e91-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="75e91-121">Requirements</span></span>  

 <span data-ttu-id="75e91-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75e91-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e91-123">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="75e91-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="75e91-124">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75e91-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75e91-125">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e91-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e91-126">참조</span><span class="sxs-lookup"><span data-stu-id="75e91-126">See also</span></span>

- [<span data-ttu-id="75e91-127">ICLRRuntimeInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="75e91-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="75e91-128">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="75e91-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="75e91-129">호스팅</span><span class="sxs-lookup"><span data-stu-id="75e91-129">Hosting</span></span>](index.md)
