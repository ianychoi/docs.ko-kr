---
description: '자세히 알아보기: 추적 확장'
title: 추적 확장
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: e387f49eb4b31ce8dc0b726853ef69d20c8af063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752368"
---
# <a name="extend-tracing"></a><span data-ttu-id="580a3-103">추적 확장</span><span class="sxs-lookup"><span data-stu-id="580a3-103">Extend tracing</span></span>

<span data-ttu-id="580a3-104">이 샘플에서는 클라이언트 및 서비스 코드에 사용자 정의 동작 추적을 작성 하 여 WCF (Windows Communication Foundation) 추적 기능을 확장 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-104">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="580a3-105">사용자 정의 동작 추적을 작성 하면 사용자가 논리적 작업 단위로 추적 작업 및 그룹 추적을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-105">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="580a3-106">전송(같은 엔드포인트 내)과 전파(엔드포인트 사이)를 통해 동작을 상호 연결시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-106">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="580a3-107">이 샘플에서는 클라이언트와 서버 모두에 대해 추적이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-107">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="580a3-108">클라이언트 및 서비스 구성 파일에서 추적을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [추적 및 메시지 로깅](tracing-and-message-logging.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="580a3-108">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="580a3-109">이 샘플은 [시작](getting-started-sample.md)을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-109">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="580a3-110">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-110">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="580a3-111">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="580a3-112">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="580a3-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="580a3-113">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="580a3-114">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="580a3-115">추적 및 동작 전파</span><span class="sxs-lookup"><span data-stu-id="580a3-115">Tracing and Activity Propagation</span></span>  

 <span data-ttu-id="580a3-116">사용자 정의 동작 추적을 사용 하면 사용자가 추적 작업을 만들어 논리적 작업 단위로 추적을 그룹화 하 고, 전송 및 전파를 통해 동작을 상호 연결 하 고, WCF 추적의 성능 비용을 줄일 수 있습니다 (예: 로그 파일의 디스크 공간 비용).</span><span class="sxs-lookup"><span data-stu-id="580a3-116">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="580a3-117">사용자 지정 원본 추가</span><span class="sxs-lookup"><span data-stu-id="580a3-117">Add custom sources</span></span>  

 <span data-ttu-id="580a3-118">사용자 정의 추적은 클라이언트와 서비스 코드 모두에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-118">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="580a3-119">클라이언트 또는 서비스 구성 파일에 추적 소스를 추가 하면 이러한 사용자 지정 추적을 기록 하 여 [서비스 추적 뷰어 도구 (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-119">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="580a3-120">다음 코드에서는 `ServerCalculatorTraceSource`라는 사용자 정의 추적 소스를 구성 파일에 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-120">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="580a3-121">활동 상관 관계</span><span class="sxs-lookup"><span data-stu-id="580a3-121">Correlate activities</span></span>  

 <span data-ttu-id="580a3-122">엔드포인트 사이에서 직접 동작을 상호 연결하려면 `propagateActivity` 추적 소스에서 `true` 특성을 `System.ServiceModel`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-122">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="580a3-123">또한 WCF 작업을 거치지 않고 추적을 전파 하려면 ServiceModel 동작 추적을 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-123">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="580a3-124">다음 코드 예제에서 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-124">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="580a3-125">ServiceModel 동작 추적을 끄는 것은 `switchValue` 속성으로 표시되는 추적 수준을 off로 설정하는 것과 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-125">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="580a3-126">성능 비용 줄이기</span><span class="sxs-lookup"><span data-stu-id="580a3-126">Lessen performance cost</span></span>  

 <span data-ttu-id="580a3-127">`ActivityTracing` 추적 소스에서 `System.ServiceModel`을 off로 설정하면 ServiceModel 동작 추적이 포함되지 않고 사용자 정의 동작 추적만 포함된 추적 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-127">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="580a3-128">ServiceModel 활동 추적을 제외 하면 훨씬 더 작은 로그 파일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-128">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="580a3-129">그러나 WCF 처리 추적과의 상관 관계를 설정할 기회가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-129">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="580a3-130">샘플 설정, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="580a3-130">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="580a3-131">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="580a3-132">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="580a3-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="580a3-133">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="580a3-133">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580a3-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="580a3-134">See also</span></span>

- <span data-ttu-id="580a3-135">[AppFabric 모니터링 샘플](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="580a3-135">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
