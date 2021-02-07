---
description: '자세히 알아보기: ISymUnmanagedDocument:: GetLanguage 메서드'
title: ISymUnmanagedDocument::GetLanguage 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: f30636303d310ed91aa4229f52a3197a29190d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710311"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="7d028-103">ISymUnmanagedDocument::GetLanguage 메서드</span><span class="sxs-lookup"><span data-stu-id="7d028-103">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="7d028-104">이 문서의 언어 식별자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7d028-104">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d028-105">구문</span><span class="sxs-lookup"><span data-stu-id="7d028-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d028-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7d028-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="7d028-107">제한이 언어 식별자를 받는 변수에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7d028-107">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d028-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="7d028-108">Return Value</span></span>  

 <span data-ttu-id="7d028-109">메서드가 성공 하면 S_OK 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d028-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d028-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d028-110">See also</span></span>

- [<span data-ttu-id="7d028-111">ISymUnmanagedDocument 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7d028-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
