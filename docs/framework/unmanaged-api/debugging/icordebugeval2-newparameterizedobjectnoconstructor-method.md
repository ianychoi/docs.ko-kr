---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 796c6aa4c42a037fe612b4b1ee5267a678cf5224
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729644"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="4482a-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 메서드</span><span class="sxs-lookup"><span data-stu-id="4482a-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="4482a-103">생성자 메서드 호출을 시도 하지 않고 지정 된 클래스의 매개 변수가 있는 새 형식 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="4482a-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4482a-104">구문</span><span class="sxs-lookup"><span data-stu-id="4482a-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4482a-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4482a-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="4482a-106">진행 인스턴스화할 개체의 클래스를 나타내는 ICorDebugClass 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="4482a-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="4482a-107">진행 전달 된 형식 인수의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4482a-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="4482a-108">진행 각각 인스턴스화되는 개체에 대 한 형식 인수를 나타내는 ICorDebugType 개체를 가리키는 포인터의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="4482a-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4482a-109">설명</span><span class="sxs-lookup"><span data-stu-id="4482a-109">Remarks</span></span>  

 <span data-ttu-id="4482a-110">`NewParameterizedObjectNoConstructor`잘못 된 수의 형식 인수 또는 잘못 된 형식의 인수 형식이 전달 되 면 메서드가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="4482a-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4482a-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4482a-111">Requirements</span></span>  

 <span data-ttu-id="4482a-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4482a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4482a-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4482a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4482a-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4482a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4482a-115">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4482a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
