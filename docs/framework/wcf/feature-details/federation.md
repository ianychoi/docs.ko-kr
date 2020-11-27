---
title: 페더레이션
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 5b5e944b96fc5e56fbb4d19a582ba9dd245904b4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286749"
---
# <a name="federation"></a><span data-ttu-id="42030-102">페더레이션</span><span class="sxs-lookup"><span data-stu-id="42030-102">Federation</span></span>

<span data-ttu-id="42030-103">이 항목에서는 페더레이션 보안의 개념에 대한 간략한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="42030-104">또한 페더레이션 보안 아키텍처를 배포 하기 위한 WCF (Windows Communication Foundation) 지원에 대해서도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="42030-105">페더레이션을 보여 주는 샘플 응용 프로그램은 [페더레이션 샘플](../samples/federation-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42030-105">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="42030-106">페더레이션 보안 정의</span><span class="sxs-lookup"><span data-stu-id="42030-106">Definition of Federated Security</span></span>  

 <span data-ttu-id="42030-107">페더레이션 보안을 사용하면 클라이언트가 액세스 중인 서비스, 관련 인증, 권한 부여 절차를 서로 확실히 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="42030-108">페더레이션 보안을 통해 여러 신뢰 영역에 있는 여러 시스템, 네트워크 및 조직 간에 협업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="42030-109">WCF는 페더레이션된 보안을 사용 하는 분산 시스템을 구축 하 고 배포 하기 위한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="42030-110">페더레이션 보안 아키텍처의 요소</span><span class="sxs-lookup"><span data-stu-id="42030-110">Elements of a Federated Security Architecture</span></span>  

 <span data-ttu-id="42030-111">다음 표에 설명된 것처럼 페더레이션 보안 아키텍처에는 세 가지 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="42030-112">요소</span><span class="sxs-lookup"><span data-stu-id="42030-112">Element</span></span>|<span data-ttu-id="42030-113">Description</span><span class="sxs-lookup"><span data-stu-id="42030-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42030-114">도메인/영역</span><span class="sxs-lookup"><span data-stu-id="42030-114">Domain/realm</span></span>|<span data-ttu-id="42030-115">보안 관리 또는 신뢰의 단일 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="42030-116">일반 도메인은 단일 조직을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="42030-117">페더레이션</span><span class="sxs-lookup"><span data-stu-id="42030-117">Federation</span></span>|<span data-ttu-id="42030-118">설정된 신뢰가 있는 도메인의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="42030-119">신뢰 수준은 다른 경우도 있지만 일반적으로 인증 및 권한 부여가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="42030-120">일반적인 페더레이션은 리소스 집합에 대한 공유 액세스에서 신뢰가 설정된 여러 조직을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="42030-121">STS(보안 토큰 서비스)</span><span class="sxs-lookup"><span data-stu-id="42030-121">Security Token Service (STS)</span></span>|<span data-ttu-id="42030-122">보안 토큰을 발급하는 웹 서비스. 이 웹 서비스에서 신뢰하는 증거를 기반으로 누구나 이 어설션을 신뢰할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42030-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="42030-123">이는 도메인 간의 신뢰를 조정하는 기준을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="42030-124">예제 시나리오</span><span class="sxs-lookup"><span data-stu-id="42030-124">Example Scenario</span></span>  

 <span data-ttu-id="42030-125">다음 그림은 페더레이션된 보안의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-125">The following illustration shows an example of federated security:</span></span>  
  
 ![일반적인 페더레이션 보안 시나리오를 보여 주는 다이어그램](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="42030-127">이 시나리오에는 A와 B라는 두 조직이 있습니다. 조직 B에는 조직 A의 일부 사용자가 가치 있게 여기는 웹 리소스(웹 서비스)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42030-128">이 섹션에서는 *리소스*, *서비스* 및 *웹 서비스* 라는 용어를 교대로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="42030-129">일반적으로 조직 A의 사용자는 조직 B의 서비스에 액세스하기 전에 일부 유효한 인증 형식을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="42030-130">뿐만 아니라 해당 사용자는 조직 B에서 특정 리소스에 액세스하려면 권한을 부여받아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="42030-131">이 문제를 해결하고 조직 A의 사용자가 조직 B의 리소스에 액세스할 수 있도록 하기 위한 한 가지 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="42030-132">조직 A의 사용자는 조직 B와 함께 자격 증명(사용자 이름 및 암호)을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="42030-133">리소스에 액세스하는 동안 조직 A의 사용자는 자격 증명을 조직 B에 제공하고, 리소스에 액세스하기 전에 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="42030-134">이 접근 방식에는 세 가지 중대한 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="42030-135">조직 B는 해당 로컬 사용자의 자격 증명뿐만 아니라 조직 A의 사용자 자격 증명도 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="42030-136">조직 A의 사용자는 조직 A 내의 리소스에 대한 액세스 권한을 얻기 위해 일반적으로 사용하는 자격 증명 외에 추가 자격 증명 집합도 유지 관리(추가 사용자 이름 및 암호를 기억)해야 합니다. 이렇게 되면 사용자는 대개 여러 서비스 사이트에서 동일한 사용자 이름과 암호를 사용하게 되며, 이것은 취약한 보안 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="42030-137">여러 조직이 조직 B의 리소스를 가치 있는 것으로 인식함에 따라 아키텍처는 확장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="42030-138">위에 언급한 단점을 해결하는 대체 접근 방식은 페더레이션 보안을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="42030-139">이러한 접근 방식으로 조직 A와 B는 신뢰 관계를 구축하고, 구축된 신뢰 관계를 조정하기 위해 STS(보안 토큰 서비스)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="42030-140">페더레이션 보안 아키텍처에서, 조직 A의 사용자는 조직 B의 STS에서 발급된 유효한 보안 토큰(특정 서비스에 대한 액세스 권한을 부여하고 인증)을 제공해야 하는 조직 B의 웹 서비스에 액세스할지 여부를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="42030-141">사용자는 STS B에 연결하여 STS와 관련된 정책으로부터 다른 수준의 간접 참조를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="42030-142">STS A(클라이언트 신뢰 영역)에서 발급한 유효한 보안 토큰을 제공해야 STS B가 보안 토큰을 발급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="42030-143">이는 두 조직 간에 자연스럽게 구축된 신뢰 관계이며, 조직 B가 조직 A의 사용자 ID를 관리할 필요가 없음을 의미합니다. 사실상 STS B에는 일반적으로 null `issuerAddress`와 `issuerMetadataAddress`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="42030-144">자세한 내용은 [방법: 로컬 발급자 구성](how-to-configure-a-local-issuer.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42030-144">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="42030-145">이 경우 클라이언트는 STS A를 찾기 위해 로컬 정책을 검색 합니다. 이 구성을 *홈 영역 페더레이션* 이라고 하며, sts B가 sts A에 대 한 정보를 유지 관리할 필요가 없기 때문에 더 효율적으로 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="42030-146">그런 다음 사용자는 조직 A의 STS에 연결하고, 조직 A 내의 기타 리소스에 대한 액세스 권한을 얻기 위해 일반적으로 사용하는 인증 자격 증명을 제공함으로써 보안 토큰을 가져옵니다. 이는 또한 사용자가 여러 자격 증명 집합을 유지 관리해야 하거나 여러 서비스 사이트에서 동일한 자격 증명 집합을 사용하는 문제를 줄여줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="42030-147">사용자는 STS A로부터 가져온 보안 토큰을 STS B에 제공합니다. 조직 B에서는 사용자 요청에 대한 권한 부여를 수행하고, 자체 보안 토큰 집합으로부터 사용자에게 보안 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="42030-148">그런 다음 사용자는 토큰을 조직 B의 리소스에 제공하고 서비스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="42030-149">WCF의 페더레이션 보안을 위한 지원</span><span class="sxs-lookup"><span data-stu-id="42030-149">Support for Federated Security in WCF</span></span>  

 <span data-ttu-id="42030-150">WCF는를 통해 페더레이션 보안 아키텍처를 배포 하기 위한 턴키 지원을 제공 합니다 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="42030-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="42030-151">요소는 암호화 된 안전 하 고 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 상호 운용할 수 있는 바인딩을 제공 합니다 .이 바인딩을 사용 하 여 요청-회신 통신 스타일에 대 한 기본 전송 메커니즘으로 HTTP를 사용 하 고, 텍스트와 XML을 인코딩에 대 한 통신 형식으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-151">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="42030-152">페더레이션 보안 시나리오에서를 사용 하는 것은 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 다음 섹션에 설명 된 대로 논리적으로 독립적인 두 단계로 분리 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-152">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="42030-153">1단계: 디자인 단계</span><span class="sxs-lookup"><span data-stu-id="42030-153">Phase 1: Design Phase</span></span>  

 <span data-ttu-id="42030-154">디자인 단계에서 클라이언트는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 서비스 끝점이 노출 하는 정책을 읽고 서비스의 인증 및 권한 부여 요구 사항을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="42030-155">적절한 프록시는 클라이언트에서 다음 페더레이션 보안 통신 패턴을 만들기 위해 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="42030-156">클라이언트 신뢰 영역의 STS로부터 보안 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42030-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="42030-157">서비스 신뢰 영역의 STS에 대해 토큰을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="42030-158">서비스 신뢰 영역에서 STS로부터 보안 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="42030-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="42030-159">서비스에 대한 토큰을 제시하여 서비스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="42030-160">2단계: 런타임 단계</span><span class="sxs-lookup"><span data-stu-id="42030-160">Phase 2: Run-Time Phase</span></span>  

 <span data-ttu-id="42030-161">런타임 단계 동안 클라이언트는 WCF 클라이언트 클래스의 개체를 인스턴스화하고 WCF 클라이언트를 사용 하 여 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="42030-162">WCF의 기본 프레임 워크는 페더레이션 보안 통신 패턴에서 이전에 언급 된 단계를 처리 하 고 클라이언트에서 서비스를 원활 하 게 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="42030-163">WCF를 사용하여 샘플 구현</span><span class="sxs-lookup"><span data-stu-id="42030-163">Sample Implementation Using WCF</span></span>  

 <span data-ttu-id="42030-164">다음 그림에서는 WCF의 네이티브 지원을 사용 하는 페더레이션된 보안 아키텍처에 대 한 샘플 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![샘플 페더레이션 보안 구현을 보여 주는 다이어그램](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="42030-166">예제 MyService</span><span class="sxs-lookup"><span data-stu-id="42030-166">Example MyService</span></span>  

 <span data-ttu-id="42030-167">ph x="1" /&gt; 서비스는 `MyServiceEndpoint`를 통해 단일 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="42030-168">다음 그림에서는 엔드포인트와 연관된 주소, 바인딩 및 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![MyServiceEndpoint 세부 정보를 표시 하는 다이어그램입니다.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="42030-170">서비스 끝점은 `MyServiceEndpoint` 를 사용 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 하며, `accessAuthorized` STS B에서 발급 한 클레임에 유효한 SAML (Security 어설션이 Markup Language) 토큰이 필요 합니다. 이는 서비스 구성에 선언적으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="42030-171">`MyService`에서 필요로 하는 클레임에 대해 미세한 지점이 언급되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="42030-172">두 번째 그림에서는 `MyService`에는 `accessAuthorized` 클레임과 함께 SAML 토큰이 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="42030-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="42030-173">좀 더 구체적으로 설명하면 이는 `MyService`에서 필요로 하는 클레임 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="42030-174">이 클레임 형식의 정규화 된 이름은 `http://tempuri.org:accessAuthorized` 서비스 구성 파일에 사용 되는 (관련 네임 스페이스와 함께)입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="42030-175">이 클레임의 값은 이 클레임의 존재를 표시하고, STS B에 의해 `true`로 설정된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="42030-176">런타임에 이 정책은 `MyServiceOperationRequirement`의 일부로 구현되는 `MyService` 클래스에 의해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="42030-177">STS B</span><span class="sxs-lookup"><span data-stu-id="42030-177">STS B</span></span>  

 <span data-ttu-id="42030-178">다음 그림에서는 STS B를 보여 줍니다. 위에서 설명한 것처럼 STS(보안 토큰 서비스)도 웹 서비스이며 이와 연관된 엔드포인트, 정책 등을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42030-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![보안 토큰 서비스 B를 보여 주는 다이어그램](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="42030-180">STS B는 보안 토큰을 요청하는 데 사용할 수 있는 `STSEndpoint`라는 단일 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="42030-181">특히 STS B는 서비스에 액세스하기 위해 `accessAuthorized` 클레임과 함께 `MyService` 서비스 사이트에 제공할 수 있는 SAML 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="42030-182">그러나 STS B를 사용하려면 `userAuthenticated` 클레임이 포함된 STS A에서 발급한 유효한 SAML 토큰을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="42030-183">이는 STS 구성에서 선언적으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="42030-184">다시 클레임은 `userAuthenticated` STS B에 필요한 클레임 유형입니다. 이 클레임 형식의 정규화 된 이름은 `http://tempuri.org:userAuthenticated` STS 구성 파일에서 사용 되는 (관련 네임 스페이스와 함께)입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="42030-185">이 클레임의 값은 이 클레임의 존재를 표시하고 STS A에 의해 `true`로 설정된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="42030-186">런타임에 `STS_B_OperationRequirement` 클래스는 STS B의 일부로 구현되는 이 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="42030-187">액세스가 확인되면 STS B는 `accessAuthorized` 클레임과 함께 SAML 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="42030-188">STS A</span><span class="sxs-lookup"><span data-stu-id="42030-188">STS A</span></span>  

 <span data-ttu-id="42030-189">다음 그림은 STS A를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="42030-190">![페더레이션](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="42030-190">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="42030-191">STS B와 마찬가지로 STS A도 보안 토큰을 발급하고, 이를 위해 단일 엔드포인트를 노출하는 웹 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="42030-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="42030-192">그러나 다른 바인딩 ()을 사용 `wsHttpBinding` 하며 사용자가 클레임을 사용 하 여 유효한 CardSpace를 제공 해야 `emailAddress` 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="42030-193">그 결과, STS A가 `userAuthenticated` 클레임과 함께 SAML 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="42030-194">이는 서비스 구성에서 선언적으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="42030-195">런타임에 `STS_A_OperationRequirement` 클래스는 STS A의 일부로 구현되는 이 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="42030-196">액세스가 `true`이면 STS A는 `userAuthenticated` 클레임과 함께 SAML 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="42030-197">조직 A의 클라이언트</span><span class="sxs-lookup"><span data-stu-id="42030-197">Client at Organization A</span></span>  

 <span data-ttu-id="42030-198">다음 그림에서는 `MyService` 서비스 호출에 포함된 단계와 함께 조직 A의 클라이언트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="42030-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="42030-199">다른 기능 구성 요소도 완전성을 위해 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-199">The other functional components are also included for completeness.</span></span>  
  
 ![MyService 서비스 호출의 단계를 보여 주는 다이어그램입니다.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="42030-201">요약</span><span class="sxs-lookup"><span data-stu-id="42030-201">Summary</span></span>  

 <span data-ttu-id="42030-202">페더레이션 보안은 책임을 확실히 나누며, 안전하고 확장성 있는 서비스 아키텍처를 구축하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42030-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="42030-203">WCF는 분산 응용 프로그램을 빌드 및 배포 하기 위한 플랫폼으로 페더레이션 보안을 구현 하기 위한 기본 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="42030-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42030-204">참조</span><span class="sxs-lookup"><span data-stu-id="42030-204">See also</span></span>

- [<span data-ttu-id="42030-205">보안</span><span class="sxs-lookup"><span data-stu-id="42030-205">Security</span></span>](security.md)
