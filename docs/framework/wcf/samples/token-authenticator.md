---
description: '자세한 정보: 토큰 인증자'
title: Token Authenticator
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 086b2e8d8e9538710a315b79ad2d5be3969bb00e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668580"
---
# <a name="token-authenticator"></a><span data-ttu-id="142dd-103">Token Authenticator</span><span class="sxs-lookup"><span data-stu-id="142dd-103">Token Authenticator</span></span>

<span data-ttu-id="142dd-104">이 샘플에서는 사용자 지정 토큰 인증자를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-104">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="142dd-105">WCF (Windows Communication Foundation)의 토큰 인증자는 메시지에 사용 되는 토큰의 유효성을 검사 하 고, 자체 일관성이 있는지 확인 하 고, 토큰과 연결 된 id를 인증 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-105">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="142dd-106">사용자 지정 토큰 인증자는 다음과 같은 여러 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-106">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="142dd-107">토큰과 연관된 기본 인증 메커니즘을 재정의하려는 경우</span><span class="sxs-lookup"><span data-stu-id="142dd-107">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="142dd-108">사용자 지정 토큰을 빌드하고 있는 경우</span><span class="sxs-lookup"><span data-stu-id="142dd-108">When you are building a custom token.</span></span>

 <span data-ttu-id="142dd-109">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="142dd-110">클라이언트에서 사용자 이름/암호 쌍을 사용하여 인증하는 방법.</span><span class="sxs-lookup"><span data-stu-id="142dd-110">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="142dd-111">서버에서 사용자 지정 토큰 인증자를 사용하여 클라이언트 자격 증명의 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="142dd-111">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="142dd-112">WCF 서비스 코드가 사용자 지정 토큰 인증자와 연결 되는 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-112">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="142dd-113">서버의 X.509 인증서를 사용하여 서버를 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="142dd-113">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="142dd-114">또한이 샘플에서는 사용자 지정 토큰 인증 프로세스 후 WCF에서 호출자의 id에 액세스할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-114">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="142dd-115">서비스에서는 서비스와의 통신에 사용할 수 있는 단일 엔드포인트를 노출하며, 이 엔드포인트는 App.config 구성 파일을 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-115">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="142dd-116">엔드포인트는 하나의 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="142dd-117">바인딩은 `wsHttpBinding`의 기본 모드인 message로 설정된 보안 모드가 있는 표준 `wsHttpBinding`을 사용하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-117">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="142dd-118">이 샘플에서는 클라이언트 사용자 이름 인증을 사용하도록 표준 `wsHttpBinding`를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-118">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="142dd-119">또한 서비스는 `serviceCredentials` 동작을 사용하여 서비스 인증서를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-119">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="142dd-120">`securityCredentials` 동작을 통해 서비스 인증서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-120">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="142dd-121">서비스 인증서는 클라이언트에서 서비스를 인증하고 메시지 보호를 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-121">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="142dd-122">다음 구성에서는 뒤에 나오는 설치 지침에 설명된 대로 샘플 설치 중에 설치되는 localhost 인증서를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-122">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="142dd-123">클라이언트 엔드포인트 구성은 구성 이름, 서비스 엔드포인트의 절대 주소, 바인딩 및 계약으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="142dd-124">클라이언트 바인딩은 적절한 `Mode` 및 `clientCredentialType`를 사용하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-124">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 <span data-ttu-id="142dd-125">클라이언트 구현에서는 사용할 사용자 이름과 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-125">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="142dd-126">사용자 지정 토큰 인증자</span><span class="sxs-lookup"><span data-stu-id="142dd-126">Custom Token Authenticator</span></span>

 <span data-ttu-id="142dd-127">다음 단계에 따라 사용자 지정 토큰 인증자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-127">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="142dd-128">사용자 지정 토큰 인증자를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-128">Write a custom token authenticator.</span></span>

     <span data-ttu-id="142dd-129">샘플에서는 사용자 이름에 유효한 전자 메일 형식이 있는지 유효성을 검사하는 사용자 지정 토큰 인증자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-129">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="142dd-130"><xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>가 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-130">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="142dd-131">이 클래스에서 가장 중요한 메서드는 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>입니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-131">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="142dd-132">이 메서드에서 인증자는 사용자 이름 형식의 유효성을 검사하고 호스트 이름이 악의적인 도메인의 것이 아닌지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-132">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="142dd-133">두 조건을 모두 충족할 경우 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 인스턴스의 읽기 전용 컬렉션이 반환되며 이 컬렉션은 사용자 이름 토큰에 저장된 정보를 나타내는 클레임을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-133">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="142dd-134">사용자 지정 토큰 인증자에 의해 반환되는 권한 부여 정책을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-134">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="142dd-135">이 샘플에서는 생성자를 통해 전달된 클레임 및 ID 집합을 반환하는 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>라는 `UnconditionalPolicy`의 고유한 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-135">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="142dd-136">사용자 지정 보안 토큰 관리자를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-136">Write a custom security token manager.</span></span>

     <span data-ttu-id="142dd-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager>는 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 메서드를 통해 전달되는 특정 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 개체에 대한 `CreateSecurityTokenAuthenticator`를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="142dd-138">또한 보안 토큰 관리자는 토큰 공급자와 토큰 serializer를 만드는 데 사용되지만 이 샘플에서는 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-138">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="142dd-139">이 샘플에서 사용자 지정 보안 토큰 관리자는 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 클래스에서 상속되며 `CreateSecurityTokenAuthenticator` 메서드를 재정의하여 전달된 토큰 요구 사항에서 사용자 이름 인증자가 요청됨을 나타낼 때 사용자 지정 사용자 이름 토큰 인증자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="142dd-140">사용자 지정 서비스 자격 증명을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-140">Write a custom service credential.</span></span>

     <span data-ttu-id="142dd-141">서비스 자격 증명 클래스는 서비스에 대해 구성된 자격 증명을 나타내는 데 사용되며 토큰 인증자, 토큰 공급자 및 토큰 serializer를 가져오는 데 사용되는 보안 토큰 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-141">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="142dd-142">사용자 지정 서비스 자격 증명을 사용하도록 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-142">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="142dd-143">서비스에서 사용자 지정 서비스 자격 증명을 사용할 수 있도록 여기서는 이미 기본 서비스 자격 증명에 미리 구성된 서비스 인증서를 캡처한 후 기본 서비스 자격 증명 클래스를 삭제합니다. 그런 다음 미리 구성된 서비스 인증서를 사용하도록 새 서비스 자격 증명 인스턴스를 구성하고 이 서비스 자격 증명 인스턴스를 서비스 동작에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-143">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="142dd-144">호출자의 정보를 표시하려면 다음 코드와 같이 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-144">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="142dd-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A>에는 현재 호출자에 대한 클레임 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="142dd-146">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="142dd-147">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="142dd-148">설치 배치 파일</span><span class="sxs-lookup"><span data-stu-id="142dd-148">Setup Batch File</span></span>

 <span data-ttu-id="142dd-149">이 샘플에 포함된 Setup.bat 배치 파일을 사용하면 서버 인증서 기반 보안이 필요한 자체 호스팅 애플리케이션을 실행하도록 관련 인증서가 있는 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-149">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="142dd-150">다중 컴퓨터 구성이나 호스트되지 않는 환경에서 이 배치 파일을 사용하려면 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="142dd-151">다음 부분에는 적절한 구성에서 실행할 수 있게 배치 파일을 수정하는 데에 도움이 되는 여러 섹션의 간략한 개요가 소개되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="142dd-152">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="142dd-152">Creating the server certificate.</span></span>

     <span data-ttu-id="142dd-153">Setup.bat 배치 파일에서 다음 행은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="142dd-154">`%SERVER_NAME%`변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="142dd-155">이 변수를 변경하여 고유의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="142dd-156">이 배치 파일에서의 기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-156">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="142dd-157">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치</span><span class="sxs-lookup"><span data-stu-id="142dd-157">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="142dd-158">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="142dd-159">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="142dd-160">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="142dd-161">설치 배치 파일은 Windows SDK 명령 프롬프트에서 실행하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-161">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="142dd-162">MSSDK 환경 변수는 SDK가 설치되는 디렉터리를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="142dd-163">이 환경 변수는 Windows SDK 명령 프롬프트 내에서 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="142dd-164">샘플을 설치하고 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="142dd-164">To set up and build the sample</span></span>

