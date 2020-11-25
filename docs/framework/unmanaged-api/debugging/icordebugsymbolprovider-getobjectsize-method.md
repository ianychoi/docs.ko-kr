---
title: ICorDebugSymbolProvider::GetObjectSize 메서드
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 4937ff1be7736f98be9efb9b01bdb322bf33e037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730810"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="d8157-102">ICorDebugSymbolProvider::GetObjectSize 메서드</span><span class="sxs-lookup"><span data-stu-id="d8157-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="d8157-103">typespec 서명을 기준으로 개체의 개체 크기를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8157-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8157-104">구문</span><span class="sxs-lookup"><span data-stu-id="d8157-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8157-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d8157-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="d8157-106">[in] typespec 서명의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="d8157-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="d8157-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="d8157-107">typeSig</span></span>  
 <span data-ttu-id="d8157-108">[in] typespec 서명입니다.</span><span class="sxs-lookup"><span data-stu-id="d8157-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="d8157-109">[out] 개체 크기에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d8157-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8157-110">설명</span><span class="sxs-lookup"><span data-stu-id="d8157-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8157-111">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8157-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8157-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d8157-112">Requirements</span></span>  

 <span data-ttu-id="d8157-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d8157-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8157-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8157-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8157-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8157-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8157-116">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8157-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8157-117">참조</span><span class="sxs-lookup"><span data-stu-id="d8157-117">See also</span></span>

- [<span data-ttu-id="d8157-118">ICorDebugSymbolProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d8157-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="d8157-119">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d8157-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
