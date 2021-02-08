---
description: '다음에 대 한 자세한 정보: CorMethodImpl 열거형'
title: CorMethodImpl 열거형
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 157db81a72742f1f2aae7e95249b819b2396ef4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784394"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="8d0c8-103">CorMethodImpl 열거형</span><span class="sxs-lookup"><span data-stu-id="8d0c8-103">CorMethodImpl Enumeration</span></span>

<span data-ttu-id="8d0c8-104">메서드 구현 기능을 설명하는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-104">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0c8-105">구문</span><span class="sxs-lookup"><span data-stu-id="8d0c8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="8d0c8-106">구성원</span><span class="sxs-lookup"><span data-stu-id="8d0c8-106">Members</span></span>  
  
|<span data-ttu-id="8d0c8-107">멤버</span><span class="sxs-lookup"><span data-stu-id="8d0c8-107">Member</span></span>|<span data-ttu-id="8d0c8-108">설명</span><span class="sxs-lookup"><span data-stu-id="8d0c8-108">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="8d0c8-109">코드 형식을 설명 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-109">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="8d0c8-110">메서드 구현이 MSIL (Microsoft 중간 언어) 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-110">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="8d0c8-111">메서드 구현이 네이티브임을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-111">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="8d0c8-112">메서드 구현을 OPTIL 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-112">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="8d0c8-113">공용 언어 런타임에서 메서드 구현을 제공 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-113">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="8d0c8-114">코드의 관리 또는 관리 되지 않는지 여부를 나타내는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-114">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="8d0c8-115">메서드 구현이 관리 되지 않는 것으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-115">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="8d0c8-116">메서드 구현을 관리 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-116">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="8d0c8-117">메서드가 정의 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-117">Specifies that the method is defined.</span></span> <span data-ttu-id="8d0c8-118">이 플래그는 주로 병합 시나리오에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-118">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="8d0c8-119">HRESULT 변환에 대해 메서드 시그니처가 손상 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-119">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="8d0c8-120">공용 언어 런타임에서 내부용으로 사용 하도록 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-120">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="8d0c8-121">메서드가 본문을 통해 단일 스레드 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-121">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="8d0c8-122">메서드를 인라인될 수 없도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-122">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="8d0c8-123">가능한 경우 메서드를 인라인 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-123">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="8d0c8-124">메서드를 최적화 하지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-124">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="8d0c8-125">의 최대 유효 값 `CorMethodImpl` 입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-125">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d0c8-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8d0c8-126">Requirements</span></span>  

 <span data-ttu-id="8d0c8-127">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0c8-128">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="8d0c8-128">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8d0c8-129">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d0c8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0c8-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d0c8-130">See also</span></span>

- [<span data-ttu-id="8d0c8-131">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="8d0c8-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
