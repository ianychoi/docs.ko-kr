---
title: IMetaDataDispenserEx::FindAssemblyModule 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: 5bc622c013e62fa9c03476cc5927133682020426
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700615"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="03d65-102">IMetaDataDispenserEx::FindAssemblyModule 메서드</span><span class="sxs-lookup"><span data-stu-id="03d65-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>

<span data-ttu-id="03d65-103">이 메서드가 구현되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="03d65-103">This method is not implemented.</span></span> <span data-ttu-id="03d65-104">이 메서드를 호출 하면 E_NOTIMPL 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d65-105">구문</span><span class="sxs-lookup"><span data-stu-id="03d65-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03d65-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="03d65-106">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="03d65-107">진행 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="03d65-108">진행 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="03d65-109">진행 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="03d65-110">진행 모듈의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="03d65-111">진행 찾을 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="03d65-112">제한이 어셈블리의 단순한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="03d65-113">진행 의 크기 (바이트)입니다 `szName` .</span><span class="sxs-lookup"><span data-stu-id="03d65-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="03d65-114">제한이 에서 실제로 반환 되는 문자 수입니다 `szName` .</span><span class="sxs-lookup"><span data-stu-id="03d65-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d65-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="03d65-115">Requirements</span></span>  

 <span data-ttu-id="03d65-116">**플랫폼:** [시스템 요구 사항](../../get-started/system-requirements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="03d65-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03d65-117">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="03d65-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03d65-118">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03d65-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03d65-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03d65-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d65-120">참조</span><span class="sxs-lookup"><span data-stu-id="03d65-120">See also</span></span>

- [<span data-ttu-id="03d65-121">IMetaDataDispenserEx 인터페이스</span><span class="sxs-lookup"><span data-stu-id="03d65-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="03d65-122">IMetaDataDispenser 인터페이스</span><span class="sxs-lookup"><span data-stu-id="03d65-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
