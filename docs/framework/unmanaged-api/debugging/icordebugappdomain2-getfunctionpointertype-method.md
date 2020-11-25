---
title: ICorDebugAppDomain2::GetFunctionPointerType 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: be797b1b3f288fd367d7f624e9cf33015dd114ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698275"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="a3ce1-102">ICorDebugAppDomain2::GetFunctionPointerType 메서드</span><span class="sxs-lookup"><span data-stu-id="a3ce1-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="a3ce1-103">지정 된 서명이 있는 함수에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ce1-104">구문</span><span class="sxs-lookup"><span data-stu-id="a3ce1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ce1-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a3ce1-105">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="a3ce1-106">진행 함수의 형식 인수 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a3ce1-107">진행 각각 함수의 형식 인수를 나타내는 ICorDebugType 개체를 가리키는 포인터의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="a3ce1-108">첫 번째 요소는 반환 형식입니다. 다른 각 요소는 매개 변수 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a3ce1-109">제한이 함수에 대 한 포인터를 나타내는 개체의 주소에 대 한 포인터 `ICorDebugType` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ce1-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a3ce1-110">Requirements</span></span>  

 <span data-ttu-id="a3ce1-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3ce1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ce1-112">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3ce1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3ce1-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3ce1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3ce1-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ce1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
