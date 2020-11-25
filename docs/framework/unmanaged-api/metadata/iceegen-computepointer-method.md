---
title: ICeeGen::ComputePointer 메서드
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 41a3b9c77fc766b2fa39b406dedbb3203cc97ad9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715474"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="e41cf-102">ICeeGen::ComputePointer 메서드</span><span class="sxs-lookup"><span data-stu-id="e41cf-102">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="e41cf-103">지정 된 코드 섹션의 버퍼를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="e41cf-104">이 메서드는 사용 되지 않으므로 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41cf-105">구문</span><span class="sxs-lookup"><span data-stu-id="e41cf-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e41cf-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e41cf-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="e41cf-107">진행 버퍼를 반환할 코드 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="e41cf-108">진행 포인터를 가져올 메서드의 상대 가상 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="e41cf-109">제한이 반환 된 버퍼에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41cf-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e41cf-110">Requirements</span></span>  

 <span data-ttu-id="e41cf-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e41cf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41cf-112">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="e41cf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e41cf-113">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e41cf-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e41cf-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41cf-115">참조</span><span class="sxs-lookup"><span data-stu-id="e41cf-115">See also</span></span>

- [<span data-ttu-id="e41cf-116">ICeeGen 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e41cf-116">ICeeGen Interface</span></span>](iceegen-interface.md)
