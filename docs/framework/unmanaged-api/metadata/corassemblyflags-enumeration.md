---
description: '다음에 대 한 자세한 정보: CorAssemblyFlags 열거형'
title: CorAssemblyFlags 열거형
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: bd74534b1f607eea15f1d8615f66723428ddae3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678490"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="1922e-103">CorAssemblyFlags 열거형</span><span class="sxs-lookup"><span data-stu-id="1922e-103">CorAssemblyFlags Enumeration</span></span>

<span data-ttu-id="1922e-104">어셈블리 컴파일에 적용되는 메타데이터를 설명하는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-104">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1922e-105">구문</span><span class="sxs-lookup"><span data-stu-id="1922e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1922e-106">구성원</span><span class="sxs-lookup"><span data-stu-id="1922e-106">Members</span></span>  
  
|<span data-ttu-id="1922e-107">멤버</span><span class="sxs-lookup"><span data-stu-id="1922e-107">Member</span></span>|<span data-ttu-id="1922e-108">설명</span><span class="sxs-lookup"><span data-stu-id="1922e-108">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="1922e-109">어셈블리 참조에 해시 되지 않은 전체 공개 키가 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-109">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="1922e-110">프로세서 아키텍처가 지정 되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-110">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="1922e-111">프로세서 아키텍처가 중립 상태임을 나타냅니다 (PE32).</span><span class="sxs-lookup"><span data-stu-id="1922e-111">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="1922e-112">프로세서 아키텍처가 x86 (PE32) 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-112">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="1922e-113">프로세서 아키텍처가 Itanium (PE32 +) 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-113">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="1922e-114">프로세서 아키텍처가 AMD X64 (PE32 +) 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-114">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="1922e-115">프로세서 아키텍처가 ARM (PE32) 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-115">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="1922e-116">어셈블리가 참조 어셈블리 임을 나타냅니다. 즉, 모든 아키텍처에 적용 되지만 모든 아키텍처에서 실행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-116">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="1922e-117">따라서 플래그는와 동일 합니다 `afPA_Mask` .</span><span class="sxs-lookup"><span data-stu-id="1922e-117">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="1922e-118">프로세서 아키텍처 플래그를 레코드로 전파 해야 함을 나타냅니다 `AssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="1922e-118">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="1922e-119">프로세서 아키텍처를 설명 하는 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-119">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="1922e-120">프로세서 아키텍처 설명을 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-120">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="1922e-121">인덱스에 대 한 프로세서 아키텍처 플래그의 이동 횟수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-121">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="1922e-122">의에서 해당 하는 값을 나타냅니다 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1922e-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="1922e-123">의에서 해당 하는 값을 나타냅니다 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1922e-123">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="1922e-124">런타임에 다른 게시자의 어셈블리에 어셈블리의 대상을 지정할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-124">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="1922e-125">내용 유형을 설명 하는 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-125">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="1922e-126">기본 콘텐츠 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-126">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="1922e-127">Windows 런타임 내용 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1922e-127">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1922e-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1922e-128">Requirements</span></span>  

 <span data-ttu-id="1922e-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1922e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1922e-130">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="1922e-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1922e-131">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1922e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1922e-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1922e-132">See also</span></span>

- [<span data-ttu-id="1922e-133">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="1922e-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
