---
title: ISymUnmanagedVariable::GetName 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726888"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="d7a02-102">ISymUnmanagedVariable::GetName 메서드</span><span class="sxs-lookup"><span data-stu-id="d7a02-102">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="d7a02-103">이 변수의 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d7a02-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a02-104">구문</span><span class="sxs-lookup"><span data-stu-id="d7a02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7a02-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d7a02-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="d7a02-106">진행 매개 변수가 가리키는 버퍼의 길이입니다 `pcchName` .</span><span class="sxs-lookup"><span data-stu-id="d7a02-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d7a02-107">제한이 `ULONG32` Null 종료를 포함 하 여 이름을 포함 하는 데 필요한 버퍼의 크기 (문자 수)를 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d7a02-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d7a02-108">제한이 이름을 저장 하는 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="d7a02-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7a02-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="d7a02-109">Return Value</span></span>  

 <span data-ttu-id="d7a02-110">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="d7a02-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a02-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d7a02-111">Requirements</span></span>  

 <span data-ttu-id="d7a02-112">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="d7a02-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a02-113">참조</span><span class="sxs-lookup"><span data-stu-id="d7a02-113">See also</span></span>

- [<span data-ttu-id="d7a02-114">ISymUnmanagedVariable 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d7a02-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
