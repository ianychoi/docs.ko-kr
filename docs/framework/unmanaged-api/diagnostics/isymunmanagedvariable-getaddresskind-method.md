---
title: ISymUnmanagedVariable::GetAddressKind 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 6a7824949edc905a3edcd58f60d40f8b1a40c53c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726914"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="c6801-102">ISymUnmanagedVariable::GetAddressKind 메서드</span><span class="sxs-lookup"><span data-stu-id="c6801-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="c6801-103">이 변수의 주소 종류를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6801-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6801-104">구문</span><span class="sxs-lookup"><span data-stu-id="c6801-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6801-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6801-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c6801-106">제한이 값을 수신 하는에 대 한 포인터 `ULONG32` 입니다.</span><span class="sxs-lookup"><span data-stu-id="c6801-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="c6801-107">가능한 값은 [CorSymAddrKind](corsymaddrkind-enumeration.md) 열거형에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6801-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6801-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6801-108">Return Value</span></span>  

 <span data-ttu-id="c6801-109">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="c6801-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6801-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c6801-110">Requirements</span></span>  

 <span data-ttu-id="c6801-111">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="c6801-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6801-112">참조</span><span class="sxs-lookup"><span data-stu-id="c6801-112">See also</span></span>

- [<span data-ttu-id="c6801-113">ISymUnmanagedVariable 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c6801-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
