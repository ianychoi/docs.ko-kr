---
description: '자세한 정보: Internet Explorer 및 WCF에서 수행 하는 서비스 인증서 유효성 검사 간의 차이점'
title: Internet Explorer와 WCF로 완료된 서비스 인증서 유효성 검사의 차이점
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 2d635aec0949ec4e65cd965089206bbf6d6815a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756359"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="4484b-103">Internet Explorer와 WCF로 완료된 서비스 인증서 유효성 검사의 차이점</span><span class="sxs-lookup"><span data-stu-id="4484b-103">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>

<span data-ttu-id="4484b-104">HTTPS를 사용 하는 경우 Internet Explorer와 Windows Communication Foundation (WCF) 서비스 인증서의 유효성을 검사 하는 방법의 차이로 인해 WCF 클라이언트가 서비스 끝점에 메시지를 성공적으로 보낼 수 있는 경우에도 Internet Explorer가 서비스의 도움말 페이지 또는 WSDL (Web Services Description Language)에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4484b-104">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="4484b-105">이는 Internet Explorer는 서비스 인증서가 `ServerAuthentication` 향상 된 사용 플래그에 OID (개체 식별자)를 포함 하는지 여부를 확인 하는 반면 WCF는 이러한 제약 조건을 적용 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4484b-105">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="4484b-106">Internet Explorer가 서비스 도움말 페이지 또는 서비스에 대 한 WSDL에 액세스할 수 없는 경우 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 서비스 메타 데이터에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="4484b-106">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4484b-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4484b-107">See also</span></span>

- [<span data-ttu-id="4484b-108">HTTPS, TCP를 통한 SSL 및 SOAP 보안의 인증서 유효성 검사 차이점</span><span class="sxs-lookup"><span data-stu-id="4484b-108">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="4484b-109">방법: 메타데이터 검색 및 규정 준수 서비스 구현</span><span class="sxs-lookup"><span data-stu-id="4484b-109">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
