---
title: 완전 신뢰 모드에서 인트라넷 애플리케이션 실행
description: .NET Framework 3.5 SP1에서 완전 신뢰 모드로 인트라넷 애플리케이션을 실행합니다. 애플리케이션 및 해당 라이브러리 어셈블리를 네트워크 공유에서 완전 신뢰 어셈블리로 실행할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: 01d98a1ca7ce67088b4f04bedf7e3ef02e0ca7a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723716"
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="39641-104">완전 신뢰 모드에서 인트라넷 애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="39641-104">Running Intranet Applications in Full Trust</span></span>

<span data-ttu-id="39641-105">.NET Framework 버전 3.5 SP1(서비스 팩 1)부터 애플리케이션 및 해당 라이브러리 어셈블리를 네트워크 공유에서 완전 신뢰 어셈블리로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="39641-106"><xref:System.Security.SecurityZone.MyComputer> 영역 증거가 인트라넷의 공유에서 로드된 어셈블리에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="39641-106"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="39641-107">이 증거는 컴퓨터에 있는 어셈블리와 동일한 권한 부여 집합(일반적으로 완전 신뢰)을 해당 어셈블리에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-107">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="39641-108">이 기능은 호스트에서 실행되도록 설계된 애플리케이션 또는 ClickOnce 애플리케이션에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-108">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>

## <a name="rules-for-library-assemblies"></a><span data-ttu-id="39641-109">라이브러리 어셈블리에 대한 규칙</span><span class="sxs-lookup"><span data-stu-id="39641-109">Rules for Library Assemblies</span></span>

<span data-ttu-id="39641-110">다음 규칙은 네트워크 공유의 실행 파일에 의해 로드된 어셈블리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39641-110">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>

- <span data-ttu-id="39641-111">라이브러리 어셈블리는 실행 가능한 어셈블리와 동일한 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-111">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="39641-112">하위 폴더에 있거나 다른 경로에서 참조된 어셈블리에는 완전 신뢰 권한 부여 집합이 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-112">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>

- <span data-ttu-id="39641-113">실행 파일이 어셈블리를 지연 로드하는 경우 실행 파일을 시작하는 데 사용된 것과 동일한 경로를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-113">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="39641-114">예를 들어 \\\\*network-computer*\\*share* 라는 공유를 드라이브 문자에 매핑한 경우 이 경로에서 실행 파일을 실행하면 실행 파일에서 네트워크 경로를 사용하여 로드한 어셈블리에 완전 신뢰가 부여되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-114">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="39641-115"><xref:System.Security.SecurityZone.MyComputer> 영역에서 어셈블리를 지연 로드하려면 실행 파일이 드라이브 문자 경로를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-115">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>

## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="39641-116">이전 인트라넷 정책 복원</span><span class="sxs-lookup"><span data-stu-id="39641-116">Restoring the Former Intranet Policy</span></span>

<span data-ttu-id="39641-117">이전 버전의 .NET Framework에서는 공유 어셈블리에 <xref:System.Security.SecurityZone.Intranet> 영역 증거가 부여되었습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-117">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="39641-118">공유의 어셈블리에 완전 신뢰를 부여하려면 코드 액세스 보안 정책을 지정해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-118">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>

<span data-ttu-id="39641-119">이 새로운 동작은 인트라넷 어셈블리에 대한 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="39641-119">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="39641-120">컴퓨터의 모든 애플리케이션에 적용되는 레지스트리 키를 설정하여 <xref:System.Security.SecurityZone.Intranet> 증거를 제공하는 이전 동작으로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39641-120">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="39641-121">이 프로세스는 32비트 컴퓨터와 64비트 컴퓨터에서 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="39641-121">This process is different for 32-bit and 64-bit computers:</span></span>

- <span data-ttu-id="39641-122">32비트 컴퓨터에서는 시스템 레지스트리의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 키 아래에 하위 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39641-122">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="39641-123">키 이름 LegacyMyComputerZone, DWORD 값 1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>

- <span data-ttu-id="39641-124">64비트 컴퓨터에서는 시스템 레지스트리의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 키 아래에 하위 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39641-124">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="39641-125">키 이름 LegacyMyComputerZone, DWORD 값 1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39641-125">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="39641-126">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 키 아래에 동일한 하위 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39641-126">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>

## <a name="see-also"></a><span data-ttu-id="39641-127">참조</span><span class="sxs-lookup"><span data-stu-id="39641-127">See also</span></span>

- [<span data-ttu-id="39641-128">어셈블리를 사용한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="39641-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
