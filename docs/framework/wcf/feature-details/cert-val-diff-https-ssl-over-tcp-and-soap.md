---
title: HTTPS, TCP를 통한 SSL 및 SOAP 보안의 인증서 유효성 검사 차이점
description: HTTPS 또는 TCP 외에도 WCF에서 제공 하는 메시지 계층 (SOAP) 보안을 사용 하는 인증서와 WCF가 이러한 인증서의 유효성을 검사 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 9be640f892fd1fcc21711114415902335f9031bd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244850"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="a55a9-103">HTTPS, TCP를 통한 SSL 및 SOAP 보안의 인증서 유효성 검사 차이점</span><span class="sxs-lookup"><span data-stu-id="a55a9-103">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>

<span data-ttu-id="a55a9-104">HTTP (HTTPS) 또는 TCP를 통한 TLS (전송 계층 보안) 외에도 SOAP (메시지 계층) 보안을 사용 하 여 WCF (Windows Communication Foundation)에서 인증서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-104">You can use certificates in Windows Communication Foundation (WCF) with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="a55a9-105">이 항목에서는 이러한 인증서의 유효성을 검사하는 방법의 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-105">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="a55a9-106">HTTPS 클라이언트 인증서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a55a9-106">Validation of HTTPS Client Certificates</span></span>  

 <span data-ttu-id="a55a9-107">HTTPS를 사용하여 클라이언트와 서비스 간에 통신하는 경우 클라이언트에서 서비스를 인증하는 데 사용하는 인증서는 신뢰 체인을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-107">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="a55a9-108">즉, 신뢰할 수 있는 루트 인증 기관에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-108">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="a55a9-109">연결되지 않은 경우 HTTP 계층에서 "원격 서버에서 (403) 사용할 수 없음 오류를 반환했습니다."라는 메시지와 함께 <xref:System.Net.WebException>이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-109">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> <span data-ttu-id="a55a9-110">WCF는이 예외를로 표시 <xref:System.ServiceModel.Security.MessageSecurityException> 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-110">WCF surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="a55a9-111">HTTPS 서비스 인증서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a55a9-111">Validation of HTTPS Service Certificates</span></span>  

 <span data-ttu-id="a55a9-112">HTTPS를 사용하여 클라이언트와 서비스 간에 통신하는 경우 서버에서 인증하는 데 사용하는 인증서는 신뢰 체인을 기본적으로 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-112">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="a55a9-113">즉, 신뢰할 수 있는 루트 인증 기관에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-113">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="a55a9-114">인증서가 해지되었는지 여부를 확인하기 위해 온라인 확인을 수행하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-114">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="a55a9-115">다음 코드에서처럼 <xref:System.Net.Security.RemoteCertificateValidationCallback> 콜백을 등록하여 이 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-115">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="a55a9-116">여기서 `ValidateServerCertificate`의 서명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-116">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="a55a9-117">`ValidateServerCertificate`를 구현하면 클라이언트 애플리케이션 개발자가 서비스 인증서의 유효성을 검사하는 데 필요하다고 판단하는 확인 사항을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-117">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="a55a9-118">TCP를 통한 SSL 또는 SOAP 보안에서 클라이언트 인증서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a55a9-118">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  

 <span data-ttu-id="a55a9-119">TCP를 통한 SSL(Secure Sockets Layer) 또는 SOAP 메시지 보안을 사용하는 경우 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 속성 값에 따라 클라이언트 인증서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-119">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="a55a9-120">속성은 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 값 중 하나로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-120">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="a55a9-121"><xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 속성 값에 따라 해지 확인을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-121">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="a55a9-122">속성은 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 값 중 하나로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-122">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="a55a9-123">TCP를 통한 SSL 또는 SOAP 보안에서 서비스 인증서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a55a9-123">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  

 <span data-ttu-id="a55a9-124">TCP를 통한 SSL 또는 SOAP 메시지 보안을 사용하는 경우 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 속성 값에 따라 서비스 인증서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-124">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="a55a9-125">속성은 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 값 중 하나로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-125">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="a55a9-126"><xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 속성 값에 따라 해지 확인을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-126">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="a55a9-127">속성은 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 값 중 하나로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a55a9-127">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a55a9-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a55a9-128">See also</span></span>

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [<span data-ttu-id="a55a9-129">인증서 사용</span><span class="sxs-lookup"><span data-stu-id="a55a9-129">Working with Certificates</span></span>](working-with-certificates.md)
