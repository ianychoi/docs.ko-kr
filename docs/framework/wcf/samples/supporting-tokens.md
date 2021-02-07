---
description: '자세한 정보: 토큰 지원'
title: Supporting Tokens
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 455c69ce1ae03bd612f78a7977b013955bd81868
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668736"
---
# <a name="supporting-tokens"></a><span data-ttu-id="d4a49-103">Supporting Tokens</span><span class="sxs-lookup"><span data-stu-id="d4a49-103">Supporting Tokens</span></span>

<span data-ttu-id="d4a49-104">Supporting Tokens 샘플에서는 WS-Security를 사용하는 메시지에 토큰을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-104">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="d4a49-105">이 예제에서는 사용자 이름 보안 토큰에 X.509 이진 보안 토큰을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-105">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="d4a49-106">이 토큰은 WS-Security 메시지 헤더에 포함되어 클라이언트에서 서비스로 전달되며, 메시지의 일부는 X.509 보안 토큰과 연결된 프라이빗 키로 서명되어 X.509 인증서를 소유했음을 수신자에게 증명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-106">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="d4a49-107">이는 발신자를 인증하거나 권한 부여하기 위해 메시지에 여러 개의 클레임이 연결되어야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-107">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="d4a49-108">이 서비스는 요청-회신 통신 패턴을 정의하는 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d4a49-109">데모</span><span class="sxs-lookup"><span data-stu-id="d4a49-109">Demonstrates</span></span>

 <span data-ttu-id="d4a49-110">이 샘플에서는 다음 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-110">The sample demonstrates:</span></span>

