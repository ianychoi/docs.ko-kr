---
description: 'ICorPublish:: EnumProcesses 메서드에 대해 자세히 알아보세요.'
title: ICorPublish::EnumProcesses 메서드
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 2451f179301eff4caca966568f966d145e269f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721998"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="ddec9-103">ICorPublish::EnumProcesses 메서드</span><span class="sxs-lookup"><span data-stu-id="ddec9-103">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="ddec9-104">이 컴퓨터에서 실행 되는 관리 되는 프로세스의 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ddec9-104">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddec9-105">구문</span><span class="sxs-lookup"><span data-stu-id="ddec9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddec9-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ddec9-106">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="ddec9-107">검색할 프로세스의 유형을 지정 하는 [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ddec9-107">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="ddec9-108">현재 버전에서는 COR_PUB_MANAGEDONLY만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddec9-108">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="ddec9-109">프로세스의 열거자 인 [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) 인스턴스의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ddec9-109">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddec9-110">설명</span><span class="sxs-lookup"><span data-stu-id="ddec9-110">Remarks</span></span>  

 <span data-ttu-id="ddec9-111">열거자의 프로세스 컬렉션은 메서드가 호출 될 때 실행 중인 프로세스의 스냅숏을 기반으로 합니다 `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="ddec9-111">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="ddec9-112">열거자는가 호출 된 후에 종료 되거나 시작 되는 프로세스를 포함 하지 않습니다 `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="ddec9-112">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="ddec9-113">`EnumProcesses`이 [ICorPublish](icorpublish-interface.md) 인스턴스에서 메서드를 두 번 이상 호출 하 여 새로운 최신 프로세스 컬렉션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddec9-113">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="ddec9-114">기존 컬렉션은 메서드에 대 한 후속 호출의 영향을 받지 않습니다 `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="ddec9-114">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddec9-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ddec9-115">Requirements</span></span>  

 <span data-ttu-id="ddec9-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddec9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddec9-117">**헤더:** CorPub .idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ddec9-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ddec9-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddec9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddec9-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddec9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddec9-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddec9-120">See also</span></span>

- [<span data-ttu-id="ddec9-121">ICorPublish 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ddec9-121">ICorPublish Interface</span></span>](icorpublish-interface.md)
