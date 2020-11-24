---
title: ECustomDumpFlavor 열거형
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686321"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="9cad4-102">ECustomDumpFlavor 열거형</span><span class="sxs-lookup"><span data-stu-id="9cad4-102">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="9cad4-103">오류를 보고할 때 힙 덤프의 사용자 지정 하위 집합에 포함할 항목을 나타내는 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cad4-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cad4-104">구문</span><span class="sxs-lookup"><span data-stu-id="9cad4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="9cad4-105">멤버</span><span class="sxs-lookup"><span data-stu-id="9cad4-105">Members</span></span>  
  
|<span data-ttu-id="9cad4-106">멤버</span><span class="sxs-lookup"><span data-stu-id="9cad4-106">Member</span></span>|<span data-ttu-id="9cad4-107">설명</span><span class="sxs-lookup"><span data-stu-id="9cad4-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="9cad4-108">사용자 지정 힙 덤프가 미니 덤프로 시작 되 고 동일한 메서드에 전달 된 [Custom덤프 항목](customdumpitem-structure.md) 인스턴스에 의해 지정 된 추가 데이터를 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cad4-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="9cad4-109">사용자 지정 힙 덤프가 동적으로 할당 되지 않은 모든 런타임 상태 데이터를 수집 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cad4-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cad4-110">설명</span><span class="sxs-lookup"><span data-stu-id="9cad4-110">Remarks</span></span>  

 <span data-ttu-id="9cad4-111">형식의 매개 변수는 `ECustomDumpFlavor` [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) 메서드에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cad4-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cad4-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9cad4-112">Requirements</span></span>  

 <span data-ttu-id="9cad4-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cad4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cad4-114">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9cad4-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cad4-115">**라이브러리:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9cad4-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cad4-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cad4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cad4-117">참조</span><span class="sxs-lookup"><span data-stu-id="9cad4-117">See also</span></span>

- [<span data-ttu-id="9cad4-118">ECustomDumpItemKind 열거형</span><span class="sxs-lookup"><span data-stu-id="9cad4-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="9cad4-119">ICLRErrorReportingManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9cad4-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="9cad4-120">호스팅 열거형</span><span class="sxs-lookup"><span data-stu-id="9cad4-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
