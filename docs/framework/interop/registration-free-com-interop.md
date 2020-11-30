---
title: 등록이 필요 없는 COM Interop
description: 등록이 필요 없는 COM interop을 사용하면 Windows 레지스트리를 사용하여 어셈블리 정보를 저장하지 않고도 구성 요소를 활성화할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
ms.openlocfilehash: f61ad954215aecfc9380a47de788d36f327ab0b3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239538"
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="41782-103">등록이 필요 없는 COM Interop</span><span class="sxs-lookup"><span data-stu-id="41782-103">Registration-Free COM Interop</span></span>

<span data-ttu-id="41782-104">등록이 필요 없는 COM interop는 Windows 레지스트리를 사용하여 어셈블리 정보를 저장하지 않고 구성 요소를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-104">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="41782-105">배포 중 컴퓨터에 구성 요소를 등록하는 대신 바인딩 및 활성화 정보를 포함하는 Win32 스타일의 매니페스트 파일을 디자인 타임에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="41782-105">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="41782-106">레지스트리 키 대신 이러한 매니페스트 파일에서 개체 활성화를 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-106">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="41782-107">배포 중에 등록하는 대신 어셈블리에 대해 등록이 필요 없는 활성화를 사용하면 다음 두 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41782-107">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
- <span data-ttu-id="41782-108">컴퓨터에 둘 이상의 버전을 설치할 때 활성화되는 DLL 버전을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41782-108">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
- <span data-ttu-id="41782-109">최종 사용자는 XCOPY 또는 FTP를 사용하여 해당 컴퓨터의 적절한 디렉터리에 애플리케이션을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41782-109">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="41782-110">그런 다음 해당 디렉터리에서 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41782-110">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="41782-111">이 섹션에서는 등록이 필요 없는 COM interop에 필요한 두 가지 매니페스트 유형인 애플리케이션 및 구성 요소 매니페스트를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-111">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="41782-112">이러한 매니페스트는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="41782-112">These manifests are XML files.</span></span> <span data-ttu-id="41782-113">애플리케이션 개발자가 만드는 애플리케이션 매니페스트에는 어셈블리와 어셈블리 종속성을 설명하는 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41782-113">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="41782-114">구성 요소 개발자가 만드는 구성 요소 매니페스트에는 그러지 않은 경우 Windows 레지스트리에 있는 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41782-114">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="41782-115">등록이 필요 없는 COM Interop에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="41782-115">Requirements for registration-free COM interop</span></span>  
  
1. <span data-ttu-id="41782-116">등록이 필요 없는 COM interop에 대한 지원은 라이브러리 어셈블리 형식, 특히 어셈블리가 관리되지 않는지(COM Side-by-side) 또는 관리되는지(.NET 기반)에 따라 약간씩 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="41782-116">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="41782-117">다음 표에서는 각 어셈블리의 형식에 대한 운영 체제 및 .NET Framework 버전 요구 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41782-117">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="41782-118">어셈블리 형식</span><span class="sxs-lookup"><span data-stu-id="41782-118">Assembly type</span></span>|<span data-ttu-id="41782-119">운영 체제</span><span class="sxs-lookup"><span data-stu-id="41782-119">Operating system</span></span>|<span data-ttu-id="41782-120">.NET Framework 버전</span><span class="sxs-lookup"><span data-stu-id="41782-120">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="41782-121">동시 Side-by-side</span><span class="sxs-lookup"><span data-stu-id="41782-121">COM side-by-side</span></span>|<span data-ttu-id="41782-122">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="41782-122">Microsoft Windows XP</span></span>|<span data-ttu-id="41782-123">필요하지 않음.</span><span class="sxs-lookup"><span data-stu-id="41782-123">Not required.</span></span>|  
    |<span data-ttu-id="41782-124">.NET 기반</span><span class="sxs-lookup"><span data-stu-id="41782-124">.NET-based</span></span>|<span data-ttu-id="41782-125">Windows XP SP2</span><span class="sxs-lookup"><span data-stu-id="41782-125">Windows XP with SP2</span></span>|<span data-ttu-id="41782-126">.NET Framework 버전 1.1 이상</span><span class="sxs-lookup"><span data-stu-id="41782-126">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="41782-127">Windows Server 2003 제품군은 .NET 기반 어셈블리에 대해서도 등록이 필요 없는 COM interop을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-127">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="41782-128">.NET 기반 클래스가 COM의 등록이 필요 없는 활성화와 호환되려면 클래스에 매개 변수가 없는 생성자가 있어야 하고 public이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-128">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a parameterless constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="41782-129">등록이 필요 없는 활성화를 위한 COM 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="41782-129">Configuring COM components for registration-free activation</span></span>  
  
1. <span data-ttu-id="41782-130">COM 구성 요소가 등록이 필요 없는 활성화에 참여하려면 Side-by-side 어셈블리로 배포되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-130">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="41782-131">Side-by-side 어셈블리는 관리되지 않는 어셈블리입니다.</span><span class="sxs-lookup"><span data-stu-id="41782-131">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="41782-132">자세한 내용은 [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies)(Side-by-Side 어셈블리 사용)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41782-132">For more information, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
     <span data-ttu-id="41782-133">COM Side-by-side-어셈블리를 사용하려면 .NET 기반 애플리케이션 개발자가 바인딩 및 활성화 정보를 포함하는 애플리케이션 매니페스트를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-133">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="41782-134">관리되지 않는 Side-by-side 어셈블리에 대한 지원은 Windows XP 운영 체제에 기본 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="41782-134">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="41782-135">운영 체제에서 지원하는 COM 런타임은 활성화되는 구성 요소가 레지스트리에 없는 경우 애플리케이션 매니페스트에서 활성화 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="41782-135">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="41782-136">Windows XP에 설치된 COM 구성 요소의 경우 등록이 필요 없는 활성화는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="41782-136">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="41782-137">Side-by-Side 어셈블리를 애플리케이션에 추가하는 방법에 대한 자세한 내용은 [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies)(Side-by-Side 어셈블리 사용)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41782-137">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="41782-138">Side-by-side 실행은 여러 버전의 런타임 및 특정 런타임 버전을 사용하는 여러 버전의 애플리케이션 및 구성 요소가 동시에 같은 컴퓨터에서 실행될 수 있도록 하는 .NET Framework 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="41782-138">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="41782-139">Side-by-side 실행 및 Side-by-side 어셈블리는 Side-by-side 기능을 제공하는 서로 다른 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="41782-139">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41782-140">참조</span><span class="sxs-lookup"><span data-stu-id="41782-140">See also</span></span>

- [<span data-ttu-id="41782-141">방법: 등록이 필요 없는 활성화를 위한 .NET Framework 기반 COM 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="41782-141">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)
