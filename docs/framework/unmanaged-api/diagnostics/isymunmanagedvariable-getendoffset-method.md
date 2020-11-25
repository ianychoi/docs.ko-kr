---
title: ISymUnmanagedVariable::GetEndOffset 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: cf4179f839b62409d5b2185f3e11e8e732c29187
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721870"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="c9030-102">ISymUnmanagedVariable::GetEndOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="c9030-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="c9030-103">부모 내에서이 변수의 끝 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9030-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="c9030-104">범위 내의 지역 변수인 경우 끝 오프셋은 범위에 대해 정의 된 오프셋에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9030-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9030-105">구문</span><span class="sxs-lookup"><span data-stu-id="c9030-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9030-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c9030-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c9030-107">제한이 `ULONG32` 끝 오프셋을 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c9030-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9030-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="c9030-108">Return Value</span></span>  

 <span data-ttu-id="c9030-109">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="c9030-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9030-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c9030-110">Requirements</span></span>  

 <span data-ttu-id="c9030-111">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="c9030-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9030-112">참조</span><span class="sxs-lookup"><span data-stu-id="c9030-112">See also</span></span>

- [<span data-ttu-id="c9030-113">ISymUnmanagedVariable 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c9030-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c9030-114">GetStartOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="c9030-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
