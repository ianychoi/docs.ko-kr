---
description: '자세히 알아보기: CorPinvokeMap 열거형'
title: CorPinvokeMap 열거형
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8285632725096b4e6afc85fe54a89f12fc899dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784264"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="922d3-103">CorPinvokeMap 열거형</span><span class="sxs-lookup"><span data-stu-id="922d3-103">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="922d3-104">PInvoke 호출에 대 한 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-104">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922d3-105">구문</span><span class="sxs-lookup"><span data-stu-id="922d3-105">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="922d3-106">구성원</span><span class="sxs-lookup"><span data-stu-id="922d3-106">Members</span></span>  
  
|<span data-ttu-id="922d3-107">멤버</span><span class="sxs-lookup"><span data-stu-id="922d3-107">Member</span></span>|<span data-ttu-id="922d3-108">설명</span><span class="sxs-lookup"><span data-stu-id="922d3-108">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="922d3-109">지정 된 각 멤버 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-109">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="922d3-110">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-110">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="922d3-111">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-111">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="922d3-112">문자열을 다중 바이트 문자열로 마샬링합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-112">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="922d3-113">문자열을 유니코드 2바이트 문자로 마샬링합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-113">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="922d3-114">문자열을 대상 운영 체제에 맞게 자동으로 마샬링합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-114">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="922d3-115">Windows NT, Windows 2000, Windows XP 및 Windows Server 2003 제품군의 기본값은 유니코드입니다. 기본값은 Windows 98 및 Windows Me의 ANSI입니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-115">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="922d3-116">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-116">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="922d3-117">ANSI 문자 집합에서 정확히 일치 하는 항목이 없는 유니코드 문자의 최적 매핑을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-117">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="922d3-118">유니코드 문자의 최적 매핑을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-118">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="922d3-119">이 경우 매핑할 수 없는 모든 문자는 '? '로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-119">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="922d3-120">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="922d3-121">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-121">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="922d3-122">Interop 마샬러에서 매핑할 때 매핑할 문자가 없으면 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-122">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="922d3-123">Interop 마샬러가 매핑할 수 없는 문자를 발견 한 경우 예외를 throw 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-123">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="922d3-124">예약됨</span><span class="sxs-lookup"><span data-stu-id="922d3-124">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="922d3-125">특성화 된 메서드에서 반환 하기 전에 호출 수신자가 Win32 함수를 호출할 수 있도록 허용 `SetLastError` 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-125">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="922d3-126">예약됨</span><span class="sxs-lookup"><span data-stu-id="922d3-126">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="922d3-127">기본 플랫폼 호출 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-127">Use the default platform calling convention.</span></span> <span data-ttu-id="922d3-128">예를 들어 Windows에서 기본값은이 `StdCall` 고 Windows CE .net의 경우입니다 `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="922d3-128">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="922d3-129">`Cdecl`호출 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-129">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="922d3-130">이 경우 호출자는 스택을 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-130">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="922d3-131">이를 통해 함수를 호출할 수 있습니다 `varargs` . 즉, 매개 변수 수를 사용 하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-131">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="922d3-132">`StdCall`호출 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-132">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="922d3-133">이 경우 호출 수신자는 스택을 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-133">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="922d3-134">이는 플랫폼 호출을 사용하여 관리되지 않는 함수를 호출하는 기본 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-134">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="922d3-135">`ThisCall`호출 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-135">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="922d3-136">이 경우 첫 번째 매개 변수는 포인터이 `this` 고 레지스터 ECX에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-136">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="922d3-137">다른 매개 변수는 스택에 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-137">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="922d3-138">`ThisCall`호출 규칙은 관리 되지 않는 DLL에서 내보낸 클래스에서 메서드를 호출 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-138">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="922d3-139">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-139">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="922d3-140">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="922d3-140">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="922d3-141">요구 사항</span><span class="sxs-lookup"><span data-stu-id="922d3-141">Requirements</span></span>  

 <span data-ttu-id="922d3-142">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="922d3-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="922d3-143">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="922d3-143">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="922d3-144">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="922d3-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="922d3-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="922d3-145">See also</span></span>

- [<span data-ttu-id="922d3-146">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="922d3-146">Metadata Enumerations</span></span>](metadata-enumerations.md)
