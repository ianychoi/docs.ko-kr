---
title: ISymUnmanagedScope::GetEndOffset 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 14e747e81e467019d464212e75513bdf98344916
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678365"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="00b2f-102">ISymUnmanagedScope::GetEndOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="00b2f-102">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="00b2f-103">이 범위에 대 한 끝 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="00b2f-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b2f-104">구문</span><span class="sxs-lookup"><span data-stu-id="00b2f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00b2f-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="00b2f-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="00b2f-106">제한이 `ULONG32` 끝 오프셋을 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="00b2f-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00b2f-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="00b2f-107">Return Value</span></span>  

 <span data-ttu-id="00b2f-108">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="00b2f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00b2f-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="00b2f-109">Requirements</span></span>  

 <span data-ttu-id="00b2f-110">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="00b2f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b2f-111">참조</span><span class="sxs-lookup"><span data-stu-id="00b2f-111">See also</span></span>

- [<span data-ttu-id="00b2f-112">ISymUnmanagedScope 인터페이스</span><span class="sxs-lookup"><span data-stu-id="00b2f-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="00b2f-113">GetStartOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="00b2f-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
