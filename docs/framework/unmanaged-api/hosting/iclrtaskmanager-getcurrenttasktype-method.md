---
title: ICLRTaskManager::GetCurrentTaskType 메서드
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728786"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="31328-102">ICLRTaskManager::GetCurrentTaskType 메서드</span><span class="sxs-lookup"><span data-stu-id="31328-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="31328-103">현재 실행 중인 작업의 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31328-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31328-104">구문</span><span class="sxs-lookup"><span data-stu-id="31328-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31328-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="31328-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="31328-106">제한이 현재 실행 중인 작업의 유형을 나타내는 [Etasktype](etasktype-enumeration.md) 열거형의 값에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="31328-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31328-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="31328-107">Requirements</span></span>  

 <span data-ttu-id="31328-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31328-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31328-109">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="31328-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31328-110">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31328-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31328-111">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31328-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31328-112">참조</span><span class="sxs-lookup"><span data-stu-id="31328-112">See also</span></span>

- [<span data-ttu-id="31328-113">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="31328-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
