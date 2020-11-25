---
title: ICorRuntimeHost::CreateDomainEx 메서드
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: d6d9e06b6ed40bb0e5a65fd64f8bca7abe3afa84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715682"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="78a5f-102">ICorRuntimeHost::CreateDomainEx 메서드</span><span class="sxs-lookup"><span data-stu-id="78a5f-102">ICorRuntimeHost::CreateDomainEx Method</span></span>

<span data-ttu-id="78a5f-103">응용 프로그램 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-103">Creates an application domain.</span></span> <span data-ttu-id="78a5f-104">호출자는 형식의 인스턴스에 대 한 형식의 인터페이스 포인터를 수신 합니다 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="78a5f-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78a5f-105">이 메서드를 사용 하면 호출자가 IAppDomainSetup 인스턴스를 전달 하 여 반환 된 인스턴스의 추가 기능을 구성할 수 있습니다 <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="78a5f-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a5f-106">구문</span><span class="sxs-lookup"><span data-stu-id="78a5f-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78a5f-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="78a5f-107">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="78a5f-108">진행 도메인에 친숙 한 이름을 지정 하는 데 사용 되는 선택적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="78a5f-109">이 이름은 디버거와 같은 사용자 인터페이스에 표시 되어 도메인을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="78a5f-110">진행 `IAppDomainSetup` [ICorRuntimeHost:: CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) 메서드를 호출 하 여 얻은 형식의 선택적 인터페이스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="78a5f-111">진행 `IIdentity` 권한 집합을 설정 하기 위해 보안 정책을 통해 매핑된 증명 정보를 나타내는 인스턴스에 대 한 포인터의 선택적 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="78a5f-112">`IIdentity` [Createevidence](icorruntimehost-createevidence-method.md) 메서드를 호출 하 여 개체를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="78a5f-113">제한이 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> 도메인을 추가로 제어 하는 데 사용할 수 있는 인스턴스에 대 한 형식의 인터페이스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78a5f-114">반환 값</span><span class="sxs-lookup"><span data-stu-id="78a5f-114">Return Value</span></span>  
  
|<span data-ttu-id="78a5f-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78a5f-115">HRESULT</span></span>|<span data-ttu-id="78a5f-116">설명</span><span class="sxs-lookup"><span data-stu-id="78a5f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78a5f-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="78a5f-117">S_OK</span></span>|<span data-ttu-id="78a5f-118">작업이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-118">The operation was successful.</span></span>|  
|<span data-ttu-id="78a5f-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="78a5f-119">S_FALSE</span></span>|<span data-ttu-id="78a5f-120">작업을 완료 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="78a5f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78a5f-121">E_FAIL</span></span>|<span data-ttu-id="78a5f-122">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="78a5f-123">메서드가 E_FAIL 반환 하는 경우 해당 프로세스에서 CLR (공용 언어 런타임)을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="78a5f-124">호스팅 Api에 대 한 후속 호출은 HOST_E_CLRNOTAVAILABLE을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78a5f-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78a5f-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78a5f-126">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78a5f-127">설명</span><span class="sxs-lookup"><span data-stu-id="78a5f-127">Remarks</span></span>  

 <span data-ttu-id="78a5f-128">`CreateDomainEx` 호출자가 응용 프로그램 도메인을 구성 하기 위해 속성 값으로 인스턴스를 전달 하도록 허용 하 여 [Createdomain](icorruntimehost-createdomain-method.md) 의 기능을 확장 합니다 `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="78a5f-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a5f-129">요구 사항</span><span class="sxs-lookup"><span data-stu-id="78a5f-129">Requirements</span></span>  

 <span data-ttu-id="78a5f-130">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78a5f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a5f-131">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="78a5f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78a5f-132">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78a5f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78a5f-133">**.NET Framework 버전:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="78a5f-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a5f-134">참조</span><span class="sxs-lookup"><span data-stu-id="78a5f-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="78a5f-135">CreateDomain 메서드</span><span class="sxs-lookup"><span data-stu-id="78a5f-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="78a5f-136">ICorRuntimeHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="78a5f-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
