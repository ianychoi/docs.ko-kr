---
description: '방법: 피드를 Atom 및 RSS로 노출 하는 방법에 대해 자세히 알아보세요.'
title: '방법: Atom 및 RSS로 피드 공개'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 5afe08b2c1d9fc687563e124061fe7fb59257180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793781"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="8929b-103">방법: Atom 및 RSS로 피드 공개</span><span class="sxs-lookup"><span data-stu-id="8929b-103">How to: Expose a Feed as Both Atom and RSS</span></span>

<span data-ttu-id="8929b-104">WCF (Windows Communication Foundation)를 사용 하 여 배포 피드를 노출 하는 서비스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-104">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="8929b-105">이 항목에서는 Atom 1.0 및 RSS 2.0을 사용하여 배포 피드를 노출하는 배포 서비스를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-105">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="8929b-106">이 서비스는 배포 형식 중 하나를 반환할 수 있는 하나의 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-106">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="8929b-107">편의를 위해 이 샘플에서 사용되는 서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-107">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="8929b-108">프로덕션 환경에서 이 형식의 서비스는 IIS 또는 WAS에서 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-108">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="8929b-109">여러 WCF 호스팅 옵션에 대 한 자세한 내용은 [호스팅](hosting.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8929b-109">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="8929b-110">기본 배포 서비스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="8929b-110">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="8929b-111"><xref:System.ServiceModel.Web.WebGetAttribute> 특성으로 표시된 인터페이스를 사용하여 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-111">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="8929b-112">배포 피드로 노출된 각 작업은 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-112">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="8929b-113"><xref:System.ServiceModel.Web.WebGetAttribute>의 매개 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-113">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="8929b-114">`UriTemplate`은 이 서비스 작업을 호출하는 데 사용되는 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-114">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="8929b-115">이 매개 변수에 대 한 문자열에는 리터럴과 중괄호 ({*format*})의 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-115">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="8929b-116">이 변수는 서비스 작업의 `format` 매개 변수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-116">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="8929b-117">자세한 내용은 <xref:System.UriTemplate>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8929b-117">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="8929b-118">`BodyStyle`은 이 서비스 작업이 보내고 받는 메시지가 작성되는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-118">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="8929b-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>는 이 서비스 작업에서 보내거나 받은 데이터가 인프라 정의 XML 요소로 래핑되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-119"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="8929b-120">자세한 내용은 <xref:System.ServiceModel.Web.WebMessageBodyStyle>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8929b-120">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="8929b-121"><xref:System.ServiceModel.ServiceKnownTypeAttribute>를 사용하여 이 인터페이스의 서비스 작업에서 반환하는 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-121">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="8929b-122">서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-122">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="8929b-123"><xref:System.ServiceModel.Syndication.SyndicationFeed> 개체를 만들고 만든 이, 범주 및 설명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-123">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="8929b-124">여러 <xref:System.ServiceModel.Syndication.SyndicationItem> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-124">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="8929b-125"><xref:System.ServiceModel.Syndication.SyndicationItem> 개체를 피드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-125">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="8929b-126">형식 매개 변수를 사용하여 요청된 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-126">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="8929b-127">서비스를 호스트하려면</span><span class="sxs-lookup"><span data-stu-id="8929b-127">To host the service</span></span>  
  
1. <span data-ttu-id="8929b-128"><xref:System.ServiceModel.Web.WebServiceHost> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-128">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="8929b-129">ph x="1" /&gt; 클래스는 코드 또는 구성에 엔드포인트가 지정되어 있지 않으면 서비스 기준 주소에 엔드포인트를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-129">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="8929b-130">이 샘플에서는 엔드포인트가 지정되어 있지 않으므로 기본 엔드포인트가 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-130">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="8929b-131">서비스 호스트를 열고 서비스에서 피드를 로드하여 피드를 표시한 다음 사용자가 Enter 키를 누를 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-131">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="8929b-132">HTTP GET을 사용하여 GetBlog를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="8929b-132">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="8929b-133">Internet Explorer를 열고 다음 URL을 입력 하 고 ENTER 키를 `http://localhost:8000/BlogService/GetBlog` 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-133">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="8929b-134">URL에는 서비스의 기준 주소 ( `http://localhost:8000/BlogService` ), 끝점의 상대 주소 및 호출할 서비스 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-134">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="8929b-135">코드에서 GetBlog()를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="8929b-135">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="8929b-136">기본 주소 및 호출할 메서드를 사용하여 <xref:System.Xml.XmlReader>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="8929b-137">지금 만든 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>를 전달하는 정적 <xref:System.Xml.XmlReader> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="8929b-138">이렇게 하면 서비스 작업이 호출되고 서비스 작업에서 반환된 포맷터로 새 <xref:System.ServiceModel.Syndication.SyndicationFeed>가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="8929b-139">피드 개체에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="8929b-140">예제</span><span class="sxs-lookup"><span data-stu-id="8929b-140">Example</span></span>  

 <span data-ttu-id="8929b-141">다음은 이 예제에 해당되는 전체 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8929b-142">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="8929b-142">Compiling the Code</span></span>  

 <span data-ttu-id="8929b-143">앞의 코드를 컴파일할 때 System.ServiceModel.dll 및 System.ServiceModel.Web.dll을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="8929b-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8929b-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8929b-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
