---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 메서드
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: b5ca524d223fad7ded0d56def3293eb40be69fa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703722"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="90ea2-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 메서드</span><span class="sxs-lookup"><span data-stu-id="90ea2-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="90ea2-103">지정 된 메모리 영역을 열거 하려는 시도의 결과로 디버거에 보고 하기 위해 [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) 에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ea2-104">구문</span><span class="sxs-lookup"><span data-stu-id="90ea2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90ea2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="90ea2-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="90ea2-106">진행 열거할 메모리 영역의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="90ea2-107">진행 메모리 영역의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90ea2-108">설명</span><span class="sxs-lookup"><span data-stu-id="90ea2-108">Remarks</span></span>  

 <span data-ttu-id="90ea2-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`메서드는 각 메모리 영역을 열거 하려고 시도한 후이 콜백 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="90ea2-110">열거형은이 메서드가 실패를 나타내는 HRESULT를 반환 하는 경우에도 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="90ea2-111">이 콜백에서 보고 한 지역은 중복 되거나 중복 된 지역이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90ea2-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ea2-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="90ea2-112">Requirements</span></span>  

 <span data-ttu-id="90ea2-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90ea2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ea2-114">**헤더:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="90ea2-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="90ea2-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ea2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90ea2-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ea2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ea2-117">참조</span><span class="sxs-lookup"><span data-stu-id="90ea2-117">See also</span></span>

- [<span data-ttu-id="90ea2-118">ICLRDataEnumMemoryRegionsCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="90ea2-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
