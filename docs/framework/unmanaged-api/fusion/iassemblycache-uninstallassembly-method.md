---
title: IAssemblyCache::UninstallAssembly 메서드
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 36a2a609e95740ffc45722635a7e1f09e0ed5601
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670786"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="0164f-102">IAssemblyCache::UninstallAssembly 메서드</span><span class="sxs-lookup"><span data-stu-id="0164f-102">IAssemblyCache::UninstallAssembly Method</span></span>

<span data-ttu-id="0164f-103">전역 어셈블리 캐시에서 지정 된 어셈블리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0164f-104">구문</span><span class="sxs-lookup"><span data-stu-id="0164f-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0164f-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0164f-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="0164f-106">진행 Fusion에 정의 된 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="0164f-107">진행 제거할 어셈블리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="0164f-108">진행 어셈블리의 설치 데이터를 포함 하는 [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="0164f-109">[out, 선택 사항] Fusion에 정의 된 처리 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="0164f-110">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0164f-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="0164f-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="0164f-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="0164f-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="0164f-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="0164f-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="0164f-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="0164f-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="0164f-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="0164f-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="0164f-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="0164f-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="0164f-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0164f-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0164f-117">Requirements</span></span>  

 <span data-ttu-id="0164f-118">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0164f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0164f-119">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0164f-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0164f-120">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0164f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0164f-121">참조</span><span class="sxs-lookup"><span data-stu-id="0164f-121">See also</span></span>

- [<span data-ttu-id="0164f-122">IAssemblyCache 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0164f-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
