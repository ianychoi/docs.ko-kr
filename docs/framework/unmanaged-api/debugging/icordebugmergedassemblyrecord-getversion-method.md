---
title: ICorDebugMergedAssemblyRecord::GetVersion 메서드
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 7352a77fc8f41124d7e6c78a3dfc6ccd6d3a94aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710508"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="7e39e-102">ICorDebugMergedAssemblyRecord::GetVersion 메서드</span><span class="sxs-lookup"><span data-stu-id="7e39e-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="7e39e-103">어셈블리의 버전 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e39e-104">구문</span><span class="sxs-lookup"><span data-stu-id="7e39e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e39e-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7e39e-105">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="7e39e-106">[out] 주 버전 번호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="7e39e-107">[out] 부 버전 번호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="7e39e-108">[out] 빌드 번호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="7e39e-109">[out] 수정 번호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e39e-110">설명</span><span class="sxs-lookup"><span data-stu-id="7e39e-110">Remarks</span></span>  

 <span data-ttu-id="7e39e-111">어셈블리 버전 번호에 대한 자세한 내용은 <xref:System.Version> 클래스 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e39e-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e39e-112">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e39e-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e39e-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7e39e-113">Requirements</span></span>  

 <span data-ttu-id="7e39e-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e39e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e39e-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e39e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e39e-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e39e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e39e-117">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e39e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e39e-118">참조</span><span class="sxs-lookup"><span data-stu-id="7e39e-118">See also</span></span>

- [<span data-ttu-id="7e39e-119">ICorDebugMergedAssemblyRecord 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7e39e-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7e39e-120">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7e39e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
