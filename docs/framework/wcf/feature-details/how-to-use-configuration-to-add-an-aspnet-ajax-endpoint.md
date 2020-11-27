---
title: '방법: 구성을 사용하여 ASP.NET AJAX 엔드포인트 추가'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: b229173381eed3e821a9ad9e1a6639912521731c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268432"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="ba5cc-102">방법: 구성을 사용하여 ASP.NET AJAX 엔드포인트 추가</span><span class="sxs-lookup"><span data-stu-id="ba5cc-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>

<span data-ttu-id="ba5cc-103">WCF (Windows Communication Foundation)를 사용 하면 클라이언트 웹 사이트의 JavaScript에서 호출할 수 있는 ASP.NET AJAX 사용 끝점을 사용할 수 있도록 하는 서비스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="ba5cc-104">이러한 끝점을 만들려면 다른 모든 WCF (Windows Communication Foundation) 끝점과 마찬가지로 구성 파일을 사용 하거나 구성 요소가 필요 하지 않은 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="ba5cc-105">이 항목에서는 구성 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="ba5cc-106">서비스 끝점이 ASP.NET 될 수 있도록 하는 프로시저의 부분은를 사용 하 <xref:System.ServiceModel.WebHttpBinding> 고 끝점 동작을 추가 하기 위해 끝점을 구성 하는 것으로 구성 됩니다 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="ba5cc-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="ba5cc-107">끝점을 구성한 후 서비스를 구현 하 고 호스트 하는 단계는 모든 WCF 서비스에서 사용 하는 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="ba5cc-108">작업 예제는 [HTTP POST를 사용 하는 AJAX 서비스](../samples/ajax-service-using-http-post.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-108">For a working example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="ba5cc-109">구성을 사용 하지 않고 ASP.NET AJAX 끝점을 구성 하는 방법에 대 한 자세한 내용은 [방법: 구성을 사용 하지 않고 ASP.NET Ajax 끝점 추가](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="ba5cc-110">기본 WCF 서비스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ba5cc-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="ba5cc-111">특성으로 표시 된 인터페이스를 사용 하 여 기본 WCF 서비스 계약을 정의 <xref:System.ServiceModel.ServiceContractAttribute> 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="ba5cc-112">각 작업을 <xref:System.ServiceModel.OperationContractAttribute>로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="ba5cc-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="ba5cc-114">`ICalculator`를 사용하여 `CalculatorService` 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="ba5cc-115">네임스페이스 블록에 `ICalculator` 및 `CalculatorService` 구현을 래핑하여 이러한 구현에 대한 네임스페이스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="ba5cc-116">서비스에 대한 ASP.NET AJAX 엔드포인트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ba5cc-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="ba5cc-117">동작 구성을 만들고 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) 서비스의 AJAX 사용 ASP.NET 끝점에 대 한 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-117">Create a behavior configuration and specify the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="ba5cc-118">이전 단계에서 정의한 <xref:System.ServiceModel.WebHttpBinding> 및 ASP.NET AJAX 동작을 사용하는 서비스에 대한 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="ba5cc-119">IIS에서 서비스를 호스팅하려면</span><span class="sxs-lookup"><span data-stu-id="ba5cc-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="ba5cc-120">IIS에서 서비스를 호스팅하려면 애플리케이션에서 .svc 확장명을 가진 새 파일 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="ba5cc-121">서비스에 대 한 적절 한 [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) 지시문 정보를 추가 하 여이 파일을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-121">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="ba5cc-122">예를 들어 `CalculatorService` 샘플에 대한 서비스 파일의 내용에는 다음 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="ba5cc-123">IIS에서 호스트 하는 방법에 대 한 자세한 내용은 [방법: iis에서 WCF 서비스](how-to-host-a-wcf-service-in-iis.md)호스팅을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="ba5cc-124">서비스를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="ba5cc-124">To call the service</span></span>  
  
1. <span data-ttu-id="ba5cc-125">끝점은 .svc 파일을 기준으로 하는 빈 주소에 구성 되어 있으므로 서비스를 사용할 수 있으며, 서비스에 대 한 요청을 전송 하 여 호출할 수 있습니다. \<operation> 예를 들어 작업에 대해 서비스 .svc/Add를 사용할 수 있습니다. `Add`</span><span class="sxs-lookup"><span data-stu-id="ba5cc-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="ba5cc-126">엔드포인트 URL을 ASP.NET AJAX Script Manager 컨트롤의 스크립트 컬렉션에 입력하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="ba5cc-127">예제는 [HTTP POST를 사용 하는 AJAX 서비스](../samples/ajax-service-using-http-post.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba5cc-127">For an example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5cc-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba5cc-128">See also</span></span>

- [<span data-ttu-id="ba5cc-129">ASP.NET AJAX용 WCF 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="ba5cc-129">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="ba5cc-130">방법: AJAX 사용 ASP.NET 웹 서비스를 WCF로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="ba5cc-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
