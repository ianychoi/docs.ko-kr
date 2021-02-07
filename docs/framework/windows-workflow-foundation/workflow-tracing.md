---
description: '자세한 정보: 워크플로 추적'
title: 워크플로 추적
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 6d976cce1310a072f8d1c98db138696921b382c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754851"
---
# <a name="workflow-tracing"></a><span data-ttu-id="4b28b-103">워크플로 추적</span><span class="sxs-lookup"><span data-stu-id="4b28b-103">Workflow Tracing</span></span>

<span data-ttu-id="4b28b-104">워크플로 추적을 사용하면 .NET Framework 추적 수신기를 통해 진단 정보를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-104">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="4b28b-105">추적은 애플리케이션에서 문제가 발견되면 사용하도록 설정했다가 문제가 해결되면 다시 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-105">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="4b28b-106">워크플로에 대한 디버그 추적을 두 가지 방법으로 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-106">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="4b28b-107">이벤트 추적 뷰어를 사용하여 구성하거나 <xref:System.Diagnostics>를 사용하여 추적 이벤트를 파일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-107">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="4b28b-108">ETW에서 디버그 추적 사용</span><span class="sxs-lookup"><span data-stu-id="4b28b-108">Enabling Debug Tracing in ETW</span></span>  

 <span data-ttu-id="4b28b-109">ETW를 사용하여 추적을 활성화하려면 이벤트 뷰어에서 디버그 채널을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-109">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="4b28b-110">이벤트 뷰어에서 분석 및 디버그 로그 노드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-110">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="4b28b-111">이벤트 뷰어의 트리 뷰에서 **이벤트 뷰어 >응용 프로그램 및 서비스 로그->Microsoft >Windows->응용 프로그램 서버-응용** 프로그램으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-111">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="4b28b-112">**응용 프로그램 서버-응용 프로그램** 을 마우스 오른쪽 단추로 클릭 하 고 **보기->분석 및 디버그 로그 표시** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-112">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="4b28b-113">**디버그** 를 마우스 오른쪽 단추로 클릭 하 고 **로그 사용** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-113">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="4b28b-114">워크플로에서 디버그를 실행하고 추적을 ETW 디버그 채널로 내보낸 후 이벤트 뷰어에서 추적 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-114">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="4b28b-115">**이벤트 뷰어->응용 프로그램 및 서비스 로그->Microsoft >Windows->응용 프로그램 서버-응용** 프로그램으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-115">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="4b28b-116">**디버그** 를 마우스 오른쪽 단추로 클릭 하 고 **새로 고침** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-116">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="4b28b-117">기본 분석 추적 버퍼 크기는 겨우 4KB이므로 이 크기를 32KB로 늘리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-117">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="4b28b-118">이렇게 하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-118">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="4b28b-119">현재 프레임워크 디렉터리(예: C:\Windows\Microsoft.NET\Framework\v4.0.21203)에서 `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-119">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="4b28b-120">\<bufferSize>Windows ApplicationServer. man 파일의 값을 32로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-120">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="4b28b-121">현재 프레임워크 디렉터리(예: C:\Windows\Microsoft.NET\Framework\v4.0.21203)에서 `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-121">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b28b-122">.NET Framework 4 클라이언트 프로필을 사용 하는 경우 먼저 .NET Framework 4 디렉터리에서 다음 명령을 실행 하 여 ETW 매니페스트를 등록 해야 합니다. `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="4b28b-122">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="4b28b-123">System.Diagnostics를 사용하여 디버그 추적 활성화</span><span class="sxs-lookup"><span data-stu-id="4b28b-123">Enabling Debug Tracing using System.Diagnostics</span></span>  

 <span data-ttu-id="4b28b-124">이러한 수신기는 워크플로 애플리케이션의 App.config 파일 또는 워크플로 서비스의 Web.config에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-124">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="4b28b-125">이 예제에서는 <xref:System.Diagnostics.TextWriterTraceListener> 추적 정보를 현재 디렉터리의 MyTraceLog.txt 파일에 저장 하도록 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b28b-125">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b28b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b28b-126">See also</span></span>

- <span data-ttu-id="4b28b-127">[Windows Server App Fabric 모니터링](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4b28b-127">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="4b28b-128">[App Fabric을 사용 하 여 응용 프로그램 모니터링](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4b28b-128">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
