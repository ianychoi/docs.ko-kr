---
description: '자세히 알아보기: IAssemblyName:: GetProperty 메서드'
title: IAssemblyName::GetProperty 메서드
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 66528bb54e1cb4adbba8fa87088065bc40c2ee15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760734"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="9ce2b-103">IAssemblyName::GetProperty 메서드</span><span class="sxs-lookup"><span data-stu-id="9ce2b-103">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="9ce2b-104">지정 된 속성 식별자가 참조 하는 속성에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ce2b-104">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce2b-105">구문</span><span class="sxs-lookup"><span data-stu-id="9ce2b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce2b-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9ce2b-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="9ce2b-107">진행 요청 된 속성에 대 한 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="9ce2b-107">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="9ce2b-108">제한이 반환 된 속성 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="9ce2b-108">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="9ce2b-109">[in, out] 의 크기 (바이트)입니다 `pvProperty` .</span><span class="sxs-lookup"><span data-stu-id="9ce2b-109">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce2b-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ce2b-110">Requirements</span></span>  

 <span data-ttu-id="9ce2b-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ce2b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce2b-112">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9ce2b-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9ce2b-113">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce2b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ce2b-114">See also</span></span>

- [<span data-ttu-id="9ce2b-115">IAssemblyName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9ce2b-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
