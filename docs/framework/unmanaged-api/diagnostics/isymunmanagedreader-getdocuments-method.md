---
description: '자세히 알아보기: ISymUnmanagedReader:: GetDocuments 메서드'
title: ISymUnmanagedReader::GetDocuments 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: 8ee2a2d8e83fcbe2f5b39960fa99e11de2ab4cd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800216"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="5f76e-103">ISymUnmanagedReader::GetDocuments 메서드</span><span class="sxs-lookup"><span data-stu-id="5f76e-103">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="5f76e-104">기호 저장소에 정의 된 모든 문서의 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f76e-104">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f76e-105">구문</span><span class="sxs-lookup"><span data-stu-id="5f76e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f76e-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f76e-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="5f76e-107">[in] `pDocs` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5f76e-107">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="5f76e-108">제한이 배열 길이를 받는 변수에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f76e-108">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="5f76e-109">제한이 문서 배열을 받는 변수에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f76e-109">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f76e-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="5f76e-110">Return Value</span></span>  

 <span data-ttu-id="5f76e-111">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5f76e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f76e-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5f76e-112">Requirements</span></span>  

 <span data-ttu-id="5f76e-113">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="5f76e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f76e-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f76e-114">See also</span></span>

- [<span data-ttu-id="5f76e-115">ISymUnmanagedReader 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5f76e-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
