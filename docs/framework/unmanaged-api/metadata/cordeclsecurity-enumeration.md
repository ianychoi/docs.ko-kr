---
description: '자세히 알아보기: CorDeclSecurity 열거형'
title: CorDeclSecurity 열거형
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 4c4b57c09ea8b3ec1b98ff120d72a5920dc5aa4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784550"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="6846f-103">CorDeclSecurity 열거형</span><span class="sxs-lookup"><span data-stu-id="6846f-103">CorDeclSecurity Enumeration</span></span>

<span data-ttu-id="6846f-104">선언적 보안을 사용하여 수행할 수 있는 보안 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-104">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6846f-105">구문</span><span class="sxs-lookup"><span data-stu-id="6846f-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="6846f-106">구성원</span><span class="sxs-lookup"><span data-stu-id="6846f-106">Members</span></span>  
  
|<span data-ttu-id="6846f-107">멤버</span><span class="sxs-lookup"><span data-stu-id="6846f-107">Member</span></span>|<span data-ttu-id="6846f-108">설명</span><span class="sxs-lookup"><span data-stu-id="6846f-108">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="6846f-109">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-109">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="6846f-110">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-110">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="6846f-111">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-111">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="6846f-112">호출 스택의 상위에 있는 모든 호출자에게 현재 사용 권한 개체가 지정한 사용 권한이 부여되었어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-112">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="6846f-113">스택의 상위 호출자에 게 리소스에 대 한 액세스 권한이 부여 되지 않더라도 호출 코드에서 현재 사용 권한 개체로 식별 되는 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-113">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="6846f-114">호출자에 게 액세스 권한이 부여 된 경우에도 현재 사용 권한 개체로 지정 된 리소스에 액세스 하는 기능이 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-114">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="6846f-115">코드에 다른 리소스에 액세스할 수 있는 권한이 부여되더라도 이 권한 개체가 지정한 리소스에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-115">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="6846f-116">직접 실행 호출자에 게 지정 된 기간 동안 지정 된 사용 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-116">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="6846f-117">다른 클래스를 상속 하거나 메서드를 재정의 하는 파생 된 클래스에는 지정 된 사용 권한이 부여 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-117">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="6846f-118">호출자는 코드를 실행 하는 데 필요한 최소 사용 권한을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-118">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="6846f-119">이 작업은 어셈블리 범위 내에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-119">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="6846f-120">호출자는 선택적 (실행 하는 데 필요 하지 않음) 인 추가 사용 권한을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-120">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="6846f-121">이 요청은 특별히 요청되지 않은 다른 모든 사용 권한을 암시적으로 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-121">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="6846f-122">이 작업은 어셈블리 범위 내에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-122">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="6846f-123">악용 될 수 있는 사용 권한에 대 한 호출자의 요청은 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-123">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="6846f-124">이 작업은 어셈블리 범위 내에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-124">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="6846f-125">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-125">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="6846f-126">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-126">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="6846f-127">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-127">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="6846f-128">직접 실행 호출자에게 지정된 사용 권한이 부여되었어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-128">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="6846f-129">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-129">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="6846f-130">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-130">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="6846f-131">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-131">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="6846f-132">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-132">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="6846f-133">예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6846f-133">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6846f-134">요구 사항</span><span class="sxs-lookup"><span data-stu-id="6846f-134">Requirements</span></span>  

 <span data-ttu-id="6846f-135">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6846f-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6846f-136">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="6846f-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6846f-137">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6846f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6846f-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6846f-138">See also</span></span>

- [<span data-ttu-id="6846f-139">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="6846f-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
