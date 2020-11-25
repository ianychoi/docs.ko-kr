---
title: GetAppIdAuthority 함수
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 5e731ac1c652b8b4505073a3a10463ae0ce21ac0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724496"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="c8521-102">GetAppIdAuthority 함수</span><span class="sxs-lookup"><span data-stu-id="c8521-102">GetAppIdAuthority Function</span></span>

<span data-ttu-id="c8521-103">응용 프로그램 id 및 참조에 대 한 키를 관리 하는 [Iappidauthority](iappidauthority-interface.md) 인스턴스에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8521-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8521-104">구문</span><span class="sxs-lookup"><span data-stu-id="c8521-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8521-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c8521-105">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="c8521-106">제한이 반환 된 `IAppIdAuthority` 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c8521-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8521-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c8521-107">Requirements</span></span>  

 <span data-ttu-id="c8521-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8521-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8521-109">**헤더:** 격리. h</span><span class="sxs-lookup"><span data-stu-id="c8521-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c8521-110">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8521-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8521-111">참조</span><span class="sxs-lookup"><span data-stu-id="c8521-111">See also</span></span>

- [<span data-ttu-id="c8521-112">IAppIdAuthority 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c8521-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="c8521-113">Fusion 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="c8521-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
