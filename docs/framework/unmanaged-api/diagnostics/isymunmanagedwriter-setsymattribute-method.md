---
description: '자세히 알아보기: ISymUnmanagedWriter:: SetSymAttribute 메서드'
title: ISymUnmanagedWriter::SetSymAttribute 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 0509e6430646fa67112b29d30d5053eb4a541415
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761995"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="f57b7-103">ISymUnmanagedWriter::SetSymAttribute 메서드</span><span class="sxs-lookup"><span data-stu-id="f57b7-103">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="f57b7-104">이름에 따라 사용자 지정 특성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-104">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="f57b7-105">이러한 특성은 메타 데이터 사용자 지정 특성과 달리 기호 저장소에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-105">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57b7-106">구문</span><span class="sxs-lookup"><span data-stu-id="f57b7-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f57b7-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f57b7-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="f57b7-108">진행 특성이 정의 되는 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-108">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="f57b7-109">진행 `WCHAR` 특성 이름을 포함 하는에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-109">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="f57b7-110">진행 `ULONG32` 배열의 크기를 나타내는입니다 `data` .</span><span class="sxs-lookup"><span data-stu-id="f57b7-110">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="f57b7-111">진행 특성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-111">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f57b7-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="f57b7-112">Return Value</span></span>  

 <span data-ttu-id="f57b7-113">메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f57b7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57b7-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f57b7-114">Requirements</span></span>  

 <span data-ttu-id="f57b7-115">**헤더:** CorSym, CorSym</span><span class="sxs-lookup"><span data-stu-id="f57b7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57b7-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f57b7-116">See also</span></span>

- [<span data-ttu-id="f57b7-117">ISymUnmanagedWriter 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f57b7-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
