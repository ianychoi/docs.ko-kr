---
description: '자세히 알아보기: ISymUnmanagedMethod:: GetSequencePoints 메서드'
title: ISymUnmanagedMethod::GetSequencePoints 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721296"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="9eb97-103">ISymUnmanagedMethod::GetSequencePoints 메서드</span><span class="sxs-lookup"><span data-stu-id="9eb97-103">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="9eb97-104">이 메서드 내의 모든 시퀀스 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-104">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb97-105">구문</span><span class="sxs-lookup"><span data-stu-id="9eb97-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eb97-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9eb97-106">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="9eb97-107">진행 `ULONG32` `offsets` ,,,, `documents` `lines` `columns` `endLines` 및 `endColumns` 배열의 크기를 받는입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-107">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="9eb97-108">제한이 `ULONG32` 시퀀스 위치를 포함 하는 데 필요한 버퍼의 길이를 수신 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-108">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="9eb97-109">진행 시퀀스 위치에 대 한 메서드의 시작 부분에서 MSIL (Microsoft 중간 언어) 오프셋을 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-109">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="9eb97-110">진행 시퀀스 위치가 있는 문서를 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-110">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="9eb97-111">진행 시퀀스 위치가 있는 문서의 줄을 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-111">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="9eb97-112">진행 시퀀스 위치가 있는 문서의 열을 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-112">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="9eb97-113">진행 시퀀스 위치가 끝나는 문서의 줄 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-113">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="9eb97-114">진행 시퀀스 위치가 끝나는 문서의 열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-114">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9eb97-115">Return Value</span><span class="sxs-lookup"><span data-stu-id="9eb97-115">Return Value</span></span>  

 <span data-ttu-id="9eb97-116">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="9eb97-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb97-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9eb97-117">Requirements</span></span>  

 <span data-ttu-id="9eb97-118">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="9eb97-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb97-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9eb97-119">See also</span></span>

- [<span data-ttu-id="9eb97-120">ISymUnmanagedMethod 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9eb97-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
