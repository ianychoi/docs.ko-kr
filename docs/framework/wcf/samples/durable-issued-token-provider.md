---
description: '자세한 정보: 지 속성 발급 토큰 공급자'
title: 영속 제공된 토큰 공급자
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: dfde4efa961704659d9d1de6010b16616467a779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793274"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="a85be-103">영속 제공된 토큰 공급자</span><span class="sxs-lookup"><span data-stu-id="a85be-103">Durable Issued Token Provider</span></span>

<span data-ttu-id="a85be-104">이 샘플에서는 사용자 지정 클라이언트가 발급한 토큰 공급자를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-104">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a85be-105">토론(Discussion)</span><span class="sxs-lookup"><span data-stu-id="a85be-105">Discussion</span></span>  

 <span data-ttu-id="a85be-106">WCF (Windows Communication Foundation)의 토큰 공급자는 보안 인프라에 자격 증명을 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-106">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="a85be-107">일반적으로 토큰 공급자는 대상을 검사하고 적절한 자격 증명을 발급하여 보안 인프라에서 메시지의 보안을 유지할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-107">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="a85be-108">WCF는 CardSpace 토큰 공급자와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-108">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="a85be-109">사용자 지정 토큰 공급자는 다음과 같은 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-109">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="a85be-110">기본 제공 토큰 공급자가 작동하지 않는 자격 증명 저장소가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="a85be-110">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="a85be-111">WCF 클라이언트가 자격 증명을 사용 하는 경우 사용자가 세부 정보를 제공 하는 시점에서 자격 증명을 변환 하는 사용자 지정 메커니즘을 제공 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="a85be-111">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="a85be-112">사용자 지정 토큰을 빌드하고 있는 경우</span><span class="sxs-lookup"><span data-stu-id="a85be-112">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="a85be-113">이 샘플에서는 STS(보안 토큰 서비스)에서 발급한 토큰을 캐시하는 사용자 지정 토큰 공급자를 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-113">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="a85be-114">즉, 이 샘플에서는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-114">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="a85be-115">사용자 지정 토큰 공급자로 클라이언트를 구성하는 방법</span><span class="sxs-lookup"><span data-stu-id="a85be-115">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="a85be-116">발급 된 토큰을 캐시 하 여 WCF 클라이언트에 제공 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-116">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="a85be-117">서버의 X.509 인증서를 사용하여 클라이언트에서 서버를 인증하는 방법</span><span class="sxs-lookup"><span data-stu-id="a85be-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="a85be-118">이 샘플은 클라이언트 콘솔 프로그램(Client.exe), 보안 토큰 서비스 콘솔 프로그램(Securitytokenservice.exe) 및 서비스 콘솔 프로그램(Service.exe)으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-118">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="a85be-119">이 서비스는 요청-회신 통신 패턴을 정의하는 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-119">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="a85be-120">계약은 수학 연산(Add, Subtract, Multiply 및 Divide)을 노출시키는 `ICalculator` 인터페이스에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-120">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="a85be-121">클라이언트가 STS(보안 토큰 서비스)에서 보안 토큰을 가져오고 지정된 수학 연산을 서비스에 동기적으로 요청하면 서비스에서 결과를 회신합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-121">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="a85be-122">콘솔 창에는 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-122">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a85be-123">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-123">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a85be-124">이 샘플에서는를 사용 하 여 ICalculator 계약을 노출 합니다 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a85be-124">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="a85be-125">다음 코드에서는 클라이언트에서의 바인딩 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-125">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="a85be-126">`security`의 `wsFederationHttpBinding` 요소에서 `mode` 값은 사용해야 하는 보안 모드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-126">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="a85be-127">이 샘플에서는 메시지 보안이 사용되므로 `message`의 `wsFederationHttpBinding` 요소 안에 `security`의 `wsFederationHttpBinding` 요소가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-127">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="a85be-128">`issuer`의 `wsFederationHttpBinding` 안에서`message`의 `wsFederationHttpBinding` 요소는 클라이언트가 계산기 서비스에 대해 인증될 수 있도록 보안 토큰을 클라이언트에게 발급하는 보안 토큰 서비스의 주소와 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-128">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="a85be-129">서비스에서 이 바인딩의 구성은 다음 코드와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-129">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="a85be-130">`security`의 `wsFederationHttpBinding` 요소에서 `mode` 값은 사용해야 하는 보안 모드를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-130">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="a85be-131">이 샘플에서는 메시지 보안이 사용되므로 `message`의 `wsFederationHttpBinding` 요소 안에 `security`의 `wsFederationHttpBinding` 요소가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-131">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="a85be-132">`issuerMetadata`의 `wsFederationHttpBinding` 요소 안에서 `message`의 `wsFederationHttpBinding` 요소는 보안 토큰 서비스에 대한 메타데이터를 검색하는 데 사용할 수 있는 엔드포인트의 주소와 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-132">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="a85be-133">다음 코드에서는 서비스의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-133">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="a85be-134">`issuedTokenAuthentication` 요소 내부의 `serviceCredentials` 요소를 사용하면 서비스에서는 인증 과정 중 클라이언트가 제시할 수 있는 토큰에 대한 제약 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-134">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="a85be-135">이 구성은 주체 이름이 CN=STS인 인증서에 의해 서명된 토큰을 서비스에서 수락하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-135">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="a85be-136">보안 토큰 서비스는 표준 wsHttpBinding을 사용하여 단일 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-136">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="a85be-137">보안 토큰 서비스는 클라이언트의 토큰 요청에 응답하며, 클라이언트가 Windows 계정을 사용하여 인증하는 경우 클라이언트의 사용자 이름을 발급된 토큰의 클레임으로 포함하는 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-137">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="a85be-138">토큰을 만드는 동안 보안 토큰 서비스는 CN=STS 인증서에 연결된 프라이빗 키를 사용하여 토큰에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-138">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="a85be-139">또한 대칭 키를 만들고 CN=localhost 인증서와 연관된 공개 키를 사용하여 이를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-139">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="a85be-140">보안 토큰 서비스는 토큰을 클라이언트에 반환하면서 대칭 키도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-140">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="a85be-141">클라이언트는 발급된 토큰을 계산기 서비스에 제공하고 대칭 키로 메시지에 서명하여 해당 키를 알고 있음을 증명합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-141">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="a85be-142">사용자 지정 클라이언트 자격 증명 및 토큰 공급자</span><span class="sxs-lookup"><span data-stu-id="a85be-142">Custom Client Credentials and Token Provider</span></span>  

 <span data-ttu-id="a85be-143">다음 단계에서는 발급 된 토큰을 캐시 하 고 WCF: security와 통합 하는 사용자 지정 토큰 공급자를 개발 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-143">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="a85be-144">사용자 지정 토큰 공급자를 개발하려면</span><span class="sxs-lookup"><span data-stu-id="a85be-144">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="a85be-145">사용자 지정 토큰 공급자를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-145">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="a85be-146">샘플에서는 캐시에서 검색한 보안 토큰을 반환하는 사용자 지정 토큰 공급자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-146">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="a85be-147">이 작업을 수행하려면 사용자 지정 토큰 공급자가 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 클래스를 파생하고 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 메서드를 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-147">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="a85be-148">이 메서드는 캐시로부터 토큰을 가져오려고 시도하거나 캐시에 토큰이 없는 경우에는 기본 공급자에서 토큰을 검색하여 검색한 토큰을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-148">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="a85be-149">두 경우 모두 메서드는 `SecurityToken`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-149">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="a85be-150">사용자 지정 보안 토큰 관리자를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-150">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="a85be-151"><xref:System.IdentityModel.Selectors.SecurityTokenManager>는 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 메서드에서 전달되는 특정 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>에 대한 `CreateSecurityTokenProvider`를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-151">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="a85be-152">또한 보안 토큰 관리자는 토큰 인증자와 토큰 serializer를 만드는 데 사용되지만 이 샘플에서는 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-152">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="a85be-153">이 샘플에서 사용자 지정 보안 토큰 관리자는 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 클래스를 상속하며, 전달된 토큰 요구 사항에서 발급된 토큰이 필요함을 나타낼 때 사용자 지정 토큰 공급자를 반환하도록 `CreateSecurityTokenProvider` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-153">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="a85be-154">사용자 지정 클라이언트 자격 증명을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-154">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="a85be-155">클라이언트 자격 증명 클래스는 클라이언트 프록시에 대해 구성된 자격 증명을 나타내는 데 사용되며 토큰 인증자, 토큰 공급자 및 토큰 serializer를 가져오는 데 사용되는 보안 토큰 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-155">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="a85be-156">토큰 캐시를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-156">Implement the token cache.</span></span> <span data-ttu-id="a85be-157">이 샘플 구현에서는 특정 토큰 캐시의 소비자가 캐시와 상호 작용할 때 이용하는 추상 기본 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-157">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="a85be-158">클라이언트가 사용자 지정 클라이언트 자격 증명을 사용할 수 있도록 이 샘플에서는 기본 클라이언트 자격 증명 클래스를 삭제하고 새 클라이언트 자격 증명 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-158">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="a85be-159">샘플 실행</span><span class="sxs-lookup"><span data-stu-id="a85be-159">Running the sample</span></span>  

 <span data-ttu-id="a85be-160">샘플 실행을 위한 지침이 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-160">See the following instructions to run the sample.</span></span> <span data-ttu-id="a85be-161">샘플을 실행하면 보안 토큰에 대한 요청이 보안 토큰 서비스 콘솔 창에 표시되고,</span><span class="sxs-lookup"><span data-stu-id="a85be-161">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="a85be-162">작업 요청 및 응답이 클라이언트 및 서비스 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-162">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="a85be-163">애플리케이션을 종료하려면 아무 콘솔 창에서나 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-163">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="a85be-164">Setup.cmd 배치 파일</span><span class="sxs-lookup"><span data-stu-id="a85be-164">The Setup.cmd Batch File</span></span>  

 <span data-ttu-id="a85be-165">이 샘플에 포함된 Setup.cmd 배치 파일을 사용하면 서버와 보안 토큰 서비스를 관련 인증서와 함께 구성하여 자체 호스팅된 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-165">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="a85be-166">배치 파일은 CurrentUser/TrustedPeople 인증서 저장소 둘 다에서 두 개의 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-166">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="a85be-167">주체 이름이 CN=STS인 첫 번째 인증서는 보안 토큰 서비스가 클라이언트에 발급되는 보안 토큰에 서명하기 위해 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-167">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="a85be-168">주체 이름이 CN=localhost인 두 번째 인증서는 보안 토큰 서비스가 서비스에서 해독할 수 있는 암호를 암호화하기 위해 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-168">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a85be-169">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="a85be-169">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a85be-170">Setup.cmd 파일을 실행하여 필요한 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-170">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="a85be-171">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="a85be-171">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="a85be-172">솔루션의 모든 프로젝트가 빌드되는지 확인합니다(Shared, RSTRSTR, Service, SecurityTokenService 및 Client).</span><span class="sxs-lookup"><span data-stu-id="a85be-172">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="a85be-173">Service.exe 및 SecurityTokenService.exe가 모두 관리자 권한으로 실행되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-173">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="a85be-174">Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-174">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a85be-175">샘플 실행 후 정리를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="a85be-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="a85be-176">샘플 실행을 완료했으면 샘플 폴더에서 Cleanup.cmd를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-176">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a85be-177">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-177">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a85be-178">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a85be-178">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a85be-179">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-179">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a85be-180">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85be-180">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
