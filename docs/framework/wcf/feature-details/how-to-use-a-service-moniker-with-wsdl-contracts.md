---
description: '자세히 알아보기: 방법: WSDL 계약을 통해 서비스 모니커 사용'
title: '방법: WSDL 계약을 통해 서비스 모니커 사용'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70a8ef0258cd8490d8e14b6a80e8de0248fa0ae2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734375"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="8a20d-103">방법: WSDL 계약을 통해 서비스 모니커 사용</span><span class="sxs-lookup"><span data-stu-id="8a20d-103">How to: Use a Service Moniker with WSDL Contracts</span></span>

<span data-ttu-id="8a20d-104">완전히 독립된 COM Interop 클라이언트가 필요한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-104">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="8a20d-105">호출하려는 서비스에서 MEX 엔드포인트를 노출하지 않을 수도 있고 WCF 클라이언트 DLL이 COM interop에 등록되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-105">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="8a20d-106">이 경우 서비스를 설명하는 WSDL 파일을 만들어 WCF 서비스 모니커에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-106">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="8a20d-107">이 항목에서는 WCF WSDL 모니커를 사용하여 WCF 시작 샘플을 호출하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-107">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="8a20d-108">WSDL 서비스 모니커 사용</span><span class="sxs-lookup"><span data-stu-id="8a20d-108">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="8a20d-109">GettingStarted 샘플 솔루션을 열고 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-109">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="8a20d-110">Internet Explorer를 열고로 이동 하 여 `http://localhost/ServiceModelSamples/Service.svc` 서비스가 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-110">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="8a20d-111">Service.cs 파일에서 CalculatorService 클래스에 다음 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-111">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="8a20d-112">서비스 App.config에 바인딩 네임스페이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-112">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="8a20d-113">애플리케이션에서 읽을 WSDL 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-113">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="8a20d-114">3 단계와 4 단계에서 네임 스페이스를 추가 했으므로 IE를 사용 하 여로 이동 하 여 서비스의 전체 WSDL 설명을 쿼리할 수 있습니다 `http://localhost/ServiceModelSamples/Service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="8a20d-114">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="8a20d-115">그런 다음 Internet Explorer에서 serviceWSDL.xml로 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-115">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="8a20d-116">3단계와 4단계에서 네임스페이스를 지정하지 않은 경우 위 URL을 쿼리했을 때 반환되는 WSDL 문서는 전체 WSDL이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-116">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="8a20d-117">반환되는 WSDL 문서에는 다른 WSDL 문서를 가져오는 몇 개의 import 문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-117">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="8a20d-118">각 import 문을 수행하고 전체 WSDL 문서를 빌드하여 서비스에서 반환되는 WSDL과 가져온 WSDL을 결합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-118">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="8a20d-119">Visual Basic 6.0을 열고 새 표준 .exe 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-119">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8a20d-120">폼에 단추를 추가하고 단추를 두 번 클릭하여 다음 코드를 클릭 처리기에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-120">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > 모니커의 형식이 잘못되었거나 서비스를 사용할 수 없는 경우 `GetObject`를 호출하면 "구문이 잘못되었습니다."라는 오류가 반환됩니다.  <span data-ttu-id="8a20d-122">이 오류가 발생하면 사용하고 있는 모니커가 올바르고 서비스를 사용할 수 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8a20d-122">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="8a20d-123">Visual Basic 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-123">Run the Visual Basic application.</span></span> <span data-ttu-id="8a20d-124">Subtract(145, 76.54)를 호출한 결과가 표시된 메시지 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8a20d-124">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a20d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a20d-125">See also</span></span>

- [<span data-ttu-id="8a20d-126">시작</span><span class="sxs-lookup"><span data-stu-id="8a20d-126">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="8a20d-127">COM 애플리케이션과 통합 개요</span><span class="sxs-lookup"><span data-stu-id="8a20d-127">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