- <span data-ttu-id="d4a49-111">클라이언트가 추가 보안 토큰을 서비스에 전달하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4a49-111">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="d4a49-112">서버가 추가 보안 토큰과 연결된 클레임에 액세스하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4a49-112">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="d4a49-113">서버의 X.509 인증서를 사용하여 메시지 암호화 및 서명에 사용되는 대칭 키를 보호하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4a49-113">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="d4a49-114">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="d4a49-115">사용자 이름 토큰 및 지원 X.509 보안 토큰을 사용하는 클라이언트 인증</span><span class="sxs-lookup"><span data-stu-id="d4a49-115">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>

 <span data-ttu-id="d4a49-116">서비스는 `BindingHelper` 및 `EchoServiceHost` 클래스를 사용하여 프로그래밍 방식으로 만들어진 단일 엔드포인트를 통신을 위해 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-116">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="d4a49-117">엔드포인트는 하나의 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="d4a49-118">바인딩은 `SymmetricSecurityBindingElement` 및 `HttpTransportBindingElement`를 사용하여 사용자 지정 바인딩으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="d4a49-119">이 샘플에서는 서비스의 X.509 인증서를 사용하여 전송 도중 대칭 키를 보호하고 WS-Security 메시지 헤더에서 `SymmetricSecurityBindingElement`을 지원 `UserNameToken`과 함께 전달하도록 `X509SecurityToken`를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-119">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="d4a49-120">대칭 키는 메시지 본문 및 사용자 이름 보안 토큰을 암호화할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-120">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="d4a49-121">WS-Security 메시지 헤더에서 지원 토큰은 추가 이진 보안 토큰으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-121">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="d4a49-122">지원 토큰의 신뢰성은 메시지의 서명 부분에서 지원 X.509 보안 토큰과 연결된 프라이빗 키를 사용하여 입증합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-122">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 <span data-ttu-id="d4a49-123">동작은 클라이언트 인증에 사용되는 서비스 자격 증명과 서비스 X.509 인증서에 대한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-123">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="d4a49-124">이 샘플에서는 `CN=localhost`를 서비스 X.509 인증서의 주체 이름으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-124">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 <span data-ttu-id="d4a49-125">서비스 코드:</span><span class="sxs-lookup"><span data-stu-id="d4a49-125">Service code:</span></span>

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 <span data-ttu-id="d4a49-126">클라이언트 엔드포인트는 서비스 엔드포인트와 동일한 방식으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-126">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="d4a49-127">클라이언트는 동일한 `BindingHelper` 클래스를 사용하여 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-127">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="d4a49-128">설정의 나머지 부분은 `Client` 클래스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-128">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="d4a49-129">클라이언트는 사용자 이름 보안 토큰, 지원 X.509 보안 토큰 및 서비스 X.509 인증서에 대한 정보를 클라이언트 엔드포인트 동작 컬렉션에 대한 설치 코드에서 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-129">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a><span data-ttu-id="d4a49-130">호출자의 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d4a49-130">Displaying Callers' Information</span></span>

 <span data-ttu-id="d4a49-131">호출자의 정보를 표시하려면 다음 코드와 같이 `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-131">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="d4a49-132">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`는 현재 호출자와 연관된 권한 부여 클레임을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-132">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="d4a49-133">이러한 클레임은 메시지에 수신 되는 모든 토큰에 대해 WCF (Windows Communication Foundation)에 의해 자동으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-133">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a><span data-ttu-id="d4a49-134">샘플 실행</span><span class="sxs-lookup"><span data-stu-id="d4a49-134">Running the Sample</span></span>

 <span data-ttu-id="d4a49-135">샘플을 실행하면 클라이언트는 먼저 사용자 이름 토큰의 사용자 이름과 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-135">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="d4a49-136">서비스의 WCF는 사용자 이름 토큰에 제공 된 값을 시스템에서 제공 하는 id에 매핑하기 때문에 시스템 계정에 올바른 값을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-136">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="d4a49-137">그런 다음 클라이언트는 서비스로부터의 응답을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-137">After that, the client displays the response from the service.</span></span> <span data-ttu-id="d4a49-138">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-138">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="d4a49-139">설치 배치 파일</span><span class="sxs-lookup"><span data-stu-id="d4a49-139">Setup Batch File</span></span>

 <span data-ttu-id="d4a49-140">이 샘플에 포함된 Setup.bat 배치 파일을 사용하면 서버 인증서 기반 보안이 필요한 IIS(인터넷 정보 서비스) 호스팅 애플리케이션을 실행하도록 관련 인증서가 있는 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-140">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="d4a49-141">다중 컴퓨터 구성이나 호스팅되지 않는 환경에서 이 배치 파일을 사용하려면 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-141">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="d4a49-142">다음 부분에는 적절한 구성에서 실행할 수 있게 배치 파일을 수정하는 데에 도움이 되는 여러 섹션의 간략한 개요가 소개되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-142">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="d4a49-143">클라이언트 인증서 만들기.</span><span class="sxs-lookup"><span data-stu-id="d4a49-143">Creating the Client Certificate</span></span>

 <span data-ttu-id="d4a49-144">Setup.bat 배치 파일에서 다음 줄은 사용할 클라이언트 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-144">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="d4a49-145">`%CLIENT_NAME%` 변수는 클라이언트 인증서의 주체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-145">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="d4a49-146">이 샘플에서는 "client.com"을 주체 이름으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-146">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="d4a49-147">인증서는 `CurrentUser` 저장 위치에 있는 My(개인) 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-147">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="d4a49-148">서버의 신뢰할 수 있는 저장소에 클라이언트 인증서 설치</span><span class="sxs-lookup"><span data-stu-id="d4a49-148">Installing the Client Certificate into the Server's Trusted Store</span></span>

 <span data-ttu-id="d4a49-149">Setup.bat 배치 파일에서 다음 행은 클라이언트 인증서를 서버의 신뢰할 수 있는 사용자 저장소로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-149">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="d4a49-150">이 단계는 Makecert.exe에서 생성한 인증서를 서버 시스템에서 명시적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-150">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="d4a49-151">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-151">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="d4a49-152">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="d4a49-152">Creating the Server Certificate</span></span>

 <span data-ttu-id="d4a49-153">Setup.bat 배치 파일에서 다음 행은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="d4a49-154">`%SERVER_NAME%`변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="d4a49-155">이 변수를 변경하여 고유의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="d4a49-156">이 배치 파일에서의 기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-156">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="d4a49-157">인증서는 LocalMachine 저장 위치에 있는 My(개인) 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-157">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="d4a49-158">IIS에서 호스트되는 서비스의 경우 인증서는 LocalMachine 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-158">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="d4a49-159">자체 호스팅 서비스의 경우 LocalMachine 문자열을 CurrentUser로 대체하여 CurrentUser 저장소 위치에 서버 인증서를 저장하도록 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-159">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="d4a49-160">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치.</span><span class="sxs-lookup"><span data-stu-id="d4a49-160">Installing Server Certificate into Client's Trusted Certificate Store</span></span>

 <span data-ttu-id="d4a49-161">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-161">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="d4a49-162">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-162">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="d4a49-163">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-163">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="d4a49-164">인증서의 프라이빗 키 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="d4a49-164">Enabling Access to the Certificate's Private Key</span></span>

 <span data-ttu-id="d4a49-165">IIS에서 호스트되는 서비스에서 인증서 프라이빗 키에 액세스할 수 있게 하려면 IIS에서 호스트되는 프로세스가 실행 중인 사용자 계정에 프라이빗 키에 대한 적절한 사용 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-165">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="d4a49-166">Setup.bat 스크립트에서 마지막 단계를 통해 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-166">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4a49-167">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d4a49-167">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d4a49-168">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-168">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d4a49-169">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d4a49-169">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="d4a49-170">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행하려면 다음 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-170">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="d4a49-171">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d4a49-171">To run the sample on the same machine</span></span>

