---
title: Membership and Role Provider
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: fa2a813c2dc1a891119e922c86f045e7f2df7125
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264714"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="45429-102">Membership and Role Provider</span><span class="sxs-lookup"><span data-stu-id="45429-102">Membership and Role Provider</span></span>

<span data-ttu-id="45429-103">멤버 자격 및 역할 공급자 샘플에서는 서비스에서 ASP.NET 멤버 자격 및 역할 공급자를 사용 하 여 클라이언트를 인증 하 고 권한을 부여 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45429-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="45429-104">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45429-105">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45429-106">이 샘플에서는 다음과 같은 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45429-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="45429-107">클라이언트에서 사용자 이름/암호 조합을 사용하여 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="45429-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="45429-108">서버는 ASP.NET 멤버 자격 공급자에 대해 클라이언트 자격 증명의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="45429-109">서버의 X.509 인증서를 사용하여 서버를 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="45429-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="45429-110">서버는 ASP.NET 역할 공급자를 사용 하 여 인증 된 클라이언트를 역할에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="45429-111">서버에서 `PrincipalPermissionAttribute`를 사용하여 서비스에 의해 노출되는 특정 메서드에 대한 액세스를 제어하는 방법</span><span class="sxs-lookup"><span data-stu-id="45429-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="45429-112">멤버 자격 및 역할 공급자는 SQL Server에서 지원하는 저장소를 사용하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="45429-113">연결 문자열과 다양한 옵션이 서비스 구성 파일에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="45429-114">멤버 자격 공급자의 이름은 `SqlMembershipProvider`로 지정되고 역할 공급자의 이름은 `SqlRoleProvider`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add
        name="SqlMembershipProvider"
        type="System.Web.Security.SqlMembershipProvider"
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="45429-115">서비스에서는 서비스와의 통신에 사용할 수 있는 단일 엔드포인트를 노출하며, 이 엔드포인트는 Web.config 구성 파일을 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="45429-116">엔드포인트는 하나의 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="45429-117">바인딩은 표준 `wsHttpBinding`을 사용하여 구성하며 기본값으로 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="45429-118">이 샘플에서는 사용자 이름 인증을 사용하도록 표준 `wsHttpBinding`을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="45429-119">동작에서는 서비스 인증에 서버 인증서를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="45429-120">서버 인증서는 `SubjectName` `findValue` 구성 요소의 특성과 동일한 값을 포함 해야 합니다 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="45429-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="45429-121">또한이 동작은 ASP.NET 멤버 자격 공급자에 의해 수행 되는 사용자 이름-암호 쌍의 인증과 두 공급자에 대해 정의 된 이름을 지정 하 여 ASP.NET 역할 공급자가 역할 매핑을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"
                              storeName ="My"
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="45429-122">샘플을 실행할 때 클라이언트는 세 개의 서로 다른 사용자 계정 Alice, Bob 및 Charlie 아래에서 다양한 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="45429-123">작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="45429-124">사용자 "Alice"로 수행한 4개의 호출은 모두 성공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="45429-125">사용자 "Bob"이 Divide 메서드를 호출하려고 할 때는 액세스 거부 오류가 발생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="45429-126">사용자 "Charlie"는 Multiply 메서드를 호출하려 할 때 액세스 거부 오류가 발생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="45429-127">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="45429-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45429-128">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="45429-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="45429-129">C # 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="45429-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="45429-130">[ASP.NET 애플리케이션 서비스 데이터베이스](https://go.microsoft.com/fwlink/?LinkId=94997)를 구성 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="45429-131">SQL Server Express Edition을 실행하는 경우 서버 이름은 .\SQLEXPRESS입니다.</span><span class="sxs-lookup"><span data-stu-id="45429-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="45429-132">이 서버는 ASP.NET 애플리케이션 서비스 데이터베이스 뿐만 아니라 Web.config 연결 문자열을 구성할 때 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="45429-133">ASP.NET worker 프로세스 계정에는이 단계에서 만든 데이터베이스에 대 한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="45429-134">이 작업에는 sqlcmd 유틸리티 또는 SQL Server Management Studio를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="45429-135">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행하려면 다음 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="45429-136">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="45429-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="45429-137">Makecert.exe가 있는 폴더가 경로에 포함되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="45429-138">Visual Studio에 대 한 개발자 명령 프롬프트 샘플 설치 폴더에서 Setup.bat를 실행 하 여 관리자 권한으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="45429-139">이 작업은 샘플 실행에 필요한 서비스 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="45429-140">\client\bin에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="45429-141">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="45429-142">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45429-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="45429-143">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="45429-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="45429-144">서비스 컴퓨터에 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45429-144">Create a directory on the service computer.</span></span> <span data-ttu-id="45429-145">IIS(인터넷 정보 서비스) 관리 도구를 사용하여 이 디렉터리에 servicemodelsamples라는 가상 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45429-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="45429-146">\inetpub\wwwroot\servicemodelsamples에서 서비스 컴퓨터의 가상 디렉터리로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="45429-147">\bin 하위 디렉터리에 파일을 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="45429-148">Setup.bat, GetComputerName.vbs 및 Cleanup.bat 파일도 서비스 컴퓨터에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="45429-149">클라이언트 컴퓨터에 클라이언트 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45429-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="45429-150">클라이언트 프로그램 파일을 클라이언트 컴퓨터의 클라이언트 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="45429-151">Setup.bat, Cleanup.bat 및 ImportServiceCert.bat 파일도 클라이언트로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="45429-152">서버에서 관리자 권한으로 Visual Studio에 대 한 개발자 명령 프롬프트를 열고를 실행 `setup.bat service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="45429-153">`setup.bat`인수를 사용 하 여를 실행 하면 컴퓨터의 정규화 된 `service` 도메인 이름으로 서비스 인증서가 생성 되 고 서비스 인증서가 이름이 .cer 인 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="45429-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="45429-154">`findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 컴퓨터의 정규화 된 도메인 이름과 같은 새 인증서 이름 (의 특성)을 반영 하도록 Web.config를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="45429-155">서비스 디렉터리에서 클라이언트 컴퓨터의 클라이언트 디렉터리로 Service.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="45429-156">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="45429-157">클라이언트에서 관리자 권한으로 Visual Studio에 대 한 개발자 명령 프롬프트를 열고 ImportServiceCert.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="45429-158">이 작업은 Service.cer 파일의 서비스 인증서를 CurrentUser - TrustedPeople 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="45429-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="45429-159">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="45429-160">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="45429-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="45429-161">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="45429-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="45429-162">샘플 실행을 완료한 후 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45429-163">다중 컴퓨터 구성에서 이 샘플을 실행할 경우에는 이 스크립트로 클라이언트의 서비스 인증서를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="45429-164">컴퓨터에서 인증서를 사용 하는 WCF (Windows Communication Foundation) 샘플을 실행 한 경우에는 CurrentUser-비트 사용자 저장소에 설치 된 서비스 인증서를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="45429-165">이를 수행하려면 `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 명령을 사용합니다(예: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="45429-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="45429-166">설치 배치 파일</span><span class="sxs-lookup"><span data-stu-id="45429-166">The Setup Batch File</span></span>  

 <span data-ttu-id="45429-167">이 샘플에 포함된 Setup.bat 배치 파일을 사용하면 서버 인증서 기반 보안이 필요한 자체 호스팅 애플리케이션을 실행하도록 관련 인증서가 있는 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="45429-168">다중 컴퓨터 구성이나 호스트되지 않는 환경에서 이 배치 파일을 사용하려면 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="45429-169">아래에는 적절한 구성에서 실행할 수 있도록 배치 파일을 수정하는 데 도움이 되는 여러 관련 단원의 간략한 개요가 소개되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="45429-170">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="45429-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="45429-171">Setup.bat 배치 파일에서 다음 행은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45429-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="45429-172">%SERVER_NAME% 변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="45429-173">이 변수를 변경하여 고유의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="45429-174">이 배치 파일에서의 기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="45429-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="45429-175">인증서는 LocalMachine 저장 위치에 있는 My(개인) 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="45429-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="45429-176">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치</span><span class="sxs-lookup"><span data-stu-id="45429-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="45429-177">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="45429-178">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45429-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="45429-179">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45429-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
