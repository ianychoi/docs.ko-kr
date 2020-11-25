---
title: AssemblyComparisonResult 열거형
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: cde25a9507006c89ef6490c13ae82033f04c2931
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731035"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="c6d7d-102">AssemblyComparisonResult 열거형</span><span class="sxs-lookup"><span data-stu-id="c6d7d-102">AssemblyComparisonResult Enumeration</span></span>

<span data-ttu-id="c6d7d-103">[CompareAssemblyIdentity](compareassemblyidentity-function.md) 함수에 의해 결정 된 두 어셈블리 id의 동일성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d7d-104">구문</span><span class="sxs-lookup"><span data-stu-id="c6d7d-104">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="c6d7d-105">멤버</span><span class="sxs-lookup"><span data-stu-id="c6d7d-105">Members</span></span>  
  
|<span data-ttu-id="c6d7d-106">멤버 이름</span><span class="sxs-lookup"><span data-stu-id="c6d7d-106">Member name</span></span>|<span data-ttu-id="c6d7d-107">설명</span><span class="sxs-lookup"><span data-stu-id="c6d7d-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="c6d7d-108">비교의 모든 어셈블리 필드가 일치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="c6d7d-109">.NET Framework 버전 2.0에서 어셈블리 버전 번호의 CLR (공용 언어 런타임 버전) 통합에 따라 어셈블리가 동일한 것으로 간주 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="c6d7d-110">.NET Framework 2.0에서 어셈블리 버전 번호의 CLR 통합을 기반으로 하는 어셈블리의 부분 일치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="c6d7d-111">어셈블리의 부분 일치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="c6d7d-112">버전 번호의 레거시 통합을 기반으로 하는 어셈블리의 부분 일치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="c6d7d-113">단순한 이름의 어셈블리에 대 한 부분 일치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="c6d7d-114">는 .NET Framework의 레거시 버전에서 버전 번호의 CLR 통합에 따라 어셈블리가 동일한 것으로 간주 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="c6d7d-115">버전 번호가 무시 된 두 개의 단순한 명명 된 어셈블리 사이에 일치 하는 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="c6d7d-116">두 어셈블리 사이에 일치 하는 항목이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="c6d7d-117">는 부분적 으로만 일치 하는 버전 번호를 제외 하 고 두 어셈블리가 일치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="c6d7d-118">일치 하지 않는 버전 번호를 제외 하 고 두 어셈블리가 일치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="c6d7d-119">같지 않음의 원인을 알 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6d7d-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c6d7d-120">Requirements</span></span>  

 <span data-ttu-id="c6d7d-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6d7d-122">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c6d7d-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c6d7d-123">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d7d-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6d7d-124">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6d7d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d7d-125">참조</span><span class="sxs-lookup"><span data-stu-id="c6d7d-125">See also</span></span>

- [<span data-ttu-id="c6d7d-126">CompareAssemblyIdentity 함수</span><span class="sxs-lookup"><span data-stu-id="c6d7d-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="c6d7d-127">Fusion 열거형</span><span class="sxs-lookup"><span data-stu-id="c6d7d-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
