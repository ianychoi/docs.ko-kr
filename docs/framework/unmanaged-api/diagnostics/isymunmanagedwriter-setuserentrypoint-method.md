---
title: ISymUnmanagedWriter::SetUserEntryPoint 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: a1c3506758221c3a2b578d93488a4377c1b86a21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683500"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="f0e5f-102">ISymUnmanagedWriter::SetUserEntryPoint 메서드</span><span class="sxs-lookup"><span data-stu-id="f0e5f-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>

<span data-ttu-id="f0e5f-103">이 모듈의 진입점인 사용자 정의 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0e5f-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="f0e5f-104">예를 들어이 진입점은 main 이전의 컴파일러 생성 스텁이 아닌 사용자의 main 메서드 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0e5f-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e5f-105">구문</span><span class="sxs-lookup"><span data-stu-id="f0e5f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0e5f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f0e5f-106">Parameters</span></span>  

 `entryMethod`  
 <span data-ttu-id="f0e5f-107">진행 사용자 진입점인 메서드의 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="f0e5f-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0e5f-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="f0e5f-108">Return Value</span></span>  

 <span data-ttu-id="f0e5f-109">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f0e5f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e5f-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f0e5f-110">Requirements</span></span>  

 <span data-ttu-id="f0e5f-111">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="f0e5f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e5f-112">참조</span><span class="sxs-lookup"><span data-stu-id="f0e5f-112">See also</span></span>

- [<span data-ttu-id="f0e5f-113">ISymUnmanagedWriter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f0e5f-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
