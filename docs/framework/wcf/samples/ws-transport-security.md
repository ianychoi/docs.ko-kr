---
title: WS 전송 보안
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 64059a5a09d49f83c9abda5b2f3d1601acf41a3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252415"
---
# <a name="ws-transport-security"></a><span data-ttu-id="541e4-102">WS 전송 보안</span><span class="sxs-lookup"><span data-stu-id="541e4-102">WS Transport Security</span></span>

<span data-ttu-id="541e4-103">이 샘플에서는 <xref:System.ServiceModel.WSHttpBinding> 바인딩의 SSL 전송 보안을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="541e4-104">기본적으로 `wsHttpBinding` 바인딩은 HTTP 통신을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="541e4-105">전송 보안용으로 구성된 경우, 바인딩은 HTTPS 통신을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="541e4-106">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-106">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="541e4-107">`wsHttpBinding`은 클라이언트 및 서비스의 애플리케이션 구성 파일에 지정 및 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="541e4-108">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="541e4-109">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="541e4-110">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="541e4-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="541e4-111">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="541e4-112">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="541e4-113">샘플의 프로그램 코드는 [시작](getting-started-sample.md) 서비스의 코드와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-113">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="541e4-114">샘플을 빌드하고 실행하기 전에 Web Server Certificate Wizard를 사용하여 인증서를 만들고 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="541e4-115">구성 파일 설정의 엔드포인트 정의와 바인딩 정의를 사용하면 클라이언트의 다음 샘플 구성에 표시된 것과 같이 `Transport` 보안 모드를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="541e4-116">지정 된 주소에서 체계를 사용 합니다 `https://` .</span><span class="sxs-lookup"><span data-stu-id="541e4-116">The address specified uses the `https://` scheme.</span></span> <span data-ttu-id="541e4-117">바인딩 구성에서는 보안 모드를 `Transport`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="541e4-118">서비스의 Web.config 파일에도 같은 보안 모드를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="541e4-119">이 샘플에 사용 된 인증서는 Makecert.exe을 사용 하 여 만든 테스트 인증서 이므로 브라우저에서와 같은 https: 주소에 액세스 하려고 할 때 보안 경고가 나타납니다. `https://localhost/servicemodelsamples/service.svc`</span><span class="sxs-lookup"><span data-stu-id="541e4-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="541e4-120">WCF (Windows Communication Foundation) 클라이언트가 현재 위치의 테스트 인증서를 사용 하도록 허용 하기 위해 일부 추가 코드를 클라이언트에 추가 하 여 보안 경고를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="541e4-121">이 코드 및 함께 사용되는 클래스는 프로덕션 인증서를 사용할 때에는 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="541e4-122">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="541e4-123">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="541e4-124">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="541e4-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="541e4-125">다음 명령을 사용 하 여 ASP.NET 4.0을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="541e4-126">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="541e4-127">[인터넷 정보 서비스 (IIS) 서버 인증서 설치 지침](iis-server-certificate-installation-instructions.md)을 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="541e4-128">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="541e4-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="541e4-129">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="541e4-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
