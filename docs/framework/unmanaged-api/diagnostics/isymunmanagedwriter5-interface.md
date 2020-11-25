---
title: ISymUnmanagedWriter5 인터페이스
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 894f3b0e45df2c681cbdec1f154703be64f32fc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725796"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="568da-102">ISymUnmanagedWriter5 인터페이스</span><span class="sxs-lookup"><span data-stu-id="568da-102">ISymUnmanagedWriter5 Interface</span></span>

<span data-ttu-id="568da-103">ISymUnmanagedWriter5 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="568da-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568da-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="568da-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="568da-105">메서드</span><span class="sxs-lookup"><span data-stu-id="568da-105">Methods</span></span>  

 <span data-ttu-id="568da-106">이 인터페이스에는 다음과 같은 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="568da-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="568da-107">메서드</span><span class="sxs-lookup"><span data-stu-id="568da-107">Method</span></span>|<span data-ttu-id="568da-108">설명</span><span class="sxs-lookup"><span data-stu-id="568da-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="568da-109">CloseMapTokensToSourceSpans 메서드</span><span class="sxs-lookup"><span data-stu-id="568da-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="568da-110">토큰-소스 범위 매핑 정보에 대 한 특수 사용자 지정 데이터 섹션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="568da-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="568da-111">닫힌 후에는 더 이상 매핑 정보를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="568da-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="568da-112">MapTokenToSourceSpan 메서드</span><span class="sxs-lookup"><span data-stu-id="568da-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="568da-113">지정 된 소스 파일의 지정 된 소스 줄 범위에 지정 된 메타 데이터 토큰을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="568da-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="568da-114">[OpenMapTokensToSourceSpans method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) 및 [CloseMapTokensToSourceSpans 메서드에](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)대 한 호출 사이에 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="568da-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="568da-115">OpenMapTokensToSourceSpans 메서드</span><span class="sxs-lookup"><span data-stu-id="568da-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="568da-116">특수 한 사용자 지정 데이터 섹션을 열어 토큰 대 소스 범위 매핑 정보를로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="568da-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="568da-117">메서드가 이미 열려 있거나 그 반대의 경우에는이 섹션을 열 때 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="568da-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="568da-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="568da-118">Requirements</span></span>  

 <span data-ttu-id="568da-119">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="568da-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568da-120">참조</span><span class="sxs-lookup"><span data-stu-id="568da-120">See also</span></span>

- [<span data-ttu-id="568da-121">진단 기호 저장소 인터페이스</span><span class="sxs-lookup"><span data-stu-id="568da-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="568da-122">ISymUnmanagedWriter4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="568da-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
