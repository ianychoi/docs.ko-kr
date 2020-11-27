---
title: '방법: X.509 인증서를 사용하여 서비스 보안'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: bf498ee373f2d637a7a93fbc36225a38ff7744c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293899"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="8aa85-102">방법: X.509 인증서를 사용하여 서비스 보안</span><span class="sxs-lookup"><span data-stu-id="8aa85-102">How to: Secure a Service with an X.509 Certificate</span></span>

<span data-ttu-id="8aa85-103">X.509 인증서를 사용 하 여 서비스를 보호 하는 것은 WCF (Windows Communication Foundation)에서 대부분의 바인딩에서 사용 하는 기본 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="8aa85-104">이 항목에서는 X.509 인증서와 함께 자체 호스팅된 서비스를 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="8aa85-105">필수 구성 요소는 서버를 인증하는 데 사용할 수 있는 유효한 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="8aa85-106">인증서는 신뢰할 수 있는 인증 기관에 의해 서버에 발급되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="8aa85-107">인증서가 유효하지 않은 경우, 서비스를 사용하려고 시도하는 클라이언트에서 해당 서비스를 신뢰할 수 없으며, 결과적으로 연결이 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="8aa85-108">인증서를 사용 하는 방법에 대 한 자세한 내용은 [인증서 작업](working-with-certificates.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8aa85-108">For more information about using certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="8aa85-109">코드를 사용하여 인증서와 함께 서비스를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="8aa85-109">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="8aa85-110">서비스 계약과 구현된 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="8aa85-111">자세한 내용은 [서비스 디자인 및 구현](../designing-and-implementing-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8aa85-111">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="8aa85-112">다음 코드에서처럼 <xref:System.ServiceModel.WSHttpBinding> 클래스의 인스턴스를 만들고, 보안 모드를 <xref:System.ServiceModel.SecurityMode.Message>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="8aa85-113">다음 코드에서처럼 계약 형식과 구현된 계약 각각에 대해 두 개의 <xref:System.Type> 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="8aa85-114">서비스의 기본 주소에 대해 <xref:System.Uri> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="8aa85-115">는 `WSHttpBinding` HTTP 전송을 사용 하기 때문에 URI (Uniform Resource Identifier)는 해당 스키마로 시작 해야 합니다. 그렇지 않으면 서비스를 열 때 WCF (Windows Communication Foundation)가 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="8aa85-116">구현된 계약 형식 변수 및 URI와 함께 <xref:System.ServiceModel.ServiceHost> 클래스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="8aa85-117"><xref:System.ServiceModel.Description.ServiceEndpoint> 메서드를 사용하여 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>를 서비스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="8aa85-118">다음 코드에서처럼 계약, 바인딩 및 엔드포인트 주소를 생성자에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="8aa85-119">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-119">Optional.</span></span> <span data-ttu-id="8aa85-120">서비스로부터 메타데이터를 검색하려면 새 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 개체를 만들고 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="8aa85-121">유효한 인증서를 서비스에 추가하려면 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 클래스의 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="8aa85-122">메서드는 인증서를 찾기 위해 여러 메서드 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="8aa85-123">다음 예제에서는 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> 열거형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="8aa85-124">열거형은 제공된 값이 인증서가 발급된 엔터티의 이름임을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="8aa85-125">서비스 수신을 시작하려면 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="8aa85-126">콘솔 애플리케이션을 만들려면 수신 상태에서 서비스를 유지하도록 <xref:System.Console.ReadLine%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="8aa85-127">예제</span><span class="sxs-lookup"><span data-stu-id="8aa85-127">Example</span></span>  

 <span data-ttu-id="8aa85-128">다음 예제에서는 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 메서드를 사용하여 X.509 인증서와 함께 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8aa85-129">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="8aa85-129">Compiling the Code</span></span>  

 <span data-ttu-id="8aa85-130">코드를 컴파일하려면 다음 네임스페이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa85-130">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="8aa85-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8aa85-131">See also</span></span>

- [<span data-ttu-id="8aa85-132">인증서 사용</span><span class="sxs-lookup"><span data-stu-id="8aa85-132">Working with Certificates</span></span>](working-with-certificates.md)
