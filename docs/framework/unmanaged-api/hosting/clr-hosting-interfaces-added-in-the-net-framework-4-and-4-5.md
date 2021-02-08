---
description: '자세한 정보: .NET Framework 4 및 4.5에 추가 된 CLR 호스팅 인터페이스'
title: .NET Framework 4 및 4.5에 추가된 CLR 호스팅 인터페이스
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: e7c5dd042822be8653d9c068e85a751aed622f06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799917"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="b0dc7-103">.NET Framework 4 및 4.5에 추가된 CLR 호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-103">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="b0dc7-104">이 섹션에서는 관리 되지 않는 호스트가 .NET Framework 4, .NET Framework 4.5 이상 버전의 CLR (공용 언어 런타임)을 해당 응용 프로그램에 통합 하는 데 사용할 수 있는 인터페이스에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-104">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="b0dc7-105">이러한 인터페이스는 호스트에서 런타임을 구성 하 고 프로세스로 로드 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="b0dc7-106">.NET Framework 4부터 모든 호스팅 인터페이스에는 다음과 같은 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-106">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="b0dc7-107">수명 관리 ( `AddRef` 및 `Release` ), 캡슐화 (암시적 컨텍스트) 및 COM을 사용 `QueryInterface` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-107">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="b0dc7-108">, 또는와 같은 COM 형식을 사용 하지 `BSTR` 않습니다 `SAFEARRAY` `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="b0dc7-108">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="b0dc7-109">[CoCreateInstance 함수](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)를 사용 하는 아파트 모델, 집계 또는 레지스트리 활성화는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-109">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0dc7-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b0dc7-110">In This Section</span></span>  

 [<span data-ttu-id="b0dc7-111">ICLRAppDomainResourceMonitor 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-111">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="b0dc7-112">응용 프로그램 도메인의 메모리 및 CPU 사용량을 검사 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-112">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="b0dc7-113">ICLRDomainManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-113">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="b0dc7-114">호스트에서 기본 응용 프로그램 도메인을 초기화 하는 데 사용 되는 응용 프로그램 도메인 관리자를 지정 하 고 초기화 속성을 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-114">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="b0dc7-115">ICLRGCManager2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-115">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="b0dc7-116">[SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) 메서드를 제공 합니다 .이 메서드를 사용 하면 호스트에서 가비지 수집 세그먼트의 크기와 가비지 수집 시스템의 최대 크기를 보다 큰 값으로 설정할 수 있습니다 `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="b0dc7-116">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="b0dc7-117">ICLRMetaHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="b0dc7-118">특정 버전의 CLR을 반환 하 고, 모든 설치 된 Clr을 나열 하 고, 모든 in-process 런타임을 나열 하 고, 활성화 인터페이스를 반환 하 고, 어셈블리를 컴파일하는 데 사용 되는 CLR 버전을 검색 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-118">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="b0dc7-119">ICLRMetaHostPolicy 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-119">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="b0dc7-120">정책 기준, 관리 되는 어셈블리, 버전 및 구성 파일을 기반으로 CLR 인터페이스를 제공 하는 [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-120">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="b0dc7-121">ICLRRuntimeInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="b0dc7-122">버전, 디렉터리 및 로드 상태를 포함 하 여 특정 런타임에 대 한 정보를 반환 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-122">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="b0dc7-123">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="b0dc7-124">강력한 이름을 사용 하 여 어셈블리에 서명 하는 데 사용할 기본 전역 정적 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-124">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="b0dc7-125">모든 [ICLRStrongName](iclrstrongname-interface.md) 메서드는 표준 COM hresult를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-125">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="b0dc7-126">ICLRStrongName2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-126">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="b0dc7-127">에서는 sha-1 512 384 256 (Secure Hash algorithm)의 SHA-2 그룹을 사용 하 여 강력한 이름을 만들 수 있는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-127">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="b0dc7-128">ICLRTask2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-128">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="b0dc7-129">는 [ICLRTask 인터페이스](iclrtask-interface.md)의 모든 기능을 제공 합니다. 또한는 현재 스레드에서 스레드 중단이 지연 될 수 있도록 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-129">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0dc7-130">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="b0dc7-130">Related Sections</span></span>  

 [<span data-ttu-id="b0dc7-131">사용되지 않는 CLR 호스팅 인터페이스 및 Coclass</span><span class="sxs-lookup"><span data-stu-id="b0dc7-131">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="b0dc7-132">.NET Framework 버전 1.0 및 1.1과 함께 제공 되는 호스팅 인터페이스에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-132">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="b0dc7-133">CLR 호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b0dc7-133">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="b0dc7-134">.NET Framework 버전 2.0, 3.0 및 3.5와 함께 제공 되는 호스팅 인터페이스에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-134">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="b0dc7-135">호스팅</span><span class="sxs-lookup"><span data-stu-id="b0dc7-135">Hosting</span></span>](index.md)  
 <span data-ttu-id="b0dc7-136">.NET Framework에서 호스팅을 도입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-136">Introduces hosting in the .NET Framework.</span></span>
