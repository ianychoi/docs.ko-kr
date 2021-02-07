---
description: '자세한 정보: 방법: ASP.NET 웹 서비스 클라이언트와 상호 운용 하도록 WCF 서비스 구성'
title: '방법: ASP.NET 웹 서비스 클라이언트와 상호 운용하도록 WCF 서비스 구성'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 180307763054f8dfe5696fb0bbf294ec2b5ee3db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743397"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a><span data-ttu-id="60f0c-103">방법: ASP.NET 웹 서비스 클라이언트와 상호 운용하도록 WCF 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="60f0c-103">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>

<span data-ttu-id="60f0c-104">ASP.NET 웹 서비스 클라이언트와 상호 운용할 수 있도록 WCF (Windows Communication Foundation) 서비스 끝점을 구성 하려면 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 형식을 서비스 끝점의 바인딩 형식으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-104">To configure a Windows Communication Foundation (WCF) service endpoint to be interoperable with ASP.NET Web service clients, use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
 <span data-ttu-id="60f0c-105">바인딩에서 HTTPS 및 전송 수준 클라이언트 인증에 대한 지원을 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-105">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span> <span data-ttu-id="60f0c-106">ASP.NET 웹 서비스 클라이언트는 MTOM 메시지 인코딩을 지원 하지 않으므로 속성은 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 기본값인로 유지 해야 합니다 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="60f0c-106">ASP.NET Web service clients do not support MTOM message encoding, so the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property should be left as its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>.</span></span> <span data-ttu-id="60f0c-107">ASP.NET 웹 서비스 클라이언트는 WS-SECURITY를 지원 하지 않으므로 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 를로 설정 해야 합니다 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> .</span><span class="sxs-lookup"><span data-stu-id="60f0c-107">ASP.NET Web Service clients do not support WS-Security, so the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> should be set to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
 <span data-ttu-id="60f0c-108">ASP.NET 웹 서비스 프록시 생성 도구 ( [Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [웹 서비스 검색 도구 (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), Visual Studio의 **웹 참조 추가** 기능 등 WCF 서비스에 대 한 메타 데이터를 사용할 수 있도록 하려면 HTTP/GET 메타 데이터 끝점을 노출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-108">To make the metadata for a WCF service available to ASP.NET Web service proxy generation tools (that is, [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio), you should expose an HTTP/GET metadata endpoint.</span></span>  
  
## <a name="add-an-endpoint-in-code"></a><span data-ttu-id="60f0c-109">코드에서 끝점 추가</span><span class="sxs-lookup"><span data-stu-id="60f0c-109">Add an endpoint in code</span></span>  
  
1. <span data-ttu-id="60f0c-110">새 <xref:System.ServiceModel.BasicHttpBinding> 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-110">Create a new <xref:System.ServiceModel.BasicHttpBinding> instance</span></span>  
  
2. <span data-ttu-id="60f0c-111">바인딩의 보안 모드를 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>로 설정하여 이 서비스 엔드포인트 바인딩에 대한 전송 보안을 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-111">Optionally enable transport security for this service endpoint binding by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="60f0c-112">자세한 내용은 [전송 보안](transport-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-112">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="60f0c-113">방금 만든 바인딩 인스턴스를 사용하여 새 애플리케이션 엔드포인트를 서비스 호스트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-113">Add a new application endpoint to your service host using the binding instance that you just created.</span></span> <span data-ttu-id="60f0c-114">코드에서 서비스 끝점을 추가 하는 방법에 대 한 자세한 내용은 [방법: 코드에서 서비스 끝점 만들기](how-to-create-a-service-endpoint-in-code.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-114">For details about how to add a service endpoint in code, see the [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
4. <span data-ttu-id="60f0c-115">서비스에 대해 HTTP/GET 메타데이터 엔드포인트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-115">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="60f0c-116">자세한 내용은 [방법: 코드를 사용 하 여 서비스에 대 한 메타 데이터 게시](how-to-publish-metadata-for-a-service-using-code.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-116">For details see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span>  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a><span data-ttu-id="60f0c-117">구성 파일에 끝점 추가</span><span class="sxs-lookup"><span data-stu-id="60f0c-117">Add an endpoint in a configuration file</span></span>  
  
1. <span data-ttu-id="60f0c-118">새 <xref:System.ServiceModel.BasicHttpBinding> 바인딩 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-118">Create a new <xref:System.ServiceModel.BasicHttpBinding> binding configuration.</span></span> <span data-ttu-id="60f0c-119">자세한 내용은 [방법: 구성에서 서비스 바인딩 지정](../how-to-specify-a-service-binding-in-configuration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-119">For details, see the [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
2. <span data-ttu-id="60f0c-120">바인딩의 보안 모드를 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>로 설정하여 이 서비스 엔드포인트 바인딩 구성에 대한 전송 보안을 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-120">Optionally enable transport security for this service endpoint binding configuration by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="60f0c-121">자세한 내용은 [전송 보안](transport-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-121">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="60f0c-122">방금 만든 바인딩 구성을 사용하여 서비스에 대한 새 애플리케이션 엔드포인트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-122">Configure a new application endpoint for your service using the binding configuration that you just created.</span></span> <span data-ttu-id="60f0c-123">구성 파일에서 서비스 끝점을 추가 하는 방법에 대 한 자세한 내용은 [방법: 구성에서 서비스 끝점 만들기](how-to-create-a-service-endpoint-in-configuration.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-123">For details about how to add a service endpoint in a configuration file, see the [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
4. <span data-ttu-id="60f0c-124">서비스에 대해 HTTP/GET 메타데이터 엔드포인트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-124">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="60f0c-125">자세한 내용은 [방법: 구성 파일을 사용 하 여 서비스에 대 한 메타 데이터 게시](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60f0c-125">For details see the [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f0c-126">예제</span><span class="sxs-lookup"><span data-stu-id="60f0c-126">Example</span></span>  

 <span data-ttu-id="60f0c-127">다음 예제 코드에서는 ASP.NET 웹 서비스 클라이언트와 호환 되는 WCF 끝점을 코드 또는 구성 파일에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="60f0c-127">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and alternatively in configuration files.</span></span>  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a><span data-ttu-id="60f0c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60f0c-128">See also</span></span>

- [<span data-ttu-id="60f0c-129">방법: 코드에서 서비스 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="60f0c-129">How to: Create a Service Endpoint in Code</span></span>](how-to-create-a-service-endpoint-in-code.md)
- [<span data-ttu-id="60f0c-130">방법: 코드를 사용하여 서비스에 대한 메타데이터 게시</span><span class="sxs-lookup"><span data-stu-id="60f0c-130">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
- [<span data-ttu-id="60f0c-131">방법: 구성에서 서비스 바인딩 지정</span><span class="sxs-lookup"><span data-stu-id="60f0c-131">How to: Specify a Service Binding in Configuration</span></span>](../how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="60f0c-132">방법: 구성에서 서비스 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="60f0c-132">How to: Create a Service Endpoint in Configuration</span></span>](how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="60f0c-133">방법: 구성 파일을 사용하여 서비스에 대한 메타데이터 게시</span><span class="sxs-lookup"><span data-stu-id="60f0c-133">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="60f0c-134">전송 보안</span><span class="sxs-lookup"><span data-stu-id="60f0c-134">Transport Security</span></span>](transport-security.md)
- [<span data-ttu-id="60f0c-135">메타데이터 사용</span><span class="sxs-lookup"><span data-stu-id="60f0c-135">Using Metadata</span></span>](using-metadata.md)
