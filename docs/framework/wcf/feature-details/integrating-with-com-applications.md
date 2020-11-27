---
title: COM 애플리케이션과 통합
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: bc58e22b64284d66367302d55b5c9554c9ec0d72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268237"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="f98cc-102">COM 애플리케이션과 통합</span><span class="sxs-lookup"><span data-stu-id="f98cc-102">Integrating with COM Applications</span></span>

<span data-ttu-id="f98cc-103">Wcf 서비스 모니커를 사용 하 여 WCF (Windows Communication Foundation) 서비스를 기존 코드에 직접 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="f98cc-104">서비스 모니커는 Office VBA, Visual Basic 6.0 또는 Visual C++ 6.0과 같은 다양한 범위의 COM 기반 개발 환경에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f98cc-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f98cc-105">In This Section</span></span>  

 [<span data-ttu-id="f98cc-106">COM 애플리케이션과 통합 개요</span><span class="sxs-lookup"><span data-stu-id="f98cc-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="f98cc-107">통합 프로세스의 주요 부분에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="f98cc-108">방법: 서비스 모니커 등록 및 구성</span><span class="sxs-lookup"><span data-stu-id="f98cc-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="f98cc-109">COM 응용 프로그램 내에서 WCF 서비스 모니커를 사용 하려면 필요한 특성 사용 형식을 COM에 등록 하 고 필요한 바인딩 구성을 사용 하 여 COM 응용 프로그램과 모니커를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="f98cc-110">방법: 등록하지 않고 Windows Communication Foundation 서비스 모니커 사용</span><span class="sxs-lookup"><span data-stu-id="f98cc-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="f98cc-111">WSDL(웹 서비스 기술 언어) 문서의 형태로 또는 WS-MetadataExchange 엔드포인트에서 계약 정의를 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="f98cc-112">방법: WSDL 계약을 통해 서비스 모니커 사용</span><span class="sxs-lookup"><span data-stu-id="f98cc-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="f98cc-113">WCF WSDL 모니커를 사용 하 여 WCF 샘플을 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="f98cc-114">방법: 메타데이터 교환 계약을 통해 서비스 모니커 사용</span><span class="sxs-lookup"><span data-stu-id="f98cc-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="f98cc-115">Mex 끝점을 지정 하는 WCF 모니커를 사용 하 여 WCF 샘플을 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="f98cc-116">방법: 채널 보안 자격 증명 지정</span><span class="sxs-lookup"><span data-stu-id="f98cc-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="f98cc-117">WCF 서비스 모니커는 `IChannelCredentials` 채널 자격 증명을 지정 하는 다양 한 다른 방법을 허용 하는 인터페이스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f98cc-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f98cc-118">참고</span><span class="sxs-lookup"><span data-stu-id="f98cc-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="f98cc-119">참조</span><span class="sxs-lookup"><span data-stu-id="f98cc-119">See also</span></span>

- [<span data-ttu-id="f98cc-120">COM + 응용 프로그램과 통합</span><span class="sxs-lookup"><span data-stu-id="f98cc-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
