---
title: 전역 어셈블리 캐시
description: .NET용 공용 언어 런타임이 설치된 경우 컴퓨터 전체 코드 캐시인 전역 어셈블리 캐시를 이해합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 57d18c01bd6261e8207d8ad3849a3a7da9a24b6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264610"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="c5063-103">전역 어셈블리 캐시</span><span class="sxs-lookup"><span data-stu-id="c5063-103">Global Assembly Cache</span></span>

<span data-ttu-id="c5063-104">공용 언어 런타임이 설치된 각 컴퓨터에는 전역 어셈블리 캐시라는 컴퓨터 수준의 코드 캐시가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="c5063-105">전역 어셈블리 캐시에는 컴퓨터의 여러 애플리케이션에서 공유하도록 특별히 지정된 어셈블리가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="c5063-106">필요할 경우에만 어셈블리를 전역 어셈블리 캐시에 설치하여 어셈블리를 공유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="c5063-107">일반적으로 어셈블리 공유가 명시적으로 필요하지 않은 경우에는 어셈블리 종속성은 pirvate으로 유지하고 어셈블리를 애플리케이션 디렉터리에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="c5063-108">또한 어셈블리가 COM interop 또는 비관리 코드에 액세스 가능하게 설정하기 위해 어셈블리를 전역 어셈블리 캐시에 설치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5063-109">어셈블리를 전역 어셈블리 캐시에 명시적으로 설치하지 않으려고 하는 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="c5063-110">애플리케이션을 구성하는 어셈블리 중 하나를 전역 어셈블리 캐시에 배치하면 **xcopy** 명령을 사용하여 애플리케이션 디렉터리를 복사하는 방식으로 애플리케이션을 더 이상 복제하거나 설치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="c5063-111">전역 어셈블리 캐시의 어셈블리도 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="c5063-112">어셈블리를 전역 어셈블리 캐시에 배포하는 다음 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="c5063-113">전역 어셈블리 캐시와 함께 사용하도록 디자인된 설치 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="c5063-114">이것은 어셈블리를 전역 어셈블리 캐시에 설치하기 위한 기본 설정된 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="c5063-115">Windows SDK에서 제공된 [전역 어셈블리 캐시 도구(Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)라는 개발자 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c5063-116">배포 시나리오에서는 전역 어셈블리 캐시에 어셈블리를 설치할 때 Windows Installer를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="c5063-117">전역 어셈블리 캐시 도구는 개발 시나리오에서만 사용합니다. 그 이유는 이 도구가 어셈블리 참조 계산 및 Windows Installer를 사용할 때 제공되는 기타 기능을 제공하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="c5063-118">.NET Framework 4부터 전역 어셈블리 캐시의 기본 위치는 **%windir%\Microsoft.NET\assembly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="c5063-119">.NET Framework의 이전 버전에서 기본 위치는 **%windir%\assembly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="c5063-120">관리자는 대부분 쓰기 및 실행 액세스를 제어하기 위해 ACL(액세스 제어 목록)을 사용하여 systemroot 디렉터리를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="c5063-121">전역 어셈블리 캐시는 systemroot 디렉터리의 하위 디렉터리에 설치되므로 해당 디렉터리의 ACL을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="c5063-122">관리자 권한을 가진 사용자만 전역 어셈블리 캐시에서 파일을 삭제하도록 허용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="c5063-123">전역 어셈블리 캐시에 배포된 어셈블리에 강력한 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="c5063-124">어셈블리가 전역 어셈블리 캐시에 추가되면 어셈블리를 구성하는 모든 파일에 대한 무결성 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="c5063-125">예를 들어 파일이 변경되었지만 매니페스트가 변경을 반영하지 않는 경우 캐시는 이러한 무결성 검사를 수행하여 어셈블리가 변조되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c5063-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5063-126">참조</span><span class="sxs-lookup"><span data-stu-id="c5063-126">See also</span></span>

- [<span data-ttu-id="c5063-127">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="c5063-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="c5063-128">어셈블리 및 전역 어셈블리 캐시 사용</span><span class="sxs-lookup"><span data-stu-id="c5063-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="c5063-129">강력한 이름의 어셈블리</span><span class="sxs-lookup"><span data-stu-id="c5063-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
