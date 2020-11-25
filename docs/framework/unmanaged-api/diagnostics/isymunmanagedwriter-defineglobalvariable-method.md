---
title: ISymUnmanagedWriter::DefineGlobalVariable 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: bc389b7247a6b1d6ce16cb3cf350f1672213b2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716423"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="f58ae-102">ISymUnmanagedWriter::DefineGlobalVariable 메서드</span><span class="sxs-lookup"><span data-stu-id="f58ae-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="f58ae-103">단일 전역 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58ae-104">구문</span><span class="sxs-lookup"><span data-stu-id="f58ae-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f58ae-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f58ae-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="f58ae-106">진행 전역 변수 이름을 정의 하는에 대 한 포인터입니다 `WCHAR` .</span><span class="sxs-lookup"><span data-stu-id="f58ae-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f58ae-107">진행 전역 변수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="f58ae-108">진행 `ULONG32` 버퍼의 크기 (문자)를 나타내는입니다 `signature` .</span><span class="sxs-lookup"><span data-stu-id="f58ae-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="f58ae-109">진행 전역 변수 서명입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f58ae-110">진행 주소 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f58ae-111">진행 매개 변수 사양의 첫 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f58ae-112">진행 매개 변수 사양의 두 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f58ae-113">진행 매개 변수 사양의 세 번째 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f58ae-114">반환 값</span><span class="sxs-lookup"><span data-stu-id="f58ae-114">Return Value</span></span>  

 <span data-ttu-id="f58ae-115">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f58ae-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f58ae-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f58ae-116">Requirements</span></span>  

 <span data-ttu-id="f58ae-117">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="f58ae-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58ae-118">참조</span><span class="sxs-lookup"><span data-stu-id="f58ae-118">See also</span></span>

- [<span data-ttu-id="f58ae-119">ISymUnmanagedWriter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f58ae-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f58ae-120">DefineLocalVariable 메서드</span><span class="sxs-lookup"><span data-stu-id="f58ae-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="f58ae-121">DefineGlobalVariable2 메서드</span><span class="sxs-lookup"><span data-stu-id="f58ae-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
