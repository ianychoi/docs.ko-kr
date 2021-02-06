---
description: '자세히 알아보기: WS-I Basic Profile 1.1 상호 운용 가능한 서비스 만들기'
title: WS-I Basic Profile 1.1 상호 운용할 수 있는 서비스 만들기
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 46e2d925dfe431957198b1d53b40d28adf6fb1c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646181"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="9eab2-103">WS-I Basic Profile 1.1 상호 운용할 수 있는 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="9eab2-103">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>

<span data-ttu-id="9eab2-104">ASP.NET 웹 서비스 클라이언트와 상호 운용할 수 있도록 WCF 서비스 끝점을 구성 하려면:</span><span class="sxs-lookup"><span data-stu-id="9eab2-104">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="9eab2-105"><xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 형식을 서비스 엔드포인트의 바인딩 형식으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-105">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="9eab2-106">서비스 엔드포인트에서 콜백 및 세션 계약 기능이나 트랜잭션 동작을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-106">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="9eab2-107">바인딩에서 HTTPS 및 전송 수준 클라이언트 인증에 대한 지원을 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-107">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="9eab2-108"><xref:System.ServiceModel.BasicHttpBinding> 클래스의 다음 기능에는 WS-I Basic Profile 1.1 이상의 기능이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-108">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="9eab2-109"><xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 속성을 사용하여 제어하는 MTOM(Message Transmission Optimization Mechanism) 메시지 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-109">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9eab2-110">MTOM을 사용하지 않으려면 이 속성을 기본값인 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-110">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="9eab2-111"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 값을 사용하여 제어하는 메시지 보안에서는 WS-I Basic Security Profile 1.0과 호환되는 WS-Security를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-111">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="9eab2-112">WS-Security를 사용하지 않으려면 이 속성을 기본값인 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-112">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="9eab2-113">WCF 서비스에 대 한 메타 데이터를 ASP.NET에서 사용할 수 있도록 하려면 웹 서비스 클라이언트 생성 도구 [(웹 서비스 기술 언어 도구 (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), 웹 [서비스 검색 도구 (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))및 Visual Studio의 **웹 참조 추가** 기능)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-113">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="9eab2-114">메타 데이터 게시를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-114">Enable metadata publication.</span></span> <span data-ttu-id="9eab2-115">자세한 내용은 [메타 데이터 끝점 게시](publishing-metadata-endpoints.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9eab2-115">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eab2-116">예제</span><span class="sxs-lookup"><span data-stu-id="9eab2-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9eab2-117">Description</span><span class="sxs-lookup"><span data-stu-id="9eab2-117">Description</span></span>  

 <span data-ttu-id="9eab2-118">다음 예제 코드에서는 ASP.NET 웹 서비스 클라이언트와 호환 되는 WCF 끝점을 코드에서, 또는 구성 파일에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9eab2-118">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9eab2-119">코드</span><span class="sxs-lookup"><span data-stu-id="9eab2-119">Code</span></span>  

 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9eab2-120">참조</span><span class="sxs-lookup"><span data-stu-id="9eab2-120">See also</span></span>

- [<span data-ttu-id="9eab2-121">ASP.NET 웹 서비스와의 상호 운용성</span><span class="sxs-lookup"><span data-stu-id="9eab2-121">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
