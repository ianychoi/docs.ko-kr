---
description: '자세히 알아보기: ISymUnmanagedWriter3:: Commit 메서드'
title: ISymUnmanagedWriter3::Commit 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 308f5d3a16cf60a0e77a581a318d6fd6c398b3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761761"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="ffdb0-103">ISymUnmanagedWriter3::Commit 메서드</span><span class="sxs-lookup"><span data-stu-id="ffdb0-103">ISymUnmanagedWriter3::Commit Method</span></span>

<span data-ttu-id="ffdb0-104">지금까지 작성 된 변경 내용을 스트림에 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="ffdb0-104">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdb0-105">구문</span><span class="sxs-lookup"><span data-stu-id="ffdb0-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ffdb0-106">Return Value</span><span class="sxs-lookup"><span data-stu-id="ffdb0-106">Return Value</span></span>  

 <span data-ttu-id="ffdb0-107">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="ffdb0-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdb0-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ffdb0-108">Requirements</span></span>  

 <span data-ttu-id="ffdb0-109">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="ffdb0-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdb0-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ffdb0-110">See also</span></span>

- [<span data-ttu-id="ffdb0-111">ISymUnmanagedWriter3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ffdb0-111">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
