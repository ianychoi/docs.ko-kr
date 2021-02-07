---
description: '자세한 정보: SAML 토큰 공급자'
title: SAML Token Provider
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: f65d34732c14bc1d3a442b9aacda1621995c975e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703694"
---
# <a name="saml-token-provider"></a><span data-ttu-id="22111-103">SAML Token Provider</span><span class="sxs-lookup"><span data-stu-id="22111-103">SAML Token Provider</span></span>

<span data-ttu-id="22111-104">이 샘플에서는 사용자 지정 클라이언트 SAML 토큰 공급자를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22111-104">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="22111-105">WCF (Windows Communication Foundation)의 토큰 공급자는 보안 인프라에 자격 증명을 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-105">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="22111-106">일반적으로 토큰 공급자는 대상을 검사하고 적절한 자격 증명을 발급하여 보안 인프라에서 메시지의 보안을 유지할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="22111-107">WCF는 기본 자격 증명 관리자 토큰 공급자와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-107">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="22111-108">WCF는 또한 CardSpace 토큰 공급자와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-108">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="22111-109">사용자 지정 토큰 공급자는 다음과 같은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-109">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="22111-110">이러한 토큰 공급자가 작동되지 않는 자격 증명 저장소가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="22111-110">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="22111-111">WCF 클라이언트 프레임 워크에서 자격 증명을 사용 하는 경우 사용자가 세부 정보를 제공 하는 시점에서 자격 증명을 변환 하는 사용자 지정 메커니즘을 제공 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="22111-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="22111-112">사용자 지정 토큰을 빌드하고 있는 경우</span><span class="sxs-lookup"><span data-stu-id="22111-112">If you are building a custom token.</span></span>

 <span data-ttu-id="22111-113">이 샘플에서는 WCF 클라이언트 프레임 워크 외부에서 가져온 SAML 토큰을 사용 하도록 허용 하는 사용자 지정 토큰 공급자를 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22111-113">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="22111-114">즉, 이 샘플에서는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22111-114">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="22111-115">사용자 지정 토큰 공급자로 클라이언트를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="22111-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="22111-116">사용자 지정 클라이언트 자격 증명으로 SAML 토큰을 전달하는 방법</span><span class="sxs-lookup"><span data-stu-id="22111-116">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="22111-117">WCF 클라이언트 프레임 워크에 SAML 토큰을 제공 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="22111-117">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="22111-118">서버의 X.509 인증서를 사용하여 클라이언트에서 서버를 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="22111-118">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="22111-119">서비스는 App.config 구성 파일을 사용 하 여 정의 된 서비스와 통신 하기 위한 두 개의 끝점을 노출 합니다. 각 끝점은 주소, 바인딩 및 계약으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-119">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="22111-120">바인딩은 메시지 보안을 사용하는 표준 `wsFederationHttpBinding`으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-120">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="22111-121">한 엔드포인트에서는 클라이언트가 대칭 증명 키를 사용하는 SAML 토큰으로 인증할 것으로 예상하고, 다른 엔드포인트에서는 클라이언트가 비대칭 증명 키를 사용하는 SAML 토큰으로 인증할 것으로 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-121">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="22111-122">또한 서비스는 `serviceCredentials` 동작을 사용하여 서비스 인증서를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-122">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="22111-123">`serviceCredentials` 동작을 통해 서비스 인증서를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-123">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="22111-124">서비스 인증서는 클라이언트에서 서비스를 인증하고 메시지 보호를 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-124">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="22111-125">다음 구성에서는 이 항목의 끝에 나오는 설치 지침에 설명된 대로 샘플 설치 중에 설치되는 "localhost" 인증서를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-125">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="22111-126">`serviceCredentials` 동작을 사용하면 SAML 토큰에 서명하도록 신뢰되는 인증서를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-126">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="22111-127">다음 구성에서는 샘플 설치 중에 설치되는 'Alice' 인증서를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-127">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="22111-128">다음 단계에서는 사용자 지정 SAML 토큰 공급자를 개발 하 고 WCF: 보안 프레임 워크와 통합 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22111-128">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="22111-129">사용자 지정 SAML 토큰 공급자를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="22111-129">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="22111-130">이 샘플에서는 생성 시에 제공되는 SAML 어설션을 기반으로 보안 토큰을 반환하는 사용자 지정 SAML 토큰 공급자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-130">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="22111-131">이 작업을 수행하려면 사용자 지정 토큰 공급자가 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 클래스에서 파생되고 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 메서드를 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-131">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="22111-132">이 메서드는 새 `SecurityToken`을 만들고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-132">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="22111-133">사용자 지정 보안 토큰 관리자를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="22111-133">Write custom security token manager.</span></span>

     <span data-ttu-id="22111-134"><xref:System.IdentityModel.Selectors.SecurityTokenManager> 클래스는 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 메서드에서 전달되는 특정 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>에 대한 `CreateSecurityTokenProvider`를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-134">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="22111-135">또한 보안 토큰 관리자는 토큰 인증자와 토큰 serializer를 만드는 데 사용되지만 이 샘플에서는 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-135">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="22111-136">이 샘플에서 사용자 지정 보안 토큰 관리자는 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 클래스에서 상속되며 `CreateSecurityTokenProvider` 메서드를 재정의하여 전달된 토큰 요구 사항에서 SAML 토큰이 요청됨을 나타낼 때 사용자 지정 SAML 토큰 공급자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-136">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="22111-137">클라이언트 자격 증명 클래스(3단계 참조)에서 어설션을 지정하지 않은 경우에는 보안 토큰 관리자에서 적절한 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22111-137">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="22111-138">사용자 지정 클라이언트 자격 증명을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="22111-138">Write a custom client credential.</span></span>

     <span data-ttu-id="22111-139">클라이언트 자격 증명 클래스는 클라이언트 프록시에 대해 구성된 자격 증명을 나타내는 데 사용되며 토큰 인증자, 토큰 공급자 및 토큰 serializer를 가져오는 데 사용되는 보안 토큰 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22111-139">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="22111-140">사용자 지정 클라이언트 자격 증명을 사용하도록 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-140">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="22111-141">이 샘플에서는 기본 클라이언트 자격 증명 클래스를 삭제하고 새 클라이언트 자격 증명 클래스를 제공하여 클라이언트에서 사용자 지정 클라이언트 자격 증명을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-141">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="22111-142">서비스에는 호출자와 관련된 요청이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-142">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="22111-143">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-143">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="22111-144">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="22111-144">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="22111-145">설치 배치 파일</span><span class="sxs-lookup"><span data-stu-id="22111-145">Setup Batch File</span></span>

 <span data-ttu-id="22111-146">이 샘플에 포함된 Setup.bat 배치 파일을 사용하면 관련 인증서로 서버를 구성하여 서버 인증서 기반 보안이 필요한 자체 호스팅 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-146">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="22111-147">다중 컴퓨터 구성이나 호스트되지 않는 환경에서 이 배치 파일을 사용하려면 배치 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-147">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="22111-148">아래에는 적절한 구성에서 실행할 수 있도록 배치 파일을 수정하는 데 도움이 되는 여러 관련 단원의 간략한 개요가 소개되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-148">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="22111-149">서버 인증서 만들기</span><span class="sxs-lookup"><span data-stu-id="22111-149">Creating the server certificate:</span></span>

     <span data-ttu-id="22111-150">Setup.bat 배치 파일에서 다음 행은 사용할 서버 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22111-150">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="22111-151">`%SERVER_NAME%`변수는 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-151">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="22111-152">이 변수를 변경하여 고유의 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-152">Change this variable to specify your own server name.</span></span> <span data-ttu-id="22111-153">이 배치 파일의 기본값은 localhost입니다.</span><span class="sxs-lookup"><span data-stu-id="22111-153">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="22111-154">인증서는 LocalMachine 저장 위치에 있는 My(개인) 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-154">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="22111-155">클라이언트의 신뢰할 수 있는 인증서 저장소에 서버 인증서 설치:</span><span class="sxs-lookup"><span data-stu-id="22111-155">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="22111-156">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-156">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="22111-157">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-157">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="22111-158">Microsoft에서 발급한 인증서와 같이 클라이언트가 신뢰할 수 있는 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우 클라이언트 인증서 저장소를 서버 인증서로 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-158">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="22111-159">발급자 인증서 만들기:</span><span class="sxs-lookup"><span data-stu-id="22111-159">Creating the issuer certificate.</span></span>

     <span data-ttu-id="22111-160">Setup.bat 배치 파일의 다음 행에서는 사용할 발급자 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-160">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="22111-161">`%USER_NAME%` 변수는 발급자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-161">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="22111-162">이 변수를 변경하여 고유한 발급자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-162">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="22111-163">이 배치 파일의 기본값은 Alice입니다.</span><span class="sxs-lookup"><span data-stu-id="22111-163">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="22111-164">인증서는 CurrentUser 저장소 위치 아래의 My 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-164">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="22111-165">서버의 신뢰할 수 있는 인증서 저장소에 발급자 인증서 설치:</span><span class="sxs-lookup"><span data-stu-id="22111-165">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="22111-166">Setup.bat 배치 파일에서 다음 행은 클라이언트의 신뢰할 수 있는 사용자 저장소로 서버 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-166">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="22111-167">이 단계는 Makecert.exe에서 생성한 인증서를 클라이언트 컴퓨터에서 절대적으로 신뢰하지는 않기 때문에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-167">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="22111-168">Microsoft에서 발급한 인증서처럼 신뢰할 수 있는 클라이언트 루트 인증서를 기반으로 하는 인증서가 이미 있는 경우에는 발급자 인증서로 서버 인증서 저장소를 채우는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-168">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="22111-169">샘플을 설치하고 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="22111-169">To set up and build the sample</span></span>

