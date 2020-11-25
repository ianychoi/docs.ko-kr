---
title: ICeeGen::GetMethodBuffer 메서드
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: e9c2dab9f30be6e5eea8f6570b297f8df11b6fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715332"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="c65b2-102">ICeeGen::GetMethodBuffer 메서드</span><span class="sxs-lookup"><span data-stu-id="c65b2-102">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="c65b2-103">지정 된 상대 가상 주소에서 메서드에 대 한 적절 한 크기의 버퍼를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c65b2-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="c65b2-104">이 메서드는 사용 되지 않으므로 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c65b2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65b2-105">구문</span><span class="sxs-lookup"><span data-stu-id="c65b2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c65b2-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c65b2-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="c65b2-107">진행 버퍼를 반환할 메서드의 상대 가상 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c65b2-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c65b2-108">제한이 반환 된 버퍼에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c65b2-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65b2-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c65b2-109">Requirements</span></span>  

 <span data-ttu-id="c65b2-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c65b2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c65b2-111">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="c65b2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c65b2-112">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c65b2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c65b2-113">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c65b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65b2-114">참조</span><span class="sxs-lookup"><span data-stu-id="c65b2-114">See also</span></span>

- [<span data-ttu-id="c65b2-115">ICeeGen 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c65b2-115">ICeeGen Interface</span></span>](iceegen-interface.md)
