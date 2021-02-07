---
description: '자세히 알아보기: MDAInfo Structure'
title: MDAInfo 구조체
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 5c42537a68d38e6cff3d70dcb796cd733ce64a1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679760"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="383ef-103">MDAInfo 구조체</span><span class="sxs-lookup"><span data-stu-id="383ef-103">MDAInfo Structure</span></span>

<span data-ttu-id="383ef-104">`Event_MDAFired`MDA (관리 디버깅 도우미) 만들기를 트리거하는 이벤트에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-104">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="383ef-105">구문</span><span class="sxs-lookup"><span data-stu-id="383ef-105">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="383ef-106">구성원</span><span class="sxs-lookup"><span data-stu-id="383ef-106">Members</span></span>  
  
|<span data-ttu-id="383ef-107">멤버</span><span class="sxs-lookup"><span data-stu-id="383ef-107">Member</span></span>|<span data-ttu-id="383ef-108">설명</span><span class="sxs-lookup"><span data-stu-id="383ef-108">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="383ef-109">현재 MDA의 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-109">The title of the current MDA.</span></span> <span data-ttu-id="383ef-110">제목은 이벤트를 트리거한 오류의 종류를 설명 합니다 `Event_MDAFired` .</span><span class="sxs-lookup"><span data-stu-id="383ef-110">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="383ef-111">현재 MDA에서 제공 하는 출력 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-111">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="383ef-112">설명</span><span class="sxs-lookup"><span data-stu-id="383ef-112">Remarks</span></span>  

 <span data-ttu-id="383ef-113">Mda (관리 디버깅 도우미)는 CLR (공용 언어 런타임)과 함께 작동 하 여 런타임 실행 엔진에서 잘못 된 조건을 식별 하거나 엔진 상태에 대 한 추가 정보를 덤프 하는 등의 작업을 수행 하는 디버깅 보조 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-113">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="383ef-114">Mda는 트래핑 하기 어려운 이벤트에 대 한 XML 메시지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-114">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="383ef-115">이러한 코드는 관리 코드와 비관리 코드 간의 전환을 디버깅 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-115">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="383ef-116">MDA 생성을 트리거하는 이벤트가 발생 하면 런타임에서 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-116">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="383ef-117">호스트에서 이벤트에 대 한 알림이 발생 하도록 [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 를 호출 하 여 [IActionOnCLREvent](iactiononclrevent-interface.md) 인스턴스를 등록 하지 않은 경우 `Event_MDAFired` 런타임은 호스트 되지 않은 기본 동작을 사용 하 여 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-117">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="383ef-118">호스트에서이 이벤트에 대 한 처리기를 등록 한 경우 런타임은 디버거가 프로세스에 연결 되어 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-118">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="383ef-119">인 경우 런타임이 디버거로 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-119">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="383ef-120">디버거가 계속 되 면 호스트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-120">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="383ef-121">디버거가 연결 되지 않은 경우 런타임에서는를 호출 `IActionOnCLREvent::OnEvent` 하 고 인스턴스에 대 한 포인터를 `MDAInfo` `data` 매개 변수로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-121">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="383ef-122">호스트는 mda를 활성화 하 고 MDA가 활성화 될 때 알리도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-122">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="383ef-123">이렇게 하면 호스트에서 기본 동작을 재정의 하 고 이벤트를 발생 시킨 관리 되는 스레드를 중단 하 여 프로세스 상태가 손상 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-123">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="383ef-124">Mda를 사용 하는 방법에 대 한 자세한 내용은 [관리 디버깅 도우미를 사용 하 여 오류 진단](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="383ef-124">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="383ef-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="383ef-125">Requirements</span></span>  

 <span data-ttu-id="383ef-126">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="383ef-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="383ef-127">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="383ef-127">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="383ef-128">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="383ef-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="383ef-129">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="383ef-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383ef-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="383ef-130">See also</span></span>

- [<span data-ttu-id="383ef-131">호스팅 구조체</span><span class="sxs-lookup"><span data-stu-id="383ef-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="383ef-132">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="383ef-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
