---
description: '자세히 알아보기: ISymUnmanagedWriter:: OpenMethod 메서드'
title: ISymUnmanagedWriter::OpenMethod 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762229"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="63083-103">ISymUnmanagedWriter::OpenMethod 메서드</span><span class="sxs-lookup"><span data-stu-id="63083-103">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="63083-104">기호 정보를 내보내는 메서드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="63083-104">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="63083-105">지정 된 메서드는 시퀀스 위치, 매개 변수 및 어휘 범위를 정의 하는 호출에 대 한 현재 메서드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63083-105">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="63083-106">전체 메서드 주위에는 암시적 어휘 범위가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63083-106">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="63083-107">이전에 닫힌 메서드를 다시 열면 해당 메서드에 대해 이전에 정의 된 기호가 모두 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="63083-107">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="63083-108">한 번에 하나의 개방형 메서드만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63083-108">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63083-109">구문</span><span class="sxs-lookup"><span data-stu-id="63083-109">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63083-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="63083-110">Parameters</span></span>  

 `method`  
 <span data-ttu-id="63083-111">진행 열려는 메서드의 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="63083-111">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63083-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="63083-112">Return Value</span></span>  

 <span data-ttu-id="63083-113">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="63083-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63083-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="63083-114">Requirements</span></span>  

 <span data-ttu-id="63083-115">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="63083-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63083-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63083-116">See also</span></span>

- [<span data-ttu-id="63083-117">ISymUnmanagedWriter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63083-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="63083-118">CloseMethod 메서드</span><span class="sxs-lookup"><span data-stu-id="63083-118">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="63083-119">OpenMethod2 메서드</span><span class="sxs-lookup"><span data-stu-id="63083-119">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
