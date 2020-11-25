---
title: CeeSectionRelocType 열거형
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732712"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="2fe45-102">CeeSectionRelocType 열거형</span><span class="sxs-lookup"><span data-stu-id="2fe45-102">CeeSectionRelocType Enumeration</span></span>

<span data-ttu-id="2fe45-103">`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)에 대 한 호출에서 내보낸 명령의 형식에 영향을 주는 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe45-104">구문</span><span class="sxs-lookup"><span data-stu-id="2fe45-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="2fe45-105">멤버</span><span class="sxs-lookup"><span data-stu-id="2fe45-105">Members</span></span>  
  
|<span data-ttu-id="2fe45-106">멤버</span><span class="sxs-lookup"><span data-stu-id="2fe45-106">Member</span></span>|<span data-ttu-id="2fe45-107">설명</span><span class="sxs-lookup"><span data-stu-id="2fe45-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="2fe45-108">섹션을 기준으로 하 여 `reloc` .reloc 섹션에 아무 것도 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="2fe45-109">`reloc`포인터 크기의 위치에 대해를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="2fe45-110">이는 플랫폼에 따라 BASED_HIGHLOW 또는 BASED_DIR64으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="2fe45-111">`reloc`32 비트 숫자의 상위 16 비트에 대해를 생성 합니다. 여기서 하위 16 비트는 .reloc 테이블의 다음 단어에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="2fe45-112">.Reloc 섹션에 아무 것도 보내지 않고 토큰 맵 재배치를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="2fe45-113">값이 상대 주소 픽스업 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="2fe45-114">섹션을 기준으로 하 여 `reloc` .reloc 섹션에 아무 것도 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="2fe45-115">섹션의 `reloc` 가상 주소가 아니라 섹션의 파일 위치를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="2fe45-116">코드 상대 주소 픽스업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="2fe45-117">`reloc`Ia64 명령에서 64 비트 주소에 대 한를 생성 `movl` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="2fe45-118">`reloc`64 비트 주소에 대 한를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="2fe45-119">`reloc`Ia64 명령의 25 비트 PC 상대 주소에 대해를 생성 `br.call` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="2fe45-120">`reloc`Ia64 명령에서 64 비트 PC 상대 주소에 대해를 생성 `brl.call` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="2fe45-121">`reloc`태그가 지정 된 포인터 값에 사용 되는 30 비트 섹션 상대를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="2fe45-122">이 열거형에 대 한 추가를 내부 이름 배열에 반영 하는 데 도움이 되는 센티널 값 `reloc` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="2fe45-123">밑을 내보내지 않도록 지정 합니다 `reloc` .</span><span class="sxs-lookup"><span data-stu-id="2fe45-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="2fe45-124">메모리의 미리 픽스업 콘텐츠가 섹션 오프셋이 아닌 포인터 임을 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fe45-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2fe45-125">Requirements</span></span>  

 <span data-ttu-id="2fe45-126">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2fe45-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fe45-127">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="2fe45-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fe45-128">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fe45-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2fe45-129">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fe45-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe45-130">참조</span><span class="sxs-lookup"><span data-stu-id="2fe45-130">See also</span></span>

- [<span data-ttu-id="2fe45-131">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="2fe45-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="2fe45-132">ICeeGen 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2fe45-132">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="2fe45-133">AddSectionReloc 메서드</span><span class="sxs-lookup"><span data-stu-id="2fe45-133">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)