1. <span data-ttu-id="142dd-165">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="142dd-166">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="142dd-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="142dd-167">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="142dd-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="142dd-168">관리자 권한으로 연 Visual Studio 2012 명령 프롬프트 내의 샘플 설치 폴더에서 Setup.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="142dd-169">이 작업은 샘플 실행에 필요한 모든 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="142dd-170">Setup.bat 배치 파일은 Visual Studio 2012 명령 프롬프트에서 실행 되도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="142dd-171">Visual Studio 2012 명령 프롬프트 내에서 설정 된 PATH 환경 변수는 Setup.bat 스크립트에 필요한 실행 파일을 포함 하는 디렉터리를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="142dd-172">service\bin에서 service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="142dd-173">\client\bin에서 client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-173">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="142dd-174">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="142dd-175">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="142dd-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="142dd-176">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="142dd-176">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="142dd-177">서비스 컴퓨터에 서비스 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-177">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="142dd-178">서비스 프로그램 파일을 서비스 컴퓨터의 서비스 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-178">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="142dd-179">Setup.bat 및 Cleanup.bat 파일도 서비스 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-179">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="142dd-180">컴퓨터의 정규화된 도메인 이름을 포함하는 주체 이름을 가진 서버 인증서가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-180">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="142dd-181">이 새로운 인증서 이름을 반영하도록 서비스 App.config 파일을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-181">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="142dd-182">`%SERVER_NAME%` 변수를 서비스가 실행되는 컴퓨터의 정규화된 호스트 이름으로 설정할 경우 Setup.bat를 사용하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-182">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="142dd-183">setup.bat 파일은 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-183">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="142dd-184">서버 인증서를 클라이언트의 CurrentUser-TrustedPeople 저장소에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-184">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="142dd-185">서버 인증서가 클라이언트의 신뢰할 수 있는 발급자에 의해 발급된 경우를 제외하고는 이 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-185">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="142dd-186">서비스 컴퓨터의 App.config 파일에서 기본 주소 값을 변경하여 localhost 대신 정규화된 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-186">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="142dd-187">서비스 컴퓨터의 명령 프롬프트에서 service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-187">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="142dd-188">언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-188">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="142dd-189">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-189">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="142dd-190">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-190">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="142dd-191">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="142dd-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="142dd-192">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="142dd-192">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="142dd-193">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="142dd-193">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
