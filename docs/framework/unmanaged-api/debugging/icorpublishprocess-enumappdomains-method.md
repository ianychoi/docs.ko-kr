---
description: 'ICorPublishProcess:: EnumAppDomains 메서드에 대해 자세히 알아보세요.'
title: ICorPublishProcess::EnumAppDomains 메서드
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: c7834b23967ab467c1589ee31929bf346b4b3b8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794613"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="d0f5d-103">ICorPublishProcess::EnumAppDomains 메서드</span><span class="sxs-lookup"><span data-stu-id="d0f5d-103">ICorPublishProcess::EnumAppDomains Method</span></span>

<span data-ttu-id="d0f5d-104">이 [ICorPublishProcess](icorpublishprocess-interface.md)에서 참조 하는 프로세스의 응용 프로그램 도메인에 대 한 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-104">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f5d-105">구문</span><span class="sxs-lookup"><span data-stu-id="d0f5d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0f5d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d0f5d-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="d0f5d-107">제한이 이 프로세스에서 응용 프로그램 도메인의 컬렉션을 반복할 수 있도록 하는 [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) 인스턴스의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-107">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0f5d-108">설명</span><span class="sxs-lookup"><span data-stu-id="d0f5d-108">Remarks</span></span>  

 <span data-ttu-id="d0f5d-109">응용 프로그램 도메인 목록은 메서드가 호출 될 때 존재 하는 응용 프로그램 도메인의 스냅숏을 기반으로 합니다 `EnumAppDomains` .</span><span class="sxs-lookup"><span data-stu-id="d0f5d-109">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="d0f5d-110">이 메서드는 새 최신 목록을 만들기 위해 두 번 이상 호출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-110">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="d0f5d-111">기존 목록은이 메서드에 대 한 후속 호출의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-111">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="d0f5d-112">프로세스가 종료 된 경우 `EnumAppDomains` 는 HRESULT 값 CORDBG_E_PROCESS_TERMINATED을 사용 하 여 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-112">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f5d-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d0f5d-113">Requirements</span></span>  

 <span data-ttu-id="d0f5d-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0f5d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0f5d-115">**헤더:** CorPub .idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d0f5d-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d0f5d-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0f5d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0f5d-117">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f5d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f5d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0f5d-118">See also</span></span>

- [<span data-ttu-id="d0f5d-119">ICorPublishProcess 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d0f5d-119">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
