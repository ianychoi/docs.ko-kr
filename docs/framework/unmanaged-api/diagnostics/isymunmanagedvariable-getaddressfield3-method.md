---
description: '자세히 알아보기: ISymUnmanagedVariable:: GetAddressField3 메서드'
title: ISymUnmanagedVariable::GetAddressField3 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 286d8382857e941173c22a7aebe65adc22ab779b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762918"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="8df1a-103">ISymUnmanagedVariable::GetAddressField3 메서드</span><span class="sxs-lookup"><span data-stu-id="8df1a-103">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="8df1a-104">이 변수의 세 번째 주소 필드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8df1a-104">Gets the third address field for this variable.</span></span> <span data-ttu-id="8df1a-105">이는 주소 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="8df1a-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8df1a-106">구문</span><span class="sxs-lookup"><span data-stu-id="8df1a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8df1a-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8df1a-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8df1a-108">제한이 `ULONG32` 세 번째 주소 필드를 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8df1a-108">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8df1a-109">Return Value</span><span class="sxs-lookup"><span data-stu-id="8df1a-109">Return Value</span></span>  

 <span data-ttu-id="8df1a-110">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="8df1a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df1a-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8df1a-111">Requirements</span></span>  

 <span data-ttu-id="8df1a-112">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="8df1a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df1a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8df1a-113">See also</span></span>

- [<span data-ttu-id="8df1a-114">ISymUnmanagedVariable 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8df1a-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="8df1a-115">GetAddressField1 메서드</span><span class="sxs-lookup"><span data-stu-id="8df1a-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="8df1a-116">GetAddressField2 메서드</span><span class="sxs-lookup"><span data-stu-id="8df1a-116">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="8df1a-117">GetAddressKind 메서드</span><span class="sxs-lookup"><span data-stu-id="8df1a-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
