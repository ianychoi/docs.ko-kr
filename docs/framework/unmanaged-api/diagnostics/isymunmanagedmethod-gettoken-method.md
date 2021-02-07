---
description: '자세히 알아보기: ISymUnmanagedMethod:: GetToken 메서드'
title: ISymUnmanagedMethod::GetToken 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: fde9936a6e79b9d1fff5b38ee7242cf5bb71369d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721309"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="84b85-103">ISymUnmanagedMethod::GetToken 메서드</span><span class="sxs-lookup"><span data-stu-id="84b85-103">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="84b85-104">이 메서드에 대한 메타데이터 토큰을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="84b85-104">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b85-105">구문</span><span class="sxs-lookup"><span data-stu-id="84b85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84b85-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="84b85-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="84b85-107">제한이 `mdMethodDef` 메타 데이터를 포함 하는 데 필요한 버퍼의 크기 (문자 수)를 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="84b85-107">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84b85-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="84b85-108">Return Value</span></span>  

 <span data-ttu-id="84b85-109">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="84b85-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b85-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="84b85-110">Requirements</span></span>  

 <span data-ttu-id="84b85-111">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="84b85-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b85-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84b85-112">See also</span></span>

- [<span data-ttu-id="84b85-113">ISymUnmanagedMethod 인터페이스</span><span class="sxs-lookup"><span data-stu-id="84b85-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
