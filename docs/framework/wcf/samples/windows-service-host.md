---
description: '자세한 정보: Windows 서비스 호스트'
title: Windows Service 호스트
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 529256675723e556879b8380f514ab1b0a5b7f8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715134"
---
# <a name="windows-service-host"></a><span data-ttu-id="dd003-103">Windows Service 호스트</span><span class="sxs-lookup"><span data-stu-id="dd003-103">Windows Service Host</span></span>

<span data-ttu-id="dd003-104">이 샘플에서는 관리 되는 Windows 서비스에서 호스팅되는 WCF (Windows Communication Foundation) 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-104">This sample demonstrates a Windows Communication Foundation (WCF) service hosted in a managed Windows Service.</span></span> <span data-ttu-id="dd003-105">Windows 서비스는 **제어판** 의 서비스 애플릿을 사용 하 여 제어 되며 시스템을 다시 부팅 한 후 자동으로 시작 되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-105">Windows Services are controlled using the Services applet in **Control Panel** and can be configured to start up automatically after a system reboot.</span></span> <span data-ttu-id="dd003-106">이 샘플은 클라이언트 프로그램과 Windows 서비스 프로그램으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-106">The sample consists of a client program and an Windows Service program.</span></span> <span data-ttu-id="dd003-107">서비스는 .exe 프로그램으로 구현되고 자체 호스팅 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-107">The service is implemented as an .exe program and contains its own hosting code.</span></span> <span data-ttu-id="dd003-108">WAS(Windows Process Activation Services) 또는 IIS(인터넷 정보 서비스) 등의 다른 호스팅 환경에서는 직접 호스팅 코드를 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-108">In other hosting environments, such as Windows Process Activation Services (WAS) or Internet Information Services (IIS), it is not necessary for you to write hosting code.</span></span>

