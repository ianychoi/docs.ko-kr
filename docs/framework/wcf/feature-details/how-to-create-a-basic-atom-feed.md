---
title: '방법: 기본 Atom 피드 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 76362684d289ca6aaac852158a05087a0a28f837
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254053"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="d1ea7-102">방법: 기본 Atom 피드 만들기</span><span class="sxs-lookup"><span data-stu-id="d1ea7-102">How to: Create a Basic Atom Feed</span></span>

<span data-ttu-id="d1ea7-103">WCF (Windows Communication Foundation)를 사용 하 여 배포 피드를 노출 하는 서비스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="d1ea7-104">이 항목에서는 Atom 배포 피드를 노출하는 배포 서비스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="d1ea7-105">기본 배포 서비스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d1ea7-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="d1ea7-106"><xref:System.ServiceModel.Web.WebGetAttribute> 특성으로 표시된 인터페이스를 사용하여 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="d1ea7-107">배포 피드로 노출된 각 작업은 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> 개체를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="d1ea7-108"><xref:System.ServiceModel.Web.WebGetAttribute>를 적용하는 모든 서비스 작업은 HTTP GET 요청에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="d1ea7-109">작업을 다른 HTTP 메서드에 매핑하려면 <xref:System.ServiceModel.Web.WebInvokeAttribute>를 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="d1ea7-110">자세한 내용은 [방법: 기본 WCF 웹 HTTP 서비스 만들기](how-to-create-a-basic-wcf-web-http-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="d1ea7-111">서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="d1ea7-112"><xref:System.ServiceModel.Syndication.SyndicationFeed> 개체를 만들고 만든 이, 범주 및 설명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="d1ea7-113">여러 <xref:System.ServiceModel.Syndication.SyndicationItem> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="d1ea7-114"><xref:System.ServiceModel.Syndication.SyndicationItem> 개체를 피드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="d1ea7-115">피드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="d1ea7-116">서비스를 호스트하려면</span><span class="sxs-lookup"><span data-stu-id="d1ea7-116">To host the service</span></span>  
  
1. <span data-ttu-id="d1ea7-117"><xref:System.ServiceModel.Web.WebServiceHost> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="d1ea7-118">서비스 호스트를 열고 서비스에서 피드를 로드하여 피드를 표시한 다음 사용자가 Enter 키를 누를 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="d1ea7-119">HTTP GET을 사용하여 GetBlog()를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="d1ea7-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="d1ea7-120">Internet Explorer를 열고 다음 URL을 입력 하 고 enter 키를 누릅니다. `http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="d1ea7-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="d1ea7-121">URL에는 서비스의 기준 주소 ( `http://localhost:8000/BlogService` ), 끝점의 상대 주소 및 호출할 서비스 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="d1ea7-122">코드에서 GetBlog()를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="d1ea7-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="d1ea7-123">기본 주소 및 호출할 메서드를 사용하여 <xref:System.Xml.XmlReader>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="d1ea7-124">지금 만든 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>를 전달하는 정적 <xref:System.Xml.XmlReader> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="d1ea7-125">이렇게 하면 서비스 작업이 호출되고 서비스 작업에서 반환된 포맷터로 새 <xref:System.ServiceModel.Syndication.SyndicationFeed>가 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="d1ea7-126">피드 개체에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="d1ea7-127">예제</span><span class="sxs-lookup"><span data-stu-id="d1ea7-127">Example</span></span>  

 <span data-ttu-id="d1ea7-128">다음은 이 예제에 해당되는 전체 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1ea7-129">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="d1ea7-129">Compiling the Code</span></span>  

 <span data-ttu-id="d1ea7-130">앞의 코드를 컴파일할 때 System.ServiceModel.dll 및 System.ServiceModel.Web.dll을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ea7-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ea7-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1ea7-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
