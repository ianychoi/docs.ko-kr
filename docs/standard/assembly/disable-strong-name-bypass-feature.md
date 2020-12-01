---
title: '방법: 강력한 이름 건너뛰기 기능 사용 안 함'
description: 강력한 이름 바이패스는 .NET에서 완전히 신뢰할 수 있는 도메인의 서명 유효성 검사를 건너뜁니다. 단일 애플리케이션 또는 모든 애플리케이션에 대해 이 기능을 재정의할 수 있습니다.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 2846efbbd76cf677a42a7031e53661d302c6c964
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687465"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="e5b14-104">방법: 강력한 이름 건너뛰기 기능 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e5b14-104">How to: Disable the strong-name bypass feature</span></span>

<span data-ttu-id="e5b14-105">.NET Framework 버전 3.5 SP1(서비스 팩 1)부터는 어셈블리가 완전 신뢰 <xref:System.AppDomain> 개체(예: `MyComputer` 영역의 기본 <xref:System.AppDomain>)에 로드될 때 강력한 이름 시그니처의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="e5b14-106">이를 강력한 이름 건너뛰기 기능이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="e5b14-107">완전 신뢰 환경에서는 <xref:System.Security.Permissions.StrongNameIdentityPermission>에 대한 요청이 해당 시그니처와 관계없이 서명된 완전 신뢰 어셈블리에 대해 항상 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="e5b14-108">유일한 제한 사항은 어셈블리 영역이 완전히 신뢰되므로 어셈블리도 완전히 신뢰할 수 있어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="e5b14-109">강력한 이름은 이러한 조건에서 결정적인 요소가 아니므로 유효성을 검사할 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="e5b14-110">강력한 이름 시그니처의 유효성 검사를 건너뛰면 상당한 성능 개선 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="e5b14-111">건너뛰기 기능은 지연 서명되지 않았으며 <xref:System.AppDomainSetup.ApplicationBase%2A> 속성으로 지정된 디렉터리에서 완전 신뢰 <xref:System.AppDomain>에 로드된 모든 완전 신뢰 어셈블리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="e5b14-112">레지스트리 키 값을 설정하여 컴퓨터의 모든 애플리케이션에 대해 건너뛰기 기능을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="e5b14-113">애플리케이션 구성 파일을 사용하여 단일 애플리케이션에 대한 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="e5b14-114">레지스트리 키를 통해 사용하지 않도록 설정된 경우 단일 애플리케이션에 대해 건너뛰기 기능을 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="e5b14-115">건너뛰기 기능을 재정의하면 정확성에 대해서만 강력한 이름의 유효성이 검사되고 <xref:System.Security.Permissions.StrongNameIdentityPermission>에 대해서는 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="e5b14-116">특정 강력한 이름을 확인하려면 해당 확인을 별도로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e5b14-117">강력한 이름 유효성 검사를 강제 적용하는 기능은 다음 절차에 설명된 대로 레지스트리 키에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="e5b14-118">애플리케이션이 해당 레지스트리 키에 액세스할 수 있는 ACL(액세스 제어 목록) 권한이 없는 계정으로 실행되는 경우에는 설정이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="e5b14-119">모든 어셈블리에서 읽을 수 있도록 이 키에 대해 ACL 권한이 구성되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="e5b14-120">모든 애플리케이션에 대해 강력한 이름 건너뛰기 기능 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e5b14-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="e5b14-121">32비트 컴퓨터에서는 시스템 레지스트리의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 키 아래에 값이 0인 `AllowStrongNameBypass`라는 DWORD 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="e5b14-122">64비트 컴퓨터에서는 시스템 레지스트리의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 및 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 아래에 값이 0인 `AllowStrongNameBypass`라는 DWORD 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="e5b14-123">단일 애플리케이션에 대해 강력한 이름 건너뛰기 기능 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="e5b14-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="e5b14-124">애플리케이션 구성 파일을 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="e5b14-125">이 파일에 대한 자세한 내용은 [앱 구성](../../framework/configure-apps/index.md)에서 애플리케이션 구성 파일 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5b14-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="e5b14-126">다음 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="e5b14-127">구성 파일 설정을 제거하거나 특성을 `true`로 설정하여 애플리케이션에 대한 건너뛰기 기능을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5b14-128">컴퓨터에서 건너뛰기 기능이 사용되는 경우에만 애플리케이션에 대해 강력한 이름 유효성 검사를 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="e5b14-129">컴퓨터에서 건너뛰기 기능이 해제된 경우 모든 애플리케이션에 대해 강력한 이름 유효성이 검사되며, 단일 애플리케이션에 대해 유효성 검사를 건너뛸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b14-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b14-130">참조</span><span class="sxs-lookup"><span data-stu-id="e5b14-130">See also</span></span>

- [<span data-ttu-id="e5b14-131">Sn.exe(강력한 이름 도구)</span><span class="sxs-lookup"><span data-stu-id="e5b14-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="e5b14-132">\<bypassTrustedAppStrongNames> 요소</span><span class="sxs-lookup"><span data-stu-id="e5b14-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="e5b14-133">강력한 이름의 어셈블리 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="e5b14-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
