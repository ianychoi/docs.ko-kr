---
description: '자세히 알아보기: ISymUnmanagedReader2:: GetMethodByVersionPreRemap 메서드'
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b827821f529b9917c6bbb3452f0c3fe3283f1ee9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763724"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="5e008-103">ISymUnmanagedReader2::GetMethodByVersionPreRemap 메서드</span><span class="sxs-lookup"><span data-stu-id="5e008-103">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>

<span data-ttu-id="5e008-104">메서드 토큰과 편집 및 계속 버전 번호가 지정 된 경우 기호 판독기 메서드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-104">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="5e008-105">버전 번호는 1부터 시작 하 고 편집 하며 계속 하기 작업의 결과로 메서드가 변경 될 때마다 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e008-106">구문</span><span class="sxs-lookup"><span data-stu-id="5e008-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e008-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5e008-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="5e008-108">진행 메서드 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-108">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="5e008-109">진행 메서드 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5e008-110">제한이 반환 된 [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-110">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e008-111">Return Value</span><span class="sxs-lookup"><span data-stu-id="5e008-111">Return Value</span></span>  

 <span data-ttu-id="5e008-112">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5e008-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e008-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5e008-113">Requirements</span></span>  

 <span data-ttu-id="5e008-114">**헤더:** CorSym.</span><span class="sxs-lookup"><span data-stu-id="5e008-114">**Header:** CorSym.idl.</span></span> <span data-ttu-id="5e008-115">CorSym</span><span class="sxs-lookup"><span data-stu-id="5e008-115">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e008-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e008-116">See also</span></span>

- [<span data-ttu-id="5e008-117">ISymUnmanagedReader2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5e008-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
