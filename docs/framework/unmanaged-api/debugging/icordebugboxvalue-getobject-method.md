---
description: '자세히 알아보기: ICorDebugBoxValue:: GetObject 메서드'
title: ICorDebugBoxValue::GetObject 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: fc5376fa7ddbbeae3464427b34caf991d0a2f59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711863"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="190cf-103">ICorDebugBoxValue::GetObject 메서드</span><span class="sxs-lookup"><span data-stu-id="190cf-103">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="190cf-104">Boxed 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="190cf-104">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190cf-105">구문</span><span class="sxs-lookup"><span data-stu-id="190cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="190cf-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="190cf-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="190cf-107">제한이 Boxed 값을 나타내는 ICorDebugObjectValue 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="190cf-107">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="190cf-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="190cf-108">Requirements</span></span>  

 <span data-ttu-id="190cf-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="190cf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="190cf-110">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="190cf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="190cf-111">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="190cf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="190cf-112">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="190cf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
