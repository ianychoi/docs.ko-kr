---
description: '자세히 알아보기: ICorDebugSymbolProvider2:: Get프레임 Props 메서드'
title: ICorDebugSymbolProvider2::GetFrameProps 메서드
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659558"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="dcb81-103">ICorDebugSymbolProvider2::GetFrameProps 메서드</span><span class="sxs-lookup"><span data-stu-id="dcb81-103">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="dcb81-104">메서드의 메서드 시작 상대 가상 주소 및 코드 상대 가상 주소가 지정된 부모 프레임을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb81-104">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb81-105">구문</span><span class="sxs-lookup"><span data-stu-id="dcb81-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcb81-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dcb81-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="dcb81-107">[in] 코드 상대 가상 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcb81-107">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="dcb81-108">[out] 메서드의 시작 상대 가상 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dcb81-108">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="dcb81-109">[out] 프레임의 시작 상대 가상 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dcb81-109">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcb81-110">설명</span><span class="sxs-lookup"><span data-stu-id="dcb81-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcb81-111">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb81-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb81-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dcb81-112">Requirements</span></span>  

 <span data-ttu-id="dcb81-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dcb81-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb81-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcb81-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcb81-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcb81-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcb81-116">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb81-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb81-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcb81-117">See also</span></span>

- [<span data-ttu-id="dcb81-118">ICorDebugSymbolProvider2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dcb81-118">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="dcb81-119">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dcb81-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