1. <span data-ttu-id="22111-170">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-170">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="22111-171">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="22111-171">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="22111-172">Svcutil.exe를 사용하여 이 샘플에 대한 구성을 다시 생성할 경우 클라이언트 구성에서 엔드포인트 이름을 클라이언트 코드와 일치하도록 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-172">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="22111-173">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="22111-173">To run the sample on the same computer</span></span>

1. <span data-ttu-id="22111-174">관리자 권한으로 실행 되는 Visual Studio 2012 명령 프롬프트 내의 샘플 설치 폴더에서 Setup.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-174">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="22111-175">이 작업은 샘플 실행에 필요한 모든 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-175">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="22111-176">Setup.bat 배치 파일은 Visual Studio 2012 명령 프롬프트에서 실행 되도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-176">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="22111-177">Visual Studio 2012 명령 프롬프트 내에서 설정 된 PATH 환경 변수는 Setup.bat 스크립트에 필요한 실행 파일을 포함 하는 디렉터리를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="22111-177">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="22111-178">service\bin에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-178">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="22111-179">\client\bin에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-179">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="22111-180">클라이언트 콘솔 애플리케이션에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="22111-180">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="22111-181">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22111-181">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="22111-182">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="22111-182">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="22111-183">서비스 컴퓨터에 서비스 이진 파일용 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22111-183">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="22111-184">서비스 프로그램 파일을 서비스 컴퓨터의 서비스 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-184">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="22111-185">Setup.bat 및 Cleanup.bat 파일도 서비스 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-185">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="22111-186">컴퓨터의 정규화된 도메인 이름을 포함하는 주체 이름을 가진 서버 인증서가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-186">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="22111-187">이 새로운 인증서 이름을 반영하도록 Service.exe.config 파일을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-187">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="22111-188">Setup.bat 배치 파일을 수정하여 서버 인증서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-188">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="22111-189">setup.bat 파일은 관리자 권한으로 연 Visual Studio 용 개발자 명령 프롬프트 창에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-189">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="22111-190">서비스를 호스트하는 데 사용되는 컴퓨터의 정규화된 호스트 이름으로 `%SERVER_NAME%` 변수를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-190">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="22111-191">서버 인증서를 클라이언트의 CurrentUser-TrustedPeople 저장소에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-191">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="22111-192">신뢰할 수 있는 클라이언트 발급자가 서버 인증서를 발급한 경우에는 이 단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22111-192">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="22111-193">서비스 컴퓨터의 Service.exe.config 파일에서 기본 주소 값을 변경하여 localhost 대신 정규화된 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-193">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="22111-194">서비스 컴퓨터의 명령 프롬프트에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-194">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="22111-195">언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-195">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="22111-196">클라이언트 컴퓨터의 Client.exe.config 파일에서 엔드포인트의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-196">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="22111-197">클라이언트 컴퓨터의 명령 프롬프트 창에서 `Client.exe`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-197">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="22111-198">클라이언트와 서비스가 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22111-198">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="22111-199">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="22111-199">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="22111-200">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="22111-200">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
