---
title: CorTypeAttr 열거형
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: 50ce4e5e6125eae493bb62032d5c6bd8887c1afb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699094"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="38a68-102">CorTypeAttr 열거형</span><span class="sxs-lookup"><span data-stu-id="38a68-102">CorTypeAttr Enumeration</span></span>

<span data-ttu-id="38a68-103">형식 메타데이터를 나타내는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a68-104">구문</span><span class="sxs-lookup"><span data-stu-id="38a68-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="38a68-105">멤버</span><span class="sxs-lookup"><span data-stu-id="38a68-105">Members</span></span>  
  
|<span data-ttu-id="38a68-106">멤버</span><span class="sxs-lookup"><span data-stu-id="38a68-106">Member</span></span>|<span data-ttu-id="38a68-107">설명</span><span class="sxs-lookup"><span data-stu-id="38a68-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="38a68-108">형식 표시 유형 정보에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="38a68-109">형식이 공용 범위에 있지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="38a68-110">형식이 공용 범위에 있음을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="38a68-111">형식이 공용 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="38a68-112">형식이 전용 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="38a68-113">형식이 패밀리 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="38a68-114">형식이 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="38a68-115">형식이 패밀리 및 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="38a68-116">형식이 패밀리 또는 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="38a68-117">형식에 대 한 레이아웃 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="38a68-118">이 형식의 필드를 자동으로 배치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="38a68-119">이 형식의 필드를 순차적으로 배치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="38a68-120">필드 레이아웃이 명시적으로 제공 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="38a68-121">형식에 대 한 의미 체계 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="38a68-122">형식을 클래스로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="38a68-123">형식을 인터페이스로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="38a68-124">형식을 추상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="38a68-125">형식을 확장할 수 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="38a68-126">클래스 이름을 특수 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-126">Specifies that the class name is special.</span></span> <span data-ttu-id="38a68-127">해당 이름에서 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="38a68-128">형식을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="38a68-129">형식을 serialize 할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="38a68-130">이 형식이 Windows 런타임 형식이 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="38a68-131">문자열을 인코딩하고 형식을 지정 하는 방법에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="38a68-132">이 형식이 LPTSTR를 ANSI로 해석 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="38a68-133">이 형식이 LPTSTR를 유니코드로 해석 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="38a68-134">이 형식이 LPTSTR를 자동으로 해석 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="38a68-135">에 지정 된 대로 형식이 비표준 인코딩을 포함 하도록 지정 합니다 `CustomFormatMask` .</span><span class="sxs-lookup"><span data-stu-id="38a68-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="38a68-136">네이티브 interop에 대 한 비표준 인코딩 정보를 가져오려면이 마스크를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="38a68-137">이러한 두 비트 값의 의미는 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="38a68-138">정적 필드에 대 한 첫 번째 액세스를 시도 하기 전에 형식을 초기화 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="38a68-139">형식을 내보내도록 지정 하 고 형식 전달자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="38a68-140">이 플래그와 아래 플래그는 공용 언어 런타임에서 내부적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="38a68-141">공용 언어 런타임에서 이름 인코딩을 확인 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="38a68-142">형식에 연결 된 보안이 있음을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a68-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38a68-143">요구 사항</span><span class="sxs-lookup"><span data-stu-id="38a68-143">Requirements</span></span>  

 <span data-ttu-id="38a68-144">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a68-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a68-145">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="38a68-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="38a68-146">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a68-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a68-147">참조</span><span class="sxs-lookup"><span data-stu-id="38a68-147">See also</span></span>

- [<span data-ttu-id="38a68-148">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="38a68-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