> [!NOTE]
> <span data-ttu-id="dd003-109">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd003-110">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dd003-111">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="dd003-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dd003-112">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd003-113">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 <span data-ttu-id="dd003-114">이 서비스를 빌드한 후에는 다른 Windows 서비스와 마찬가지로 Installutil.exe 유틸리티로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-114">After building this service, it must be installed with the Installutil.exe utility like any other Windows Service.</span></span> <span data-ttu-id="dd003-115">서비스를 변경하려는 경우에는 먼저 `installutil /u`를 사용하여 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-115">If you are going to make changes to the service, you must first uninstall it with `installutil /u`.</span></span> <span data-ttu-id="dd003-116">이 샘플에 포함된 Setup.bat 및 Cleanup.bat 파일은 Windows 서비스를 설치 및 시작하기 위한 명령과 Windows 서비스를 종료 및 제거하기 위한 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-116">The Setup.bat and Cleanup.bat files included in this sample are the commands to install and start up the Windows Service, and to shut down and uninstall the Windows Service.</span></span> <span data-ttu-id="dd003-117">WCF 서비스는 Windows 서비스가 실행 중인 경우에만 클라이언트에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-117">The WCF service can only respond to clients if the Windows Service is running.</span></span> <span data-ttu-id="dd003-118">**제어판** 에서 서비스 애플릿을 사용 하 여 Windows 서비스를 중지 하 고 클라이언트를 실행 하는 경우 <xref:System.ServiceModel.EndpointNotFoundException> 클라이언트가 서비스에 액세스 하려고 하면 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-118">If you stop the Windows Service by using the Services applet from **Control Panel** and run the client, a <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="dd003-119">Windows 서비스를 다시 시작하고 클라이언트를 다시 실행하면 통신이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-119">If you restart the Windows Service and rerun the client, communication succeeds.</span></span>  
  
 <span data-ttu-id="dd003-120">서비스 코드에는 설치 관리자 클래스, ICalculator 계약을 구현 하는 WCF 서비스 구현 클래스 및 런타임 호스트 역할을 하는 Windows 서비스 클래스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-120">The service code includes an installer class, a WCF service implementation class which implements the ICalculator contract, and a Windows Service class that acts as the run-time host.</span></span> <span data-ttu-id="dd003-121"><xref:System.Configuration.Install.Installer>에서 상속되는 설치 관리자 클래스를 사용하면 프로그램을 Installutil.exe 도구를 통해 NT 서비스로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-121">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as an NT service by the Installutil.exe tool.</span></span> <span data-ttu-id="dd003-122">서비스 구현 클래스인는 `WcfCalculatorService` 기본 서비스 계약을 구현 하는 WCF 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-122">The service implementation class, `WcfCalculatorService`, is an WCF service that implements a basic service contract.</span></span> <span data-ttu-id="dd003-123">이 WCF 서비스는 라는 Windows 서비스 클래스 내에서 호스팅됩니다 `WindowsCalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="dd003-123">This WCF service is hosted inside a Windows Service class called `WindowsCalculatorService`.</span></span> <span data-ttu-id="dd003-124">Windows 서비스로 정규화하기 위해 클래스가 <xref:System.ServiceProcess.ServiceBase>에서 상속되고 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 및 <xref:System.ServiceProcess.ServiceBase.OnStop> 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-124">To qualify as a Windows Service, the class inherits from <xref:System.ServiceProcess.ServiceBase> and implements the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> and <xref:System.ServiceProcess.ServiceBase.OnStop> methods.</span></span> <span data-ttu-id="dd003-125"><xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>에서 <xref:System.ServiceModel.ServiceHost> 개체가 `WcfCalculatorService` 형식에 대해 만들어지고 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-125">In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, a <xref:System.ServiceModel.ServiceHost> object is created for the `WcfCalculatorService` type and opened.</span></span> <span data-ttu-id="dd003-126"><xref:System.ServiceProcess.ServiceBase.OnStop>에서 ServiceHost는 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 개체의 <xref:System.ServiceModel.ServiceHost> 메서드를 호출하여 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-126">In <xref:System.ServiceProcess.ServiceBase.OnStop>, the ServiceHost is closed by calling the <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> method of the <xref:System.ServiceModel.ServiceHost> object.</span></span> <span data-ttu-id="dd003-127">호스트의 기본 주소는 요소를 사용 하 여 구성 됩니다. 요소는 요소의 자식인 요소의 자식인 [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) 의 자식입니다 [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) .</span><span class="sxs-lookup"><span data-stu-id="dd003-127">The host's base address is configured using the [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, which is a child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), which is a child of the [\<host>](../../configure-apps/file-schema/wcf/host.md) element, which is a child of the [\<service>](../../configure-apps/file-schema/wcf/service.md) element.</span></span>  
  
 <span data-ttu-id="dd003-128">정의 된 끝점은 기본 주소와를 사용 합니다 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dd003-128">The endpoint that is defined uses the base address and a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="dd003-129">다음 샘플에서는 CalculatorService를 노출시키는 엔드포인트와 기본 주소의 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-129">The following sample shows the configuration of the base address as well as the endpoint that exposes the CalculatorService.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 <span data-ttu-id="dd003-130">샘플을 실행하면 작업 요청 및 응답이 서비스와 클라이언트 콘솔 창 모두에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-130">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="dd003-131">서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-131">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dd003-132">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="dd003-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dd003-133">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dd003-134">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dd003-135">솔루션을 빌드한 후에는 Installutil.exe 도구를 사용 하 여 Windows 서비스를 설치 하기 위해 관리자 권한 Visual Studio 2012 명령 프롬프트에서 Setup.bat를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-135">After the solution has been built, run Setup.bat from an elevated Visual Studio 2012 command prompt to install the Windows service using the Installutil.exe tool.</span></span> <span data-ttu-id="dd003-136">서비스가 서비스에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd003-136">The service should appear in Services.</span></span>  
  
4. <span data-ttu-id="dd003-137">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="dd003-137">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd003-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd003-138">See also</span></span>

- <span data-ttu-id="dd003-139">[AppFabric 호스팅 및 지속성 샘플](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="dd003-139">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
