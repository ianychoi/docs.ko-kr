---
title: ICorDebugSymbolProvider::GetCodeRange 메서드
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: f61a98dbd5a65207a46e033d54f9d5f60adac201
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709130"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="968f9-102">ICorDebugSymbolProvider::GetCodeRange 메서드</span><span class="sxs-lookup"><span data-stu-id="968f9-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="968f9-103">메서드의 RVA(상대 가상 주소)가 지정된 경우 메서드 시작 주소와 크기를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="968f9-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968f9-104">구문</span><span class="sxs-lookup"><span data-stu-id="968f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="968f9-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="968f9-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="968f9-106">[in] 메서드의 RVA(상대 가상 주소)입니다.</span><span class="sxs-lookup"><span data-stu-id="968f9-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="968f9-107">[out] 메서드의 시작 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="968f9-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="968f9-108">메서드 코드 크기(메서드 코드의 바이트 수)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="968f9-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="968f9-109">설명</span><span class="sxs-lookup"><span data-stu-id="968f9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="968f9-110">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="968f9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968f9-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="968f9-111">Requirements</span></span>  

 <span data-ttu-id="968f9-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="968f9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968f9-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="968f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="968f9-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="968f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="968f9-115">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968f9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968f9-116">참조</span><span class="sxs-lookup"><span data-stu-id="968f9-116">See also</span></span>

- [<span data-ttu-id="968f9-117">ICorDebugSymbolProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="968f9-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="968f9-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="968f9-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
