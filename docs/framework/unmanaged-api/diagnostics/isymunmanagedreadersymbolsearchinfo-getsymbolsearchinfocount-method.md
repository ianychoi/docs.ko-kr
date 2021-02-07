---
description: '자세히 알아보기: ISymUnmanagedReaderSymbolSearchInfo:: GetSymbolSearchInfoCount 메서드'
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: b8bfa61397850c3f960fe30c0136e0a8b074cf1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763594"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="7c7d9-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount 메서드</span><span class="sxs-lookup"><span data-stu-id="7c7d9-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="7c7d9-104">기호 검색 정보의 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7c7d9-104">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7d9-105">구문</span><span class="sxs-lookup"><span data-stu-id="7c7d9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c7d9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7c7d9-106">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="7c7d9-107">] out] `ULONG32` 검색 정보를 포함 하는 데 필요한 버퍼의 크기를 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7c7d9-107">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c7d9-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="7c7d9-108">Return Value</span></span>  

 <span data-ttu-id="7c7d9-109">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="7c7d9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7d9-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7c7d9-110">Requirements</span></span>  

 <span data-ttu-id="7c7d9-111">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="7c7d9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7d9-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c7d9-112">See also</span></span>

- [<span data-ttu-id="7c7d9-113">ISymUnmanagedReaderSymbolSearchInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7c7d9-113">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
