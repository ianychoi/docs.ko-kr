---
description: '자세한 정보: 방법: 서비스 끝점으로 메타 데이터 가져오기'
title: '방법: 서비스 엔드포인트로 메타데이터 가져오기'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: d6e69b64c5f70a8e49ed6ee7c9ff319f5a639a30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793742"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="49c6e-103">방법: 서비스 엔드포인트로 메타데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="49c6e-103">How to: Import Metadata into Service Endpoints</span></span>

<span data-ttu-id="49c6e-104">이 항목에서는 서비스 끝점 컬렉션에 메타 데이터를 가져오고 [시작](../samples/getting-started-sample.md)에 정의 된 서비스를 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-104">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="49c6e-105">이 항목에서는 서비스에서 메타데이터를 가져온 다음 서비스에 `Add` 메서드를 호출하는 클라이언트 애플리케이션을 만든 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-105">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="49c6e-106">서비스 엔드포인트로 메타데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="49c6e-106">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="49c6e-107"><xref:System.ServiceModel.EndpointAddress> 개체를 선언하고 URI(Uniform Resource Identifier)를 사용하여 서비스의 MEX(메타데이터 교환) 주소에 대해 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-107">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="49c6e-108">MEX 주소를 전달하여 <xref:System.ServiceModel.Description.MetadataExchangeClient>를 만들고 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-108">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="49c6e-109">그러면 서비스에서 메타데이터가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-109">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="49c6e-110">이전에 검색한 메타데이터를 전달하여 <xref:System.ServiceModel.Description.WsdlImporter>를 만들고 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-110">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="49c6e-111">그러면 <xref:System.ServiceModel.Description.ContractDescription> 개체 컬렉션이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-111">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="49c6e-112">필요에 따라 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> 또는 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-112">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="49c6e-113">메타데이터를 가져온 후에는 클라이언트 채널을 만들거나 메타데이터를 내보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-113">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="49c6e-114">이 시점에는 형식 정보를 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-114">This is because no type information is available at this point.</span></span> <span data-ttu-id="49c6e-115">실제로 서비스와 상호 작용하거나 메타데이터를 내보내려면 형식 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-115">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="49c6e-116">형식 정보를 생성하려면 4단계와 5단계에 표시된 코드를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-116">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="49c6e-117">또는 <xref:System.ServiceModel.Description.MetadataResolver> 도우미 클래스를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-117">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="49c6e-118">자세한 내용은 [방법: MetadataResolver를 사용 하 여 동적으로 바인딩 메타 데이터 가져오기](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49c6e-118">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="49c6e-119">각 계약에 대해 형식 정보를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-119">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="49c6e-120">이제 이 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-120">Now you can use this information.</span></span> <span data-ttu-id="49c6e-121">다음 샘플에서는 C# 소스 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="49c6e-121">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="49c6e-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49c6e-122">See also</span></span>

- [<span data-ttu-id="49c6e-123">메타데이터</span><span class="sxs-lookup"><span data-stu-id="49c6e-123">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="49c6e-124">시작</span><span class="sxs-lookup"><span data-stu-id="49c6e-124">Getting Started</span></span>](../samples/getting-started-sample.md)
