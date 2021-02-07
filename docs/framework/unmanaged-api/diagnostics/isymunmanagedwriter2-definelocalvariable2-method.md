---
description: ISymUnmanagedWriter2::D efineLocalVariable2 메서드에 대해 자세히 알아보세요.
title: ISymUnmanagedWriter2::DefineLocalVariable2 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 169a086b8420b5dbe20af8e16b21d5b41a958ead
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761813"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="dcc53-103">ISymUnmanagedWriter2::DefineLocalVariable2 메서드</span><span class="sxs-lookup"><span data-stu-id="dcc53-103">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="dcc53-104">현재 어휘 범위에 단일 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="dcc53-105">이 메서드는 범위 전체의 여러 홈이 있는 동일한 이름의 변수에 대해 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="dcc53-106">그러나이 경우 `startOffset` 및 `endOffset` 매개 변수의 값이 겹치지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc53-107">구문</span><span class="sxs-lookup"><span data-stu-id="dcc53-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcc53-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dcc53-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="dcc53-109">진행 지역 변수 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-109">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="dcc53-110">진행 지역 변수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-110">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="dcc53-111">진행 시그니처의 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-111">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="dcc53-112">진행 주소 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="dcc53-113">진행 매개 변수 사양의 첫 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="dcc53-114">진행 매개 변수 사양의 두 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="dcc53-115">진행 매개 변수 사양의 세 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="dcc53-116">진행 변수의 시작 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="dcc53-117">이 매개 변수는 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-117">This parameter is optional.</span></span> <span data-ttu-id="dcc53-118">0 인 경우이 매개 변수는 무시 되 고 변수는 전체 범위에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="dcc53-119">0이 아닌 값인 경우 변수는 현재 범위의 오프셋 내에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="dcc53-120">진행 변수의 끝 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="dcc53-121">이 매개 변수는 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-121">This parameter is optional.</span></span> <span data-ttu-id="dcc53-122">0 인 경우이 매개 변수는 무시 되 고 변수는 전체 범위에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="dcc53-123">0이 아닌 값인 경우 변수는 현재 범위의 오프셋 내에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcc53-124">Return Value</span><span class="sxs-lookup"><span data-stu-id="dcc53-124">Return Value</span></span>  

 <span data-ttu-id="dcc53-125">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc53-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcc53-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dcc53-126">Requirements</span></span>  

 <span data-ttu-id="dcc53-127">**헤더:** CorSym</span><span class="sxs-lookup"><span data-stu-id="dcc53-127">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc53-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcc53-128">See also</span></span>

- [<span data-ttu-id="dcc53-129">ISymUnmanagedWriter2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dcc53-129">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="dcc53-130">DefineLocalVariable 메서드</span><span class="sxs-lookup"><span data-stu-id="dcc53-130">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
