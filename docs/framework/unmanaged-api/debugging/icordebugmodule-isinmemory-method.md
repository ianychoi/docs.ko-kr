---
description: '자세히 알아보기: ICorDebugModule:: IsInMemory 메서드'
title: ICorDebugModule::IsInMemory 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 41454ede15e1d45775af8fb0ab7a6b571d9c0e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660091"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="eecb9-103">ICorDebugModule::IsInMemory 메서드</span><span class="sxs-lookup"><span data-stu-id="eecb9-103">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="eecb9-104">이 모듈이 메모리에만 있는지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="eecb9-104">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eecb9-105">구문</span><span class="sxs-lookup"><span data-stu-id="eecb9-105">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eecb9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eecb9-106">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="eecb9-107">[out] `true` 이 모듈은 메모리에만 존재 합니다. 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="eecb9-107">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eecb9-108">설명</span><span class="sxs-lookup"><span data-stu-id="eecb9-108">Remarks</span></span>  

 <span data-ttu-id="eecb9-109">CLR (공용 언어 런타임)은 원시 바이트 스트림에서 모듈 로드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="eecb9-109">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="eecb9-110">이러한 모듈은 *메모리 내 모듈* 이라고 하며 디스크에 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecb9-110">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eecb9-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="eecb9-111">Requirements</span></span>  

 <span data-ttu-id="eecb9-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eecb9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eecb9-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eecb9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eecb9-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eecb9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eecb9-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eecb9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eecb9-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eecb9-116">See also</span></span>
