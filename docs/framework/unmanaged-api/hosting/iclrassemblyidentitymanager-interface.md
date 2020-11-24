---
title: ICLRAssemblyIdentityManager 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: 41d049c931091d2cc0b41bd1e9d74b3c15d7878d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679262"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="b953c-102">ICLRAssemblyIdentityManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b953c-102">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="b953c-103">호스트와 어셈블리에 대 한 CLR (공용 언어 런타임) 간의 통신을 지 원하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b953c-104">메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-104">Methods</span></span>  
  
|<span data-ttu-id="b953c-105">메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-105">Method</span></span>|<span data-ttu-id="b953c-106">설명</span><span class="sxs-lookup"><span data-stu-id="b953c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b953c-107">GetBindingIdentityFromFile 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="b953c-108">지정 된 파일 경로에서 어셈블리의 어셈블리 id 바인딩 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="b953c-109">GetBindingIdentityFromStream 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="b953c-110">지정 된 스트림의 어셈블리에 대 한 정식 어셈블리 id 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="b953c-111">GetCLRAssemblyReferenceList 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-111">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="b953c-112">제공 된 부분 어셈블리 id 목록에서 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="b953c-113">GetProbingAssembliesFromReference 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-113">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="b953c-114">지정 된 id를 사용 하 여 어셈블리에서 참조 하는 어셈블리 id의 [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="b953c-115">GetReferencedAssembliesFromFile 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-115">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="b953c-116">지정 된 파일 경로에서 어셈블리가 참조 하는 어셈블리의 목록을 포함 하는 [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="b953c-117">GetReferencedAssembliesFromStream 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="b953c-118">지정 된 스트림의 어셈블리에서 참조 하는 어셈블리 `ICLRReferenceAssemblyEnum` 에 대 한 어셈블리 id 데이터를 포함 하는 개체에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="b953c-119">IsStronglyNamed 메서드</span><span class="sxs-lookup"><span data-stu-id="b953c-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="b953c-120">지정 된 어셈블리에 강력한 이름이 지정 되었는지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b953c-121">설명</span><span class="sxs-lookup"><span data-stu-id="b953c-121">Remarks</span></span>  

 <span data-ttu-id="b953c-122">를 사용 `ICLRAssemblyIdentityManager` 하 여 인스턴스를 가져오고 `ICLRAssemblyReferenceList` 어셈블리 id를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b953c-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b953c-123">Requirements</span></span>  

 <span data-ttu-id="b953c-124">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b953c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b953c-125">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b953c-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b953c-126">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b953c-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b953c-127">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b953c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b953c-128">참조</span><span class="sxs-lookup"><span data-stu-id="b953c-128">See also</span></span>

- [<span data-ttu-id="b953c-129">ICLRAssemblyReferenceList 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b953c-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b953c-130">ICLRProbingAssemblyEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b953c-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="b953c-131">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b953c-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
