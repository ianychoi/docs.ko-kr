---
title: PreBindAssemblyEx 함수
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723963"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="a5c86-102">PreBindAssemblyEx 함수</span><span class="sxs-lookup"><span data-stu-id="a5c86-102">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="a5c86-103">어셈블리의 정책 후 표시 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="a5c86-104">이 함수는 .NET Framework 인프라를 지원 하며 사용자 코드에서 직접 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c86-105">구문</span><span class="sxs-lookup"><span data-stu-id="a5c86-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c86-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a5c86-106">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="a5c86-107">진행 응용 프로그램 컨텍스트를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="a5c86-108">진행 어셈블리 이름을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="a5c86-109">진행 부모 어셈블리를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="a5c86-110">이 매개 변수는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="a5c86-111">진행 런타임 버전을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="a5c86-112">제한이 사후 정책 표시 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a5c86-113">진행 향후 확장성을 위해 예약 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a5c86-114">`pvReserved` 는 null 참조 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c86-115">설명</span><span class="sxs-lookup"><span data-stu-id="a5c86-115">Remarks</span></span>  

 <span data-ttu-id="a5c86-116">`ppNamePostPolicy`출력 매개 변수는 함수가 HRESULT FUSION_E_REF_DEF_MISMATCH을 반환 하는 경우에만 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="a5c86-117">그렇지 않으면 null입니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c86-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a5c86-118">Requirements</span></span>  

 <span data-ttu-id="a5c86-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5c86-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c86-120">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a5c86-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a5c86-121">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5c86-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5c86-122">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c86-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c86-123">참조</span><span class="sxs-lookup"><span data-stu-id="a5c86-123">See also</span></span>

- [<span data-ttu-id="a5c86-124">Fusion 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="a5c86-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