1. <span data-ttu-id="d4a49-172">관리자 권한으로 실행 되는 Visual Studio 2012 명령 프롬프트 내의 샘플 설치 폴더에서 Setup.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-172">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="d4a49-173">이 작업은 샘플 실행에 필요한 모든 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-173">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d4a49-174">Setup.bat 배치 파일은 Visual Studio 2012 명령 프롬프트에서 실행 되도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-174">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="d4a49-175">Visual Studio 2012 명령 프롬프트 내에서 설정 된 PATH 환경 변수는 Setup.bat 스크립트에 필요한 실행 파일을 포함 하는 디렉터리를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-175">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="d4a49-176">샘플 사용을 마쳤으면 Cleanup.bat를 실행하여 인증서를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-176">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="d4a49-177">다른 보안 샘플에도 동일한 인증서가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-177">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="d4a49-178">\client\bin에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="d4a49-179">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-179">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="d4a49-180">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4a49-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="d4a49-181">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d4a49-181">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="d4a49-182">서비스 컴퓨터에 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-182">Create a directory on the service machine.</span></span> <span data-ttu-id="d4a49-183">IIS(인터넷 정보 서비스) 관리 도구를 사용하여 이 디렉터리에 servicemodelsamples라는 가상 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-183">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="d4a49-184">\inetpub\wwwroot\servicemodelsamples에서 서비스 컴퓨터의 가상 디렉터리로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-184">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="d4a49-185">\bin 하위 디렉터리에 파일을 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-185">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="d4a49-186">또한 Setup.bat, Cleanup.bat 및 ImportClientCert.bat 파일을 서비스 시스템에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-186">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="d4a49-187">클라이언트 컴퓨터에 클라이언트 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-187">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="d4a49-188">클라이언트 프로그램 파일을 클라이언트 컴퓨터의 클라이언트 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-188">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="d4a49-189">Setup.bat, Cleanup.bat 및 ImportServiceCert.bat 파일도 클라이언트로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-189">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="d4a49-190">서버에서 `setup.bat service` 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-190">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="d4a49-191">`setup.bat`인수를 사용 하 여를 실행 하면 컴퓨터의 정규화 된 `service` 도메인 이름으로 서비스 인증서가 생성 되 고 서비스 인증서가 이름이 .cer 인 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-191">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="d4a49-192">`findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) 컴퓨터의 정규화 된 도메인 이름과 같은 새 인증서 이름 (의 특성)을 반영 하도록 Web.config를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-192">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="d4a49-193">서비스 디렉터리에서 클라이언트 컴퓨터의 클라이언트 디렉터리로 Service.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-193">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="d4a49-194">클라이언트에서 `setup.bat client` 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-194">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="d4a49-195">`setup.bat` 인수를 사용하여 `client`를 실행하면 client.com이라는 클라이언트 인증서가 생성되어 Client.cer이라는 파일로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-195">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="d4a49-196">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-196">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="d4a49-197">이렇게 하려면 localhost를 서버의 정규화된 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-197">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="d4a49-198">클라이언트 디렉터리에서 서버의 서비스 디렉터리로 Client.cer 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-198">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="d4a49-199">클라이언트에서 ImportServiceCert.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-199">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="d4a49-200">이 작업은 Service.cer 파일의 서비스 인증서를 CurrentUser - TrustedPeople 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-200">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="d4a49-201">서버에서 ImportClientCert.bat를 실행하여 Client.cer 파일에서 LocalMachine - TrustedPeople 저장소로 클라이언트 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-201">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="d4a49-202">클라이언트 컴퓨터의 명령 프롬프트 창에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-202">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="d4a49-203">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4a49-203">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d4a49-204">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="d4a49-204">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d4a49-205">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-205">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4a49-206">다중 컴퓨터 구성에서 이 샘플을 실행할 경우에는 이 스크립트로 서비스 인증서를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-206">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="d4a49-207">컴퓨터에서 인증서를 사용 하는 WCF 샘플을 실행 한 경우에는 CurrentUser-비트 사용자 저장소에 설치 된 서비스 인증서를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4a49-207">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d4a49-208">이를 수행하려면 `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 명령을 사용합니다(예: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="d4a49-208">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
