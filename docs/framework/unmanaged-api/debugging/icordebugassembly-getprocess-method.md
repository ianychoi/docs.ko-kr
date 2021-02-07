---
description: '자세히 알아보기: ICorDebugAssembly:: GetProcess 메서드'
title: ICorDebugAssembly::GetProcess 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: b121d7f892f6e2e2aa76290d4aee51767c72e9fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754150"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="a71d2-103">ICorDebugAssembly::GetProcess 메서드</span><span class="sxs-lookup"><span data-stu-id="a71d2-103">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="a71d2-104">이 ICorDebugAssembly 인스턴스가 실행 되 고 있는 프로세스에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a71d2-104">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a71d2-105">구문</span><span class="sxs-lookup"><span data-stu-id="a71d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a71d2-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a71d2-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="a71d2-107">제한이 프로세스를 나타내는 ICorDebugProcess 인터페이스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a71d2-107">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a71d2-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a71d2-108">Requirements</span></span>  

 <span data-ttu-id="a71d2-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a71d2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a71d2-110">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a71d2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a71d2-111">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a71d2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a71d2-112">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a71d2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
