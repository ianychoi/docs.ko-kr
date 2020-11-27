---
title: 메타데이터 엔드포인트 게시
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249763"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="57772-102">메타데이터 엔드포인트 게시</span><span class="sxs-lookup"><span data-stu-id="57772-102">Publishing Metadata Endpoints</span></span>

<span data-ttu-id="57772-103">WCF (Windows Communication Foundation) 서비스는 하나 이상의 메타 데이터 끝점을 게시 하 여 메타 데이터를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="57772-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="57772-104">서비스 메타데이터를 게시하면 WS-MetadataExchange(MEX) 및 HTTP/GET 요청과 같이 표준화된 프로토콜을 통해 메타데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57772-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="57772-105">메타데이터 엔드포인트는 주소, 바인딩 및 계약에 포함된 다른 서비스 엔드포인트와 유사하며 구성 또는 코드를 통해 서비스 호스트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57772-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="57772-106">메타데이터 엔드포인트 게시를 사용하도록 설정하려면 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 서비스 동작을 서비스에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57772-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57772-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="57772-107">In This Section</span></span>  

 [<span data-ttu-id="57772-108">방법: 구성 파일을 사용하여 서비스에 대한 메타데이터 게시</span><span class="sxs-lookup"><span data-stu-id="57772-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="57772-109">클라이언트에서 쿼리 문자열을 사용 하 여 WS-MetadataExchange 또는 HTTP/GET 요청을 사용 하 여 메타 데이터를 검색할 수 있도록 WCF 서비스에서 메타 데이터를 게시 하도록 구성 하는 방법을 보여 줍니다 `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="57772-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="57772-110">방법: 코드를 사용하여 서비스에 대한 메타데이터 게시</span><span class="sxs-lookup"><span data-stu-id="57772-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="57772-111">클라이언트에서 쿼리 문자열을 사용 하 여 WS-MetadataExchange 또는 HTTP/GET 요청을 사용 하 여 메타 데이터를 검색할 수 있도록 코드에서 WCF 서비스에 대 한 메타 데이터 게시를 사용 하도록 설정 하는 방법을 보여 줍니다 `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="57772-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57772-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57772-112">See also</span></span>

- [<span data-ttu-id="57772-113">메타데이터 게시</span><span class="sxs-lookup"><span data-stu-id="57772-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
