---
description: '자세한 정보: WCF에서 사용 되는 보안 개념'
title: WCF에서 사용되는 보안 개념
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 5ad5b80c69e5dec5675879984fbcd2585b295dd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779766"
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="04ecc-103">WCF에서 사용되는 보안 개념</span><span class="sxs-lookup"><span data-stu-id="04ecc-103">Security Concepts Used in WCF</span></span>

<span data-ttu-id="04ecc-104">WCF (Windows Communication Foundation) 보안은 이미 사용 되 고 다양 한 보안 인프라에서 배포 된 개념을 기반으로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-104">Windows Communication Foundation (WCF) security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 <span data-ttu-id="04ecc-105">WCF는 HTTP (HTTPS)를 통한 SSL(Secure Sockets Layer) (SSL)와 같은 이러한 인프라 중 일부를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-105">WCF supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="04ecc-106">그러나 WCF는 SOAP 인코딩된 메시지에 대해 새로운 상호 운용 가능한 보안 표준 (예: WS-SECURITY)을 구현 하 여 기존 보안 인프라를 지 원하는 것 이상으로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-106">However, WCF goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="04ecc-107">기존 메커니즘 또는 새로운 상호 운용 가능한 표준을 사용하는지 여부에 따라 두 가지의 보안 개념은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-107">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="04ecc-108">따라서 기존 인프라 및 최신 표준에 적용된 개념을 이해하는 것이 특정 애플리케이션에 대해 가장 적합한 보안 모델을 구현하는 데 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-108">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="04ecc-109">WCF 웹 서비스 보안에 대한 소개</span><span class="sxs-lookup"><span data-stu-id="04ecc-109">Introduction to Security for WCF Web Services</span></span>  

<span data-ttu-id="04ecc-110">Microsoft 패턴 및 사례 그룹은 [WCF 보안 가이드](https://archive.codeplex.com/?p=wcfsecurityguide)라는 심층 백서를 작성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-110">The Microsoft Patterns and Practices group wrote an in-depth white paper called [WCF Security Guide](https://archive.codeplex.com/?p=wcfsecurityguide).</span></span> <span data-ttu-id="04ecc-111">이 백서는 웹 서비스, 주요 WCF 보안 개념, 인트라넷 응용 프로그램 시나리오 및 인터넷 응용 프로그램 시나리오와 관련 하 여 기본적인 보안 개념을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-111">This white paper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="04ecc-112">산업 전반 보안 사양</span><span class="sxs-lookup"><span data-stu-id="04ecc-112">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="04ecc-113">공개 키 인프라</span><span class="sxs-lookup"><span data-stu-id="04ecc-113">Public Key Infrastructure</span></span>  

<span data-ttu-id="04ecc-114">PKI (공개 키 인프라)는 공개 키 암호화를 사용 하 여 전자적 트랜잭션과 관련 된 각 파티를 확인 하 고 인증 하는 디지털 인증서, 인증 기관 및 기타 등록 기관의 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-114">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public-key cryptography.</span></span>
  
### <a name="kerberos-protocol"></a><span data-ttu-id="04ecc-115">Kerberos 프로토콜</span><span class="sxs-lookup"><span data-stu-id="04ecc-115">Kerberos Protocol</span></span>  

 <span data-ttu-id="04ecc-116">*Kerberos 프로토콜* 은 Windows 도메인에서 사용자를 인증 하는 보안 메커니즘을 만들기 위한 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-116">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="04ecc-117">이를 통해 사용자가 도메인 내의 다른 엔터티로 보안 컨텍스트를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-117">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="04ecc-118">Windows 2000 이상 플랫폼은 기본적으로 Kerberos 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-118">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="04ecc-119">인트라넷 클라이언트와 상호 작용할 서비스를 만들 때 시스템의 메커니즘을 이해하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-119">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="04ecc-120">또한 *Web Services Security Kerberos 바인딩이* 널리 게시 되기 때문에 kerberos 프로토콜을 사용 하 여 인터넷 클라이언트와 통신할 수 있습니다. 즉, kerberos 프로토콜을 상호 운용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-120">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> <span data-ttu-id="04ecc-121">Windows에서 Kerberos 프로토콜을 구현 하는 방법에 대 한 자세한 내용은  [Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="04ecc-121">For more information about how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="04ecc-122">X.509 인증서</span><span class="sxs-lookup"><span data-stu-id="04ecc-122">X.509 Certificates</span></span>  

 <span data-ttu-id="04ecc-123">X.509 인증서는 보안 애플리케이션에 사용되는 기본 자격 증명 양식입니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-123">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="04ecc-124">X.509 인증서에 대 한 자세한 내용은 [X.509 공개 키 인증서](/windows/win32/seccertenroll/about-x-509-public-key-certificates)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04ecc-124">For more information on X.509 certificates see [X.509 Public Key Certificates](/windows/win32/seccertenroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="04ecc-125">X.509 인증서는 인증서 저장소 내에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-125">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="04ecc-126">Windows를 실행하는 컴퓨터에는 여러 종류의 인증서 저장소가 있으며 저장소마다 용도가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-126">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> <span data-ttu-id="04ecc-127">여러 저장소에 대 한 자세한 내용은 [인증서 저장소](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04ecc-127">For more information about the different stores, see [Certificate Stores](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="04ecc-128">웹 서비스 보안 사양</span><span class="sxs-lookup"><span data-stu-id="04ecc-128">Web Services Security Specifications</span></span>  

 <span data-ttu-id="04ecc-129">시스템 정의 바인딩에서는 일반적으로 많이 사용되는 웹 서비스 보안 사양을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-129">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="04ecc-130">시스템에서 제공 하는 바인딩 및 지원 되는 웹 서비스 사양의 전체 목록은 [System-Provided 상호 운용성 바인딩에서 지 원하는 웹 서비스 프로토콜](web-services-protocols-supported-by-system-provided-interoperability-bindings.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04ecc-130">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="04ecc-131">Access Control 메커니즘</span><span class="sxs-lookup"><span data-stu-id="04ecc-131">Access Control Mechanisms</span></span>  

 <span data-ttu-id="04ecc-132">WCF에서는 서비스 또는 작업에 대한 액세스를 제어하는 여러 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-132">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="04ecc-133">다음과 같은 방법이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="04ecc-133">Among them are</span></span>  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. <span data-ttu-id="04ecc-134">ASP.NET 멤버 자격 공급자</span><span class="sxs-lookup"><span data-stu-id="04ecc-134">ASP.NET Membership Provider</span></span>  
  
3. <span data-ttu-id="04ecc-135">ASP.NET 역할 공급자</span><span class="sxs-lookup"><span data-stu-id="04ecc-135">ASP.NET Role Provider</span></span>  
  
4. <span data-ttu-id="04ecc-136">권한 부여 관리자</span><span class="sxs-lookup"><span data-stu-id="04ecc-136">Authorization Manager</span></span>  
  
5. <span data-ttu-id="04ecc-137">ID 모델</span><span class="sxs-lookup"><span data-stu-id="04ecc-137">Identity Model</span></span>  
  
 <span data-ttu-id="04ecc-138">이러한 항목에 대 한 자세한 내용은 [Access Control 메커니즘](access-control-mechanisms.md) (영문)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04ecc-138">For more information on these topics see, [Access Control Mechanisms](access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ecc-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04ecc-139">See also</span></span>

- [<span data-ttu-id="04ecc-140">보안 개요</span><span class="sxs-lookup"><span data-stu-id="04ecc-140">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="04ecc-141">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="04ecc-141">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
