---
description: '자세한 정보: WCF 웹 HTTP 오류 처리'
title: WCF 웹 HTTP 오류 처리
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 88483c249bc1b6b866517ca10b348c0885fc34fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779481"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="91309-103">WCF 웹 HTTP 오류 처리</span><span class="sxs-lookup"><span data-stu-id="91309-103">WCF Web HTTP Error Handling</span></span>

<span data-ttu-id="91309-104">WCF (Windows Communication Foundation) 웹 HTTP 오류 처리를 사용 하면 HTTP 상태 코드를 지정 하 고 작업과 동일한 형식 (예: XML 또는 JSON)을 사용 하 여 오류 정보를 반환 하는 WCF 웹 HTTP 서비스에서 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91309-104">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="91309-105">WCF 웹 HTTP 오류 처리</span><span class="sxs-lookup"><span data-stu-id="91309-105">WCF Web HTTP Error Handling</span></span>  

 <span data-ttu-id="91309-106"><xref:System.ServiceModel.Web.WebFaultException> 클래스는 HTTP 상태 코드를 지정할 수 있도록 하는 생성자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="91309-106">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="91309-107">이 상태 코드는 나중에 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="91309-107">This status code is then returned to the client.</span></span> <span data-ttu-id="91309-108"><xref:System.ServiceModel.Web.WebFaultException> 클래스의 제네릭 버전인 <xref:System.ServiceModel.Web.WebFaultException%601>을 사용하면 발생한 오류에 대한 정보가 들어 있는 사용자 정의 형식을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91309-108">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="91309-109">이 사용자 지정 개체는 작업에 지정된 형식을 사용하여 serialize되고 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="91309-109">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="91309-110">다음 예제에서는 HTTP 상태 코드를 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="91309-110">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="91309-111">다음 예제에서는 HTTP 상태 코드와 추가 정보를 사용자 정의 형식에 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91309-111">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="91309-112">`MyErrorDetail`은 발생한 오류에 대한 추가 정보를 포함하는 사용자 정의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="91309-112">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="91309-113">위의 코드에서는 사용할 수 없음 상태 코드 및 `MyErrorDetails` 개체의 인스턴스가 포함된 본문과 함께 HTTP 응답을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="91309-113">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="91309-114">`MyErrorDetails` 개체의 형식은 다음에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="91309-114">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="91309-115">서비스 작업에 지정된 `ResponseFormat` 또는 <xref:System.ServiceModel.Web.WebGetAttribute> 특성의 <xref:System.ServiceModel.Web.WebInvokeAttribute> 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="91309-115">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="91309-116"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>의 값</span><span class="sxs-lookup"><span data-stu-id="91309-116">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="91309-117"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>에 액세스하는 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 속성의 값</span><span class="sxs-lookup"><span data-stu-id="91309-117">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="91309-118">이러한 값이 작업 서식 지정에 미치는 영향에 대 한 자세한 내용은 [WCF 웹 HTTP 형식 지정](wcf-web-http-formatting.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="91309-118">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="91309-119"><xref:System.ServiceModel.Web.WebFaultException>은 <xref:System.ServiceModel.FaultException>이므로 SOAP 엔드포인트와 웹 HTTP 엔드포인트를 둘 다 노출하는 서비스의 오류 예외 프로그래밍 모델로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91309-119"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91309-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91309-120">See also</span></span>

- [<span data-ttu-id="91309-121">WCF 웹 HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="91309-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="91309-122">WCF 웹 HTTP 형식 지정</span><span class="sxs-lookup"><span data-stu-id="91309-122">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="91309-123">오류 정의 및 지정</span><span class="sxs-lookup"><span data-stu-id="91309-123">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="91309-124">예외 및 오류 처리</span><span class="sxs-lookup"><span data-stu-id="91309-124">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="91309-125">오류 보내기 및 받기</span><span class="sxs-lookup"><span data-stu-id="91309-125">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
