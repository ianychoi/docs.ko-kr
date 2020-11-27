---
title: '방법: 샌드박스에서 부분 신뢰 코드 실행'
description: .NET의 샌드박스에서 부분적으로 신뢰할 수 있는 코드를 실행 하는 방법을 알아봅니다. AppDomain 클래스는 관리 되는 응용 프로그램을 샌드 박싱 하는 효과적인 방법입니다.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: baa04a3c55728590b8aa502648a8ab42bf62f903
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288283"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="8e02b-104">방법: 샌드박스에서 부분 신뢰 코드 실행</span><span class="sxs-lookup"><span data-stu-id="8e02b-104">How to: Run Partially Trusted Code in a Sandbox</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8e02b-105">샌드박싱은 코드에 부여되는 액세스 권한을 제한하는 제한된 보안 환경에서 코드를 실행하는 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="8e02b-106">예를 들어 완전히 신뢰할 수는 없는 출처의 관리되는 라이브러리가 있으면 완전히 신뢰할 수 있는 것처럼 실행하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="8e02b-107">대신에 코드에 필요한 항목에 대한 권한을 제한하는 샌드박스에 코드를 배치해야 합니다(예: <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 권한).</span><span class="sxs-lookup"><span data-stu-id="8e02b-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="8e02b-108">샌드박싱을 사용하여 부분적으로 신뢰할 수 있는 환경에서 실행하고 배포할 코드를 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="8e02b-109"><xref:System.AppDomain>은 관리되는 애플리케이션에 대한 샌드박스를 제공하는 효과적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="8e02b-110">부분적으로 신뢰할 수 있는 코드에 사용되는 애플리케이션 도메인에는 해당 <xref:System.AppDomain> 내에서 실행할 때 사용할 수 있는 보호된 리소스를 정의하는 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="8e02b-111"><xref:System.AppDomain> 내부에서 실행되는 코드는 <xref:System.AppDomain>과 연결된 권한으로 바인딩되고 지정된 리소스에만 액세스하도록 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="8e02b-112"><xref:System.AppDomain>에는 완전히 신뢰된 코드로 로드될 어셈블리를 구별하는 데 사용되는 <xref:System.Security.Policy.StrongName> 배열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="8e02b-113">이를 통해 <xref:System.AppDomain> 작성자는 특정 도우미 어셈블리를 완전히 신뢰할 수 있도록 하는 새 샌드박싱 도메인을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="8e02b-114">어셈블리를 완전히 신뢰된 코드로 로드하는 다른 옵션은 어셈블리를 전역 어셈블리 캐시에 배치하는 것입니다. 하지만 이렇게 하면 어셈블리는 해당 컴퓨터에서 만들어진 모든 애플리케이션 도메인에서 완전히 신뢰된 코드로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="8e02b-115">강력한 이름 목록은 더 제한적인 결정을 제공하는 <xref:System.AppDomain>별 결정을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="8e02b-116"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 메서드 오버로드를 사용하여 샌드박스에서 실행되는 애플리케이션에 대한 권한 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="8e02b-117">이 오버로드를 사용하여 원하는 정확한 코드 액세스 보안 수준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="8e02b-118">이 오버로드를 사용하여 <xref:System.AppDomain>에 로드된 어셈블리는 지정된 권한 집합만 포함하거나 완전히 신뢰될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="8e02b-119">어셈블리가 전역 어셈블리 캐시에 있거나 `fullTrustAssemblies`(<xref:System.Security.Policy.StrongName>) 배열 매개 변수에 나열되면 어셈블리에 완전 신뢰가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="8e02b-120">완전히 신뢰된 코드로 알려진 어셈블리만 `fullTrustAssemblies` 목록에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="8e02b-121">오버로드에는 다음 서명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="8e02b-122"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 메서드 오버로드에 대한 매개 변수는 <xref:System.AppDomain> 이름, <xref:System.AppDomain>에 대한 증거, 샌드박스에 대한 애플리케이션 기준 위치를 나타내는 <xref:System.AppDomainSetup> 개체, 사용할 권한 집합, 완전히 신뢰할 수 있는 어셈블리의 강력한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="8e02b-123">보안상 이유로 `info` 매개 변수에 지정된 애플리케이션 기준 위치는 호스팅 애플리케이션에 사용되는 애플리케이션 기준 위치와 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="8e02b-124">`grantSet` 매개 변수에 대해 명시적으로 만든 권한 집합을 지정하거나 <xref:System.Security.SecurityManager.GetStandardSandbox%2A> 메서드에서 만들어진 표준 권한 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="8e02b-125">대부분 <xref:System.AppDomain> 로드와 달리 `securityInfo` 매개 변수에서 제공되는 <xref:System.AppDomain>에 대한 증거는 부분적으로 신뢰할 수 있는 어셈블리에 대한 권한 집합을 결정하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="8e02b-126">대신에 `grantSet` 매개 변수를 통해 독립적으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="8e02b-127">그러나 격리된 스토리지 범위를 결정하는 것과 같은 다른 용도에는 이 증거를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="8e02b-128">샌드박스에서 애플리케이션을 실행하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="8e02b-129">신뢰할 수 없는 애플리케이션에 부여할 권한 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="8e02b-130">부여할 수 있는 최소 권한은 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="8e02b-131">신뢰할 수 없는 코드에 대해 안전하다고 판단되는 추가적인 권한을 부여할 수도 있습니다(예: <xref:System.Security.Permissions.IsolatedStorageFilePermission>).</span><span class="sxs-lookup"><span data-stu-id="8e02b-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="8e02b-132">다음 코드에서는 <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> 권한만 포함된 새로운 권한 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="8e02b-133">또는 인터넷과 같은 기존 명명된 권한 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="8e02b-134"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> 메서드는 증거의 영역에 따라 `Internet` 권한 집합 또는 `LocalIntranet` 권한 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="8e02b-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>는 참조로 전달되는 일부 증거 개체에 대한 ID 권한을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="8e02b-136">신뢰할 수 없는 코드를 호출하는 호스팅 클래스(이 예제에서 이름은 `Sandboxer`)가 포함된 어셈블리에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="8e02b-137">어셈블리에 서명하는 데 사용된 <xref:System.Security.Policy.StrongName>을 <xref:System.AppDomain.CreateDomain%2A> 호출에 대한 `fullTrustAssemblies` 매개 변수의 <xref:System.Security.Policy.StrongName> 배열에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="8e02b-138">부분 신뢰 코드를 실행할 수 있게 하거나 부분 신뢰 애플리케이션에 서비스를 제공하려면 호스팅 클래스가 완전히 신뢰된 코드로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="8e02b-139">어셈블리의 <xref:System.Security.Policy.StrongName>을 읽는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="8e02b-140">mscorlib 및 System.dll과 같은 .NET Framework 어셈블리는 전역 어셈블리 캐시에서 완전 신뢰된 코드로 로드되므로 완전 신뢰 목록에 추가하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="8e02b-141"><xref:System.AppDomain.CreateDomain%2A> 메서드의 <xref:System.AppDomainSetup> 매개 변수를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="8e02b-142">이 매개 변수를 사용하여 새 <xref:System.AppDomain>의 설정을 대부분 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="8e02b-143"><xref:System.AppDomainSetup.ApplicationBase%2A> 속성은 중요한 설정이고 호스팅 애플리케이션의 <xref:System.AppDomain>에 대한 <xref:System.AppDomainSetup.ApplicationBase%2A> 속성과 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="8e02b-144"><xref:System.AppDomainSetup.ApplicationBase%2A> 설정이 같으면 부분 신뢰 애플리케이션이 호스팅 애플리케이션에 연결되어 부분 신뢰 애플리케이션이 정의한 예외를 완전 신뢰된 코드로 로드하므로 부분 신뢰 애플리케이션이 악용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="8e02b-145">이는 catch(예외)를 권장하지 않는 또 다른 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="8e02b-146">호스트의 애플리케이션 기준 위치를 샌드박싱된 애플리케이션의 애플리케이션 기준 위치와 다르게 설정하면 악용의 위험이 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="8e02b-147"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> 메서드 오버로드를 호출하여 지정한 매개 변수를 통해 애플리케이션 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="8e02b-148">이 메서드에 대한 서명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="8e02b-149">추가 정보:</span><span class="sxs-lookup"><span data-stu-id="8e02b-149">Additional information:</span></span>  
  
    - <span data-ttu-id="8e02b-150">이는 <xref:System.Security.PermissionSet>을 매개 변수로 사용하는 <xref:System.AppDomain.CreateDomain%2A> 메서드의 유일한 오버로드이므로 부분 신뢰 설정에서 애플리케이션을 로드하도록 하는 유일한 오버로드입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="8e02b-151">`evidence` 매개 변수는 권한 집합을 계산하는 데 사용되지 않으며, .NET Framework의 기타 기능을 통한 식별에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="8e02b-152">`info` 매개 변수의 <xref:System.AppDomainSetup.ApplicationBase%2A> 속성의 설정은 이 오버로드에 대해 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="8e02b-153">`fullTrustAssemblies` 매개 변수에는 <xref:System.Security.Policy.StrongName> 배열을 만드는 데 필요하지 않음을 의미하는 `params` 키워드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="8e02b-154">0, 1 또는 더 강력한 이름을 매개 변수로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="8e02b-155">애플리케이션 도메인을 만드는 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="8e02b-156">직접 만든 샌드박싱 <xref:System.AppDomain>에 코드를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="8e02b-157">이 작업은 두 가지 방법으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="8e02b-158">어셈블리에 대한 <xref:System.AppDomain.ExecuteAssembly%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="8e02b-159"><xref:System.Activator.CreateInstanceFrom%2A> 메서드를 사용하여 <xref:System.MarshalByRefObject>에서 파생된 클래스의 인스턴스를 새 <xref:System.AppDomain>에서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="8e02b-160">새 <xref:System.AppDomain> 인스턴스에 매개 변수를 전달하는 것이 더 간편하므로 두 번째 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="8e02b-161"><xref:System.Activator.CreateInstanceFrom%2A> 메서드는 다음 두 가지 중요 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="8e02b-162">어셈블리가 포함되지 않은 위치를 가리키는 코드베이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="8e02b-163">중요 클래스의 인스턴스를 만들 수 있는 완전 신뢰(<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>)의 경우 <xref:System.Security.CodeAccessPermission.Assert%2A> 아래에서 만들기를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="8e02b-164">이는 어셈블리에 투명도 표시가 없고 완전히 신뢰할 수 있는 상태로 로드 될 때마다 발생 합니다. 따라서이 함수를 사용 하 여 신뢰 하는 코드만 만들어야 하므로 새 응용 프로그램 도메인에서 완전히 신뢰할 수 있는 클래스의 인스턴스만 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="8e02b-165">새 도메인에서 클래스의 인스턴스를 만들려면 클래스를 확장 해야 합니다 <xref:System.MarshalByRefObject> .</span><span class="sxs-lookup"><span data-stu-id="8e02b-165">To create an instance of a class in a new domain, the class must extend the <xref:System.MarshalByRefObject> class.</span></span>
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="8e02b-166">새 도메인 인스턴스를 이 도메인의 참조로 래핑 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="8e02b-167">이 참조는 신뢰할 수 없는 코드를 실행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="8e02b-168">방금 만든 `Sandboxer` 클래스 인스턴스에서 `ExecuteUntrustedCode` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="8e02b-169">이 호출은 제한된 권한을 가진 샌드박싱된 애플리케이션 도메인에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="8e02b-170"><xref:System.Reflection>은 부분적으로 신뢰할 수 있는 어셈블리에서 메서드 핸들을 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="8e02b-171">핸들을 사용하여 최소 권한을 사용하는 안전한 방법으로 코드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="8e02b-172">이전 코드에서 <xref:System.Security.SecurityException>을 인쇄하기 전에 완전 신뢰 권한에 대한 <xref:System.Security.PermissionSet.Assert%2A>를 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="8e02b-173">완전 신뢰 어설션은 <xref:System.Security.SecurityException>에서 확장된 정보를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="8e02b-174"><xref:System.Security.PermissionSet.Assert%2A>를 사용하지 않으면 <xref:System.Security.SecurityException>의 <xref:System.Security.SecurityException.ToString%2A> 메서드는 스택에 부분적으로 신뢰할 수 있는 코드가 있는지 검색하고 반환된 정보를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="8e02b-175">부분 신뢰 코드가 해당 정보를 읽을 수 없으면 이로 인해 보안 문제가 발생할 수 있지만 <xref:System.Security.Permissions.UIPermission>을 부여하지 않음으로써 위험이 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="8e02b-176">완전 신뢰 어설션은 꼭 필요할 때만, 확실히 부분 신뢰 코드를 완전 신뢰로 높일 수 없을 때만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="8e02b-177">원칙적으로 같은 함수에서, 그리고 완전 신뢰에 대한 어설션을 호출한 후에는 신뢰할 수 없는 코드를 호출하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8e02b-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="8e02b-178">어설션 사용을 완료하면 항상 어설션을 되돌리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e02b-179">예제</span><span class="sxs-lookup"><span data-stu-id="8e02b-179">Example</span></span>  

 <span data-ttu-id="8e02b-180">다음 예제에서는 이전 섹션의 절차를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="8e02b-181">예제에서 Visual Studio 솔루션의 `Sandboxer` 프로젝트에는 `UntrustedClass` 클래스를 구현하는 `UntrustedCode` 프로젝트가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="8e02b-182">이 시나리오에서는 제공한 숫자가 피보나치 수인지를 나타내는 `true` 또는 `false`를 반환해야 하는 메서드가 포함된 라이브러리 어셈블리를 다운로드했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="8e02b-183">대신에 메서드는 컴퓨터에서 파일을 읽으려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="8e02b-184">다음 예제에서는 신뢰할 수 없는 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-184">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8e02b-185">다음 예제에서는 신뢰할 수 없는 코드를 실행하는 `Sandboxer` 애플리케이션 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e02b-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e02b-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e02b-186">See also</span></span>

- [<span data-ttu-id="8e02b-187">보안 코딩 지침</span><span class="sxs-lookup"><span data-stu-id="8e02b-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
