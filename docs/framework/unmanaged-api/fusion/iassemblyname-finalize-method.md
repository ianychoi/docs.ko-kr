---
title: IAssemblyName::Finalize 메서드
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
ms.openlocfilehash: 842b878fac1e2590eb6ea0b29ebee0d46e818474
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727928"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="02062-102">IAssemblyName::Finalize 메서드</span><span class="sxs-lookup"><span data-stu-id="02062-102">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="02062-103">소멸자가 호출 되기 전에이 [IAssemblyName](iassemblyname-interface.md) 개체가 리소스를 해제 하 고 다른 정리 작업을 수행할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="02062-103">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02062-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="02062-104">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="02062-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="02062-105">Requirements</span></span>  

 <span data-ttu-id="02062-106">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="02062-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02062-107">**헤더:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="02062-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="02062-108">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02062-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02062-109">참조</span><span class="sxs-lookup"><span data-stu-id="02062-109">See also</span></span>

- [<span data-ttu-id="02062-110">IAssemblyName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="02062-110">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
