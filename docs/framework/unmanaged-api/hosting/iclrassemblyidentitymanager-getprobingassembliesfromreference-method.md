---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 메서드
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 263058131e63205aa37f81847ed647944fef7540
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731399"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="df01e-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference 메서드</span><span class="sxs-lookup"><span data-stu-id="df01e-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="df01e-103">지정 된 id 형식을 사용 하 여 어셈블리에서 참조 하는 어셈블리 id의 [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df01e-104">구문</span><span class="sxs-lookup"><span data-stu-id="df01e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df01e-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="df01e-105">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="df01e-106">진행 Winnt.exe에 정의 된 대로 프로세서 아키텍처를 지정 하는 유효한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="df01e-107">진행 향후 확장성을 위해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="df01e-108">현재 버전의 CLR (공용 언어 런타임)에서 지 원하는 유일한 값은 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT입니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="df01e-109">진행 일반적으로 [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) 또는 [ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) 메서드 호출에서 반환 되는 불투명 어셈블리 바인딩 id입니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="df01e-110">제한이 `ICLRProbingAssemblyEnum` 로 식별 되는 어셈블리에서 참조 하는 어셈블리에 대 한 참조를 포함 하는 열거자에 대 한 인터페이스 포인터입니다 `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="df01e-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df01e-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="df01e-111">Return Value</span></span>  
  
|<span data-ttu-id="df01e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df01e-112">HRESULT</span></span>|<span data-ttu-id="df01e-113">설명</span><span class="sxs-lookup"><span data-stu-id="df01e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df01e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="df01e-114">S_OK</span></span>|<span data-ttu-id="df01e-115">메서드가 성공적으로 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="df01e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df01e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df01e-117">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="df01e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="df01e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="df01e-119">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-119">The call timed out.</span></span>|  
|<span data-ttu-id="df01e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="df01e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="df01e-121">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="df01e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="df01e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="df01e-123">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="df01e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df01e-124">E_FAIL</span></span>|<span data-ttu-id="df01e-125">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="df01e-126">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="df01e-127">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df01e-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="df01e-128">Requirements</span></span>  

 <span data-ttu-id="df01e-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df01e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df01e-130">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="df01e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df01e-131">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df01e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df01e-132">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df01e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df01e-133">참조</span><span class="sxs-lookup"><span data-stu-id="df01e-133">See also</span></span>

- [<span data-ttu-id="df01e-134">ICLRAssemblyIdentityManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="df01e-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="df01e-135">ICLRAssemblyReferenceList 인터페이스</span><span class="sxs-lookup"><span data-stu-id="df01e-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="df01e-136">ICLRProbingAssemblyEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="df01e-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
