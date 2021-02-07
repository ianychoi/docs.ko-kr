---
description: '자세히 알아보기: X. x.509 Certificate Validator'
title: X.509 Certificate Validator
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 3fead47cab4d639640f5af755717636ca2e8d01e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726236"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="be837-103">X.509 Certificate Validator</span><span class="sxs-lookup"><span data-stu-id="be837-103">X.509 Certificate Validator</span></span>

<span data-ttu-id="be837-104">이 샘플에서는 사용자 지정 X.509 인증서 유효성 검사기를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be837-104">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="be837-105">이 방법은 기본 제공되는 X.509 인증서 유효성 검사기 중에서 애플리케이션의 요구 사항에 적절한 것이 없는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-105">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="be837-106">이 샘플에서는 자체 발급된 인증서를 승인하는 사용자 지정 유효성 검사기가 있는 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be837-106">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="be837-107">그런 인증서를 사용하여 클라이언트가 서비스에 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-107">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="be837-108">참고: 자체 발급된 인증서는 누구나 작성할 수 있기 때문에 서비스에서 사용되는 사용자 지정 유효성 검사기는 ChainTrust X509CertificateValidationMode에서 제공되는 기본 동작보다 안전성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="be837-108">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="be837-109">이 경우 프로덕션 코드에서 이 유효성 검사 논리를 사용하기 전에 보안 상의 영향을 세심하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-109">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="be837-110">요약하면, 이 샘플에서는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be837-110">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="be837-111">X.509 인증서를 사용하여 클라이언트를 인증하는 방법.</span><span class="sxs-lookup"><span data-stu-id="be837-111">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="be837-112">서버에서 사용자 지정 X509CertificateValidator를 기준으로 클라이언트의 유효성을 검증하는 방법.</span><span class="sxs-lookup"><span data-stu-id="be837-112">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="be837-113">서버의 X.509 인증서를 사용하여 서버를 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="be837-113">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="be837-114">서비스는 App.config 구성 파일을 사용 하 여 정의 된 서비스와 통신 하기 위한 단일 끝점을 노출 합니다. 끝점은 주소, 바인딩 및 계약으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-114">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="be837-115">바인딩은 `wsHttpBinding` `WSSecurity` 및 클라이언트 인증서 인증을 기본적으로 사용 하는 표준으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-115">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="be837-116">서비스 동작에서는 클라이언트 X.509 인증서의 유효성을 검사하기 위한 사용자 지정 모드와 유효성 검사기 클래스의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-116">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="be837-117">동작에서는 serviceCertificate 요소를 사용하여 서버 인증서도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-117">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="be837-118">서버 인증서에는의와 동일한 값이 포함 되어야 합니다 `SubjectName` `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="be837-118">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="be837-119">클라이언트 엔드포인트 구성은 구성 이름, 서비스 엔드포인트의 절대 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-119">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="be837-120">클라이언트 바인딩에는 적절한 모드 및 메시지 `clientCredentialType`이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-120">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

<span data-ttu-id="be837-121">클라이언트 구현에서는 사용할 클라이언트 인증서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-121">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

<span data-ttu-id="be837-122">이 샘플에서는 사용자 지정 X509CertificateValidator를 사용하여 인증서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-122">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="be837-123">샘플에서는 <xref:System.IdentityModel.Selectors.X509CertificateValidator>로부터 파생된 CustomX509CertificateValidator를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-123">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="be837-124">자세한 내용은 <xref:System.IdentityModel.Selectors.X509CertificateValidator>에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="be837-124">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="be837-125">이 특정 사용자 지정 유효성 검사기 샘플에서는 다음 코드에 표시된 것과 같이 자체 발급된 모든 X.509 인증서를 승인하는 Validate 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-125">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="be837-126">서비스 코드에 유효성 검사기를 구현하고 나면 사용할 유효성 검사기 인스턴스에 대한 정보를 서비스 호스트에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-126">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="be837-127">이것은 다음 코드를 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-127">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="be837-128">또는 다음과 같이 구성에서도 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-128">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="be837-129">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-129">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="be837-130">클라이언트에서 모든 메서드를 성공적으로 호출할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-130">The client should successfully call all the methods.</span></span> <span data-ttu-id="be837-131">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="be837-131">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="be837-132">설치 배치 파일</span><span class="sxs-lookup"><span data-stu-id="be837-132">Setup Batch File</span></span>

<span data-ttu-id="be837-133">이 샘플에 포함된 Setup.bat 배치 파일을 사용하면 서버 인증서 기반 보안이 필요한 자체 호스팅 애플리케이션을 실행하도록 관련 인증서가 있는 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-133">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="be837-134">다중 컴퓨터 구성이나 호스트되지 않는 환경에서 이 배치 파일을 사용하려면 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-134">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="be837-135">다음 부분에는 적절한 구성으로 실행되게 수정할 수 있도록 배치 파일의 다양한 섹션에 대한 간략한 개요가 소개되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-135">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="be837-136">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="be837-136">Creating the server certificate:</span></span>

     <span data-ttu-id="be837-137">Setup.bat 배치 파일에서 다음 행은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be837-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="be837-138">%SERVER_NAME% 변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="be837-139">이 변수를 변경하여 고유의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-139">Change this variable to specify your own server name.</span></span> <span data-ttu-id="be837-140">기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="be837-140">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="be837-141">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치:</span><span class="sxs-lookup"><span data-stu-id="be837-141">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="be837-142">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-142">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="be837-143">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 시스템에서 암시적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-143">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="be837-144">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-144">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="be837-145">클라이언트 인증서 만들기:</span><span class="sxs-lookup"><span data-stu-id="be837-145">Creating the client certificate:</span></span>

     <span data-ttu-id="be837-146">Setup.bat 배치 파일에서 다음 줄은 사용할 클라이언트 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be837-146">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="be837-147">%USER_NAME% 변수는 클라이언트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-147">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="be837-148">이 값은 클라이언트 코드에서 찾는 이름이기 때문에 "test1"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-148">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="be837-149">%USER_NAME% 값을 변경한 경우에는 Client.cs 소스 파일에서 해당 값을 변경하고 클라이언트를 다시 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-149">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="be837-150">인증서는 CurrentUser 저장소 위치에 있는 My (Personal) 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-150">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="be837-151">서버의 신뢰할 수 있는 인증서 저장소에 클라이언트 인증서 설치:</span><span class="sxs-lookup"><span data-stu-id="be837-151">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="be837-152">Setup.bat 배치 파일에서 다음 줄은 신뢰할 수 있는 사용자 저장소로 클라이언트 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-152">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="be837-153">이 단계는 Makecert.exe에서 생성한 인증서를 서버 시스템에서 암시적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-153">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="be837-154">Microsoft에서 발급한 인증서와 같이 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 서버 인증서 저장소를 클라이언트 인증서로 채우는 이 단계는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-154">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="be837-155">샘플을 설치하고 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="be837-155">To set up and build the sample</span></span>

1. <span data-ttu-id="be837-156">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="be837-156">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="be837-157">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행하려면 다음 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-157">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="be837-158">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="be837-158">To run the sample on the same computer</span></span>

1. <span data-ttu-id="be837-159">관리자 권한으로 연 Visual Studio 2012 명령 프롬프트 내의 샘플 설치 폴더에서 Setup.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-159">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="be837-160">이 작업은 샘플 실행에 필요한 모든 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-160">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="be837-161">Setup.bat 배치 파일은 Visual Studio 2012 명령 프롬프트에서 실행 되도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-161">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="be837-162">Visual Studio 2012 명령 프롬프트 내에서 설정 된 PATH 환경 변수는 Setup.bat 스크립트에 필요한 실행 파일을 포함 하는 디렉터리를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="be837-162">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="be837-163">service\bin에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-163">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="be837-164">\client\bin에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-164">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="be837-165">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-165">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="be837-166">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be837-166">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="be837-167">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="be837-167">To run the sample across computers</span></span>

1. <span data-ttu-id="be837-168">서비스 컴퓨터에 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be837-168">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="be837-169">\service\bin에서 서비스 컴퓨터의 가상 디렉터리로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-169">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="be837-170">Setup.bat, Cleanup.bat, GetComputerName.vbs 및 ImportClientCert.bat 파일도 서비스 컴퓨터에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-170">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="be837-171">클라이언트 컴퓨터에 클라이언트 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be837-171">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="be837-172">클라이언트 프로그램 파일을 클라이언트 컴퓨터의 클라이언트 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-172">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="be837-173">Setup.bat, Cleanup.bat 및 ImportServiceCert.bat 파일도 클라이언트로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-173">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="be837-174">서버에서 `setup.bat service` 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-174">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="be837-175">`setup.bat`인수를 사용 하 여를 실행 하면 컴퓨터의 정규화 된 `service` 도메인 이름으로 서비스 인증서가 생성 되 고 서비스 인증서가 이름이 .cer 인 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="be837-175">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="be837-176">`findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 컴퓨터의 정규화 된 도메인 이름과 같은 새 인증서 이름 (의 특성)을 반영 하도록 Service.exe.config를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-176">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="be837-177">또한 요소의 컴퓨터 이름을 \<service> / \<baseAddresses> localhost에서 서비스 컴퓨터의 정규화 된 이름으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-177">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="be837-178">서비스 디렉터리에서 클라이언트 컴퓨터의 클라이언트 디렉터리로 Service.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-178">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="be837-179">클라이언트에서 `setup.bat client` 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-179">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="be837-180">`setup.bat` 인수를 사용하여 `client`를 실행하면 client.com이라는 클라이언트 인증서가 생성되어 Client.cer이라는 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="be837-180">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="be837-181">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-181">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="be837-182">이렇게 하려면 localhost를 서버의 정규화된 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="be837-182">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="be837-183">클라이언트 디렉터리에서 서버의 서비스 디렉터리로 Client.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-183">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="be837-184">클라이언트에서 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트에서 ImportServiceCert.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-184">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="be837-185">이 작업은 Service.cer 파일의 서비스 인증서를 CurrentUser - TrustedPeople 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="be837-185">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="be837-186">서버에서 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트에서 ImportClientCert.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-186">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="be837-187">이 작업은 Client.cer 파일의 클라이언트 인증서를 LocalMachine - TrustedPeople 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="be837-187">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="be837-188">서버 컴퓨터의 명령 프롬프트 창에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-188">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="be837-189">클라이언트 컴퓨터의 명령 프롬프트 창에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-189">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="be837-190">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be837-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="be837-191">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="be837-191">To clean up after the sample</span></span>

1. <span data-ttu-id="be837-192">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="be837-193">그러면 인증서 저장소에서 서버 및 클라이언트 인증서가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="be837-193">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="be837-194">다중 컴퓨터 구성에서 이 샘플을 실행할 경우에는 이 스크립트로 클라이언트의 서비스 인증서를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be837-194">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="be837-195">컴퓨터에서 인증서를 사용 하는 WCF (Windows Communication Foundation) 샘플을 실행 한 경우에는 CurrentUser-비트 사용자 저장소에 설치 된 서비스 인증서를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be837-195">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="be837-196">이를 수행하려면 `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 명령을 사용합니다(예: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="be837-196">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
