---
title: 추적 구성
description: 추적을 사용 하도록 설정 하 고, 추적 소스를 구성 하 고, 활동 추적 및 전파를 설정 하 고, 추적 수신기를 WCF의 추적에 액세스 하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 35ac2dded5b3c727391fcad3ca950c2de4dbea64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254443"
---
# <a name="configuring-tracing"></a><span data-ttu-id="34d25-103">추적 구성</span><span class="sxs-lookup"><span data-stu-id="34d25-103">Configuring Tracing</span></span>

<span data-ttu-id="34d25-104">이 항목에서는 추적을 사용하고, 추적을 내보내도록 추적 소스를 구성하고, 추적 수준을 설정하고, 엔드투엔드 추적 상관 관계를 지원하도록 동작 추적 및 전파를 설정하고, 추적에 액세스하도록 추적 수신기를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-104">This topic describes how you can enable tracing, configure trace sources to emit traces and set trace levels, set activity tracing and propagation to support end-to-end trace correlation, and set trace listeners to access traces.</span></span>  
  
 <span data-ttu-id="34d25-105">프로덕션 또는 디버깅 환경에서의 추적 설정 권장 사항은 [추적 및 메시지 로깅에 대 한 권장 설정](recommended-settings-for-tracing-and-message-logging.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-105">For tracing settings recommendations in production or debugging environment, refer to [Recommended Settings for Tracing and Message Logging](recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34d25-106">Windows 8에서 애플리케이션이 추적 로그를 생성할 수 있도록 하려면 애플리케이션을 승격된 상태(관리자 권한으로 실행)로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-106">On Windows 8 you must run your application elevated (Run as Administrator) in order for your application to generate trace logs.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="34d25-107">추적 사용</span><span class="sxs-lookup"><span data-stu-id="34d25-107">Enabling Tracing</span></span>  

 <span data-ttu-id="34d25-108">WCF (Windows Communication Foundation)는 진단 추적에 대해 다음 데이터를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-108">Windows Communication Foundation (WCF) outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="34d25-109">작업 호출, 코드 예외, 경고 및 기타 중요 한 처리 이벤트와 같은 응용 프로그램의 모든 구성 요소에서 프로세스 마일스 톤에 대 한 추적입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-109">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings, and other significant processing events.</span></span>  
  
- <span data-ttu-id="34d25-110">추적 기능 오작동 시 Windows 오류 이벤트.</span><span class="sxs-lookup"><span data-stu-id="34d25-110">Windows error events when the tracing feature malfunctions.</span></span> <span data-ttu-id="34d25-111">[이벤트 로깅](../event-logging/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-111">See [Event Logging](../event-logging/index.md).</span></span>  
  
 <span data-ttu-id="34d25-112">WCF 추적은를 기반으로 빌드됩니다 <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="34d25-112">WCF tracing is built on top of <xref:System.Diagnostics>.</span></span> <span data-ttu-id="34d25-113">추적을 사용하려면 구성 파일 또는 코드에 추적 소스를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-113">To use tracing, you should define trace sources in the configuration file or in code.</span></span> <span data-ttu-id="34d25-114">WCF는 각 WCF 어셈블리에 대 한 추적 소스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-114">WCF defines a trace source for each WCF assembly.</span></span> <span data-ttu-id="34d25-115">`System.ServiceModel`추적 소스는 가장 일반적으로 사용 되는 wcf 추적 소스 이며, 전송 시작/종료부터 사용자 코드 입력/종료까지 wcf 통신 스택의 처리 마일스 톤을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-115">The `System.ServiceModel` trace source is the most general WCF trace source, and records processing milestones across the WCF communication stack, from entering/leaving transport to entering/leaving user code.</span></span> <span data-ttu-id="34d25-116">`System.ServiceModel.MessageLogging` 추적 소스는 시스템을 통해 이동하는 모든 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-116">The `System.ServiceModel.MessageLogging` trace source records all messages that flow through the system.</span></span>  
  
 <span data-ttu-id="34d25-117">추적은 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-117">Tracing is not enabled by default.</span></span> <span data-ttu-id="34d25-118">추적을 활성화 하려면 추적 수신기를 만들고 구성에서 선택한 추적 소스에 대해 "Off" 이외의 추적 수준을 설정 해야 합니다. 그렇지 않으면 WCF는 추적을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-118">To activate tracing, you must create a trace listener and set a trace level other than "Off" for the selected trace source in configuration; otherwise, WCF does not generate any traces.</span></span> <span data-ttu-id="34d25-119">수신기를 지정하지 않으면 추적이 자동으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-119">If you do not specify a listener, tracing is automatically disabled.</span></span> <span data-ttu-id="34d25-120">수신기는 정의되었지만 수준이 지정되지 않은 경우 수준이 기본적으로 "Off"로 설정됩니다. 이 설정은 추적이 내보내지지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-120">If a listener is defined, but no level is specified, the level is set to "Off" by default, which means that no trace is emitted.</span></span>  
  
 <span data-ttu-id="34d25-121">사용자 지정 작업 호출자와 같은 WCF 확장성 요소를 사용 하는 경우 사용자 고유의 추적을 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-121">If you use WCF extensibility points such as custom operation invokers, you should emit your own traces.</span></span> <span data-ttu-id="34d25-122">이는 확장성 지점을 구현 하는 경우 WCF는 더 이상 기본 경로에서 표준 추적을 내보낼 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-122">This is because if you implement an extensibility point, WCF can no longer emit the standard traces in the default path.</span></span> <span data-ttu-id="34d25-123">추적을 내보내 수동 추적 지원을 구현하지 않으면 예상하는 추적이 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-123">If you do not implement manual tracing support by emitting traces, you may not see the traces you expect.</span></span>  
  
 <span data-ttu-id="34d25-124">응용 프로그램의 구성 파일 (웹 호스팅 응용 프로그램의 경우 Web.config 또는 자체 호스팅 응용 프로그램용 Appname.exe.config을 편집 하 여 추적을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-124">You can configure tracing by editing the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted applications.</span></span> <span data-ttu-id="34d25-125">다음은 이러한 편집의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-125">The following is an example of such edit.</span></span> <span data-ttu-id="34d25-126">이러한 설정에 대 한 자세한 내용은 "추적을 사용 하도록 추적 수신기 구성" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-126">For more information on these settings, see the "Configuring Trace Listeners to Consume Traces" section.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="34d25-127">Visual Studio에서 WCF 서비스 프로젝트의 구성 파일을 편집 하려면 응용 프로그램의 구성 파일 (웹 호스팅 응용 프로그램의 경우 Web.config)을 마우스 오른쪽 단추로 클릭 하 고 **솔루션 탐색기** 에서 자체 호스팅된 응용 프로그램의 경우 Appname.exe.config 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-127">To edit the configuration file of a WCF service project in Visual Studio, right click the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted application in **Solution Explorer**.</span></span> <span data-ttu-id="34d25-128">그런 다음 **WCF 구성** 상황에 맞는 메뉴 항목 편집을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-128">Then choose the **Edit WCF Configuration** context menu item.</span></span> <span data-ttu-id="34d25-129">이렇게 하면 그래픽 사용자 인터페이스를 사용 하 여 WCF 서비스에 대 한 구성 설정을 수정할 수 있는 [구성 편집기 도구 (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md)가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-129">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), which enables you to modify configuration settings for WCF services using a graphical user interface.</span></span>  
  
## <a name="configuring-trace-sources-to-emit-traces"></a><span data-ttu-id="34d25-130">추적을 내보내도록 추적 소스 구성</span><span class="sxs-lookup"><span data-stu-id="34d25-130">Configuring Trace Sources to Emit Traces</span></span>  

 <span data-ttu-id="34d25-131">WCF는 각 어셈블리에 대 한 추적 소스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-131">WCF defines a trace source for each assembly.</span></span> <span data-ttu-id="34d25-132">어셈블리 내에 생성된 추적은 해당 소스에 대해 정의된 수신기를 통해 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-132">Traces generated within an assembly are accessed by the listeners defined for that source.</span></span> <span data-ttu-id="34d25-133">다음 추적 소스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-133">The following trace sources are defined:</span></span>  
  
- <span data-ttu-id="34d25-134">System.servicemodel: 구성을 읽을 때마다, 메시지를 전송에서 처리 하 고, 보안을 처리 하 고, 메시지를 사용자 코드에 디스패치할 수 있는 등의 모든 WCF 처리 단계를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-134">System.ServiceModel: Logs all stages of WCF processing, whenever configuration is read, a message is processed in transport, security processing, a message is dispatched in user code, and so on.</span></span>  
  
- <span data-ttu-id="34d25-135">System.ServiceModel.MessageLogging: 시스템을 통해 이동하는 모든 메시지를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-135">System.ServiceModel.MessageLogging: Logs all messages that flow through the system.</span></span>  
  
- <span data-ttu-id="34d25-136">System.IdentityModel</span><span class="sxs-lookup"><span data-stu-id="34d25-136">System.IdentityModel.</span></span>  
  
- <span data-ttu-id="34d25-137">System.ServiceModel.Activation</span><span class="sxs-lookup"><span data-stu-id="34d25-137">System.ServiceModel.Activation.</span></span>  
  
- <span data-ttu-id="34d25-138">System.IO.Log: CLFS(Common Log File System)에 대한 .NET Framework 인터페이스에 대해 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-138">System.IO.Log: Logging for the .NET Framework interface to the Common Log File System (CLFS).</span></span>  
  
- <span data-ttu-id="34d25-139">System.Runtime.Serialization: 개체를 읽거나 쓸 때 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-139">System.Runtime.Serialization: Logs when objects are read or written.</span></span>  
  
- <span data-ttu-id="34d25-140">CardSpace</span><span class="sxs-lookup"><span data-stu-id="34d25-140">CardSpace.</span></span>  
  
 <span data-ttu-id="34d25-141">다음 구성 예제에 표시된 대로 같은(공유) 수신기를 사용하도록 각 추적 소스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-141">You can configure each trace source to use the same (shared) listener, as indicated in the following configuration example.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="34d25-142">또한, 다음 예제처럼 사용자 정의 추적 소스를 추가하여 사용자 코드 추적을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-142">In addition, you can add user-defined trace sources, as demonstrated by the following example, to emit user code traces.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />
</system.diagnostics>  
```  
  
 <span data-ttu-id="34d25-143">사용자 정의 추적 소스를 만드는 방법에 대 한 자세한 내용은 [추적 확장](../../samples/extending-tracing.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-143">For more information about creating user-defined trace sources, see [Extending Tracing](../../samples/extending-tracing.md).</span></span>  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a><span data-ttu-id="34d25-144">추적을 사용하도록 추적 수신기 구성</span><span class="sxs-lookup"><span data-stu-id="34d25-144">Configuring Trace Listeners to Consume Traces</span></span>  

 <span data-ttu-id="34d25-145">런타임에 WCF는 데이터를 처리 하는 수신기에 추적 데이터를 공급 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-145">At runtime, WCF feeds trace data to the listeners, which process the data.</span></span> <span data-ttu-id="34d25-146">WCF는 <xref:System.Diagnostics> 출력에 사용 되는 형식과 다른에 대해 미리 정의 된 여러 수신기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-146">WCF provides several predefined listeners for <xref:System.Diagnostics>, which differ in the format they use for output.</span></span> <span data-ttu-id="34d25-147">사용자 지정 수신기 형식을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-147">You can also add custom listener types.</span></span>  
  
 <span data-ttu-id="34d25-148">`add`를 사용하여 사용할 추적 수신기의 이름과 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-148">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="34d25-149">예제 구성에서는 수신기 이름을 `traceListener`로 지정하고 표준 .NET Framework 추적 수신기(`System.Diagnostics.XmlWriterTraceListener`)를 사용할 형식으로 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-149">In our example configuration, we named the Listener `traceListener` and added the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type we want to use.</span></span> <span data-ttu-id="34d25-150">각 소스에 대한 추적 수신기를 여러 개 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-150">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="34d25-151">추적 수신기가 파일로 추적을 내보내는 경우에는 구성 파일에 출력 파일 위치와 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-151">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="34d25-152">이 작업을 수행하려면 `initializeData`를 해당 수신기의 파일 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-152">This is done by setting `initializeData` to the name of the file for that listener.</span></span> <span data-ttu-id="34d25-153">파일 이름을 지정하지 않으면 사용된 수신기 형식에 따라 임의 파일 이름이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-153">If you do not specify a file name, a random file name is generated based on the listener type used.</span></span> <span data-ttu-id="34d25-154"><xref:System.Diagnostics.XmlWriterTraceListener>가 사용되면 확장명이 없는 파일 이름이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-154">If <xref:System.Diagnostics.XmlWriterTraceListener> is used, a file name with no extension is generated.</span></span> <span data-ttu-id="34d25-155">사용자 지정 수신기를 구현하는 경우 이 특성을 사용하여 파일 이름 이외의 초기화 데이터를 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-155">If you implement a custom listener, you can also use this attribute to receive initialization data other than a filename.</span></span> <span data-ttu-id="34d25-156">예를 들면 이 특성에 대한 데이터베이스 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-156">For example, you can specify a database identifier for this attribute.</span></span>  
  
 <span data-ttu-id="34d25-157">원격 데이터베이스와 같은 연결을 통해 추적을 보내도록 사용자 지정 추적 수신기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-157">You can configure a custom trace listener to send traces on the wire, for example, to a remote database.</span></span> <span data-ttu-id="34d25-158">애플리케이션 배포자인 경우 원격 컴퓨터의 추적 로그에 적절한 액세스 제어를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-158">As an application deployer, you should enforce proper access control on the trace logs in the remote machine.</span></span>  
  
 <span data-ttu-id="34d25-159">추적 수신기를 프로그래밍 방식으로 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-159">You can also configure a trace listener programmatically.</span></span> <span data-ttu-id="34d25-160">자세한 내용은 [방법: 추적 수신기 만들기 및 초기화](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) 및 [사용자 지정 TraceListener 만들기](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-160">For more information, see [How to: Create and Initialize Trace Listeners](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [Creating a Custom TraceListener](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="34d25-161">`System.Diagnostics.XmlWriterTraceListener`는 스레드로부터 안전하지 않으므로 추적을 출력할 때 추적 소스가 리소스를 단독으로 잠글 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-161">Because `System.Diagnostics.XmlWriterTraceListener` is not thread-safe, the trace source may lock resources exclusively when outputting traces.</span></span> <span data-ttu-id="34d25-162">여러 스레드에서 이 수신기를 사용하도록 구성된 추적 소스로 추적을 출력하면 리소스 경합이 발생할 수 있으며, 이로 인해 성능이 크게 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-162">When many threads output traces to a trace source configured to use this listener, resource contention may occur, which results in a significant performance issue.</span></span> <span data-ttu-id="34d25-163">이 문제를 해결하려면 스레드로부터 안전한 사용자 지정 수신기를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-163">To resolve this problem, you should implement a custom listener that is thread-safe.</span></span>  
  
## <a name="trace-level"></a><span data-ttu-id="34d25-164">추적 수준</span><span class="sxs-lookup"><span data-stu-id="34d25-164">Trace Level</span></span>  

 <span data-ttu-id="34d25-165">추적 수준은 추적 소스의 `switchValue` 설정에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-165">The tracing level is controlled by the `switchValue` setting of the trace source.</span></span> <span data-ttu-id="34d25-166">다음 표에서는 사용할 수 있는 추적 수준에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-166">The available tracing levels are described in the following table.</span></span>  
  
|<span data-ttu-id="34d25-167">추적 수준</span><span class="sxs-lookup"><span data-stu-id="34d25-167">Trace Level</span></span>|<span data-ttu-id="34d25-168">추적 이벤트의 특성</span><span class="sxs-lookup"><span data-stu-id="34d25-168">Nature of the Tracked Events</span></span>|<span data-ttu-id="34d25-169">추적 이벤트의 내용</span><span class="sxs-lookup"><span data-stu-id="34d25-169">Content of the Tracked Events</span></span>|<span data-ttu-id="34d25-170">추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="34d25-170">Tracked Events</span></span>|<span data-ttu-id="34d25-171">사용자 대상</span><span class="sxs-lookup"><span data-stu-id="34d25-171">User Target</span></span>|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="34d25-172">끄기</span><span class="sxs-lookup"><span data-stu-id="34d25-172">Off</span></span>|<span data-ttu-id="34d25-173">해당 없음</span><span class="sxs-lookup"><span data-stu-id="34d25-173">N/A</span></span>|<span data-ttu-id="34d25-174">해당 없음</span><span class="sxs-lookup"><span data-stu-id="34d25-174">N/A</span></span>|<span data-ttu-id="34d25-175">내보낸 추적이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-175">No traces are emitted.</span></span>|<span data-ttu-id="34d25-176">해당 없음</span><span class="sxs-lookup"><span data-stu-id="34d25-176">N/A</span></span>|  
|<span data-ttu-id="34d25-177">위험</span><span class="sxs-lookup"><span data-stu-id="34d25-177">Critical</span></span>|<span data-ttu-id="34d25-178">"음수" 이벤트: 예기치 않은 처리 또는 오류 상태를 나타내는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-178">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>||<span data-ttu-id="34d25-179">다음을 포함하여 처리되지 않은 예외를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-179">Unhandled exceptions including the following are logged:</span></span><br /><br /> <span data-ttu-id="34d25-180">-OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="34d25-180">-   OutOfMemoryException</span></span><br /><span data-ttu-id="34d25-181">-ThreadAbortException (CLR은 모든 ThreadAbortExceptionHandler를 호출 합니다.)</span><span class="sxs-lookup"><span data-stu-id="34d25-181">-   ThreadAbortException (the CLR invokes any ThreadAbortExceptionHandler)</span></span><br /><span data-ttu-id="34d25-182">-System.stackoverflowexception (catch 할 수 없음)</span><span class="sxs-lookup"><span data-stu-id="34d25-182">-   StackOverflowException (cannot be caught)</span></span><br /><span data-ttu-id="34d25-183">-System.configuration.configurationerrorsexception</span><span class="sxs-lookup"><span data-stu-id="34d25-183">-   ConfigurationErrorsException</span></span><br /><span data-ttu-id="34d25-184">-SEHException</span><span class="sxs-lookup"><span data-stu-id="34d25-184">-   SEHException</span></span><br /><span data-ttu-id="34d25-185">-응용 프로그램 시작 오류</span><span class="sxs-lookup"><span data-stu-id="34d25-185">-   Application start errors</span></span><br /><span data-ttu-id="34d25-186">-Failfast 이벤트</span><span class="sxs-lookup"><span data-stu-id="34d25-186">-   Failfast events</span></span><br /><span data-ttu-id="34d25-187">-시스템 중지</span><span class="sxs-lookup"><span data-stu-id="34d25-187">-   System hangs</span></span><br /><span data-ttu-id="34d25-188">-포이즌 메시지: 응용 프로그램 실패를 유발 하는 메시지 추적입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-188">-   Poison messages: message traces that cause the application to fail.</span></span>|<span data-ttu-id="34d25-189">관리자</span><span class="sxs-lookup"><span data-stu-id="34d25-189">Administrators</span></span><br /><br /> <span data-ttu-id="34d25-190">애플리케이션 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-190">Application developers</span></span>|  
|<span data-ttu-id="34d25-191">오류</span><span class="sxs-lookup"><span data-stu-id="34d25-191">Error</span></span>|<span data-ttu-id="34d25-192">"음수" 이벤트: 예기치 않은 처리 또는 오류 상태를 나타내는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-192">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="34d25-193">예기치 않은 처리가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-193">Unexpected processing has happened.</span></span> <span data-ttu-id="34d25-194">애플리케이션이 예상한 대로 작업을 수행하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-194">The application was not able to perform a task as expected.</span></span> <span data-ttu-id="34d25-195">그러나 애플리케이션이 여전히 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-195">However, the application is still up and running.</span></span>|<span data-ttu-id="34d25-196">모든 예외가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-196">All exceptions are logged.</span></span>|<span data-ttu-id="34d25-197">관리자</span><span class="sxs-lookup"><span data-stu-id="34d25-197">Administrators</span></span><br /><br /> <span data-ttu-id="34d25-198">애플리케이션 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-198">Application developers</span></span>|  
|<span data-ttu-id="34d25-199">경고</span><span class="sxs-lookup"><span data-stu-id="34d25-199">Warning</span></span>|<span data-ttu-id="34d25-200">"음수" 이벤트: 예기치 않은 처리 또는 오류 상태를 나타내는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-200">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="34d25-201">문제가 발생했거나 발생할 수도 있지만 애플리케이션이 여전히 올바르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-201">A possible problem has occurred or may occur, but the application still functions correctly.</span></span> <span data-ttu-id="34d25-202">그러나 계속 올바르게 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-202">However, it may not continue to work properly.</span></span>|<span data-ttu-id="34d25-203">-응용 프로그램이 제한 설정에서 허용 하는 것 보다 많은 요청을 받고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-203">-   The application is receiving more requests than its throttling settings allow.</span></span><br /><span data-ttu-id="34d25-204">-수신 큐가 구성 된 최대 용량에 도달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-204">-   The receiving queue is near its maximum configured capacity.</span></span><br /><span data-ttu-id="34d25-205">-제한 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-205">-   Timeout has exceeded.</span></span><br /><span data-ttu-id="34d25-206">-자격 증명이 거부 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-206">-   Credentials are rejected.</span></span>|<span data-ttu-id="34d25-207">관리자</span><span class="sxs-lookup"><span data-stu-id="34d25-207">Administrators</span></span><br /><br /> <span data-ttu-id="34d25-208">애플리케이션 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-208">Application developers</span></span>|  
|<span data-ttu-id="34d25-209">정보</span><span class="sxs-lookup"><span data-stu-id="34d25-209">Information</span></span>|<span data-ttu-id="34d25-210">"긍정" 이벤트: 성공적인 마일스 톤을 표시 하는 이벤트</span><span class="sxs-lookup"><span data-stu-id="34d25-210">"Positive" events: events that mark successful milestones</span></span>|<span data-ttu-id="34d25-211">애플리케이션이 올바르게 작동하는지 여부에 관계 없이 애플리케이션 실행의 중요한 중요 시점과 성공적인 중요 시점입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-211">Important and successful milestones of application execution, regardless of whether the application is working properly or not.</span></span>|<span data-ttu-id="34d25-212">일반적으로 시스템 상태 모니터링 및 진단, 성능 측정 또는 프로파일링에 유용한 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-212">In general, messages helpful for monitoring and diagnosing system status, measuring performance or profiling are generated.</span></span> <span data-ttu-id="34d25-213">용량 계획 및 성능 관리에 이러한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-213">You can use such information for capacity planning and performance management:</span></span><br /><br /> <span data-ttu-id="34d25-214">-채널이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-214">-   Channels are created.</span></span><br /><span data-ttu-id="34d25-215">-끝점 수신기가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-215">-   Endpoint listeners are created.</span></span><br /><span data-ttu-id="34d25-216">-메시지가 전송 되 고 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-216">-   Message enters/leaves transport.</span></span><br /><span data-ttu-id="34d25-217">-보안 토큰을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-217">-   Security token is retrieved.</span></span><br /><span data-ttu-id="34d25-218">-구성 설정을 읽었습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-218">-   Configuration setting is read.</span></span>|<span data-ttu-id="34d25-219">관리자</span><span class="sxs-lookup"><span data-stu-id="34d25-219">Administrators</span></span><br /><br /> <span data-ttu-id="34d25-220">애플리케이션 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-220">Application developers</span></span><br /><br /> <span data-ttu-id="34d25-221">제품 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-221">Product developers.</span></span>|  
|<span data-ttu-id="34d25-222">자세히</span><span class="sxs-lookup"><span data-stu-id="34d25-222">Verbose</span></span>|<span data-ttu-id="34d25-223">"긍정" 이벤트: 성공적인 마일스 톤을 표시 하는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-223">"Positive" events: events that mark successful milestones.</span></span>|<span data-ttu-id="34d25-224">사용자 코드 및 서비스에 대 한 하위 수준 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-224">Low-level events for both user code and servicing are emitted.</span></span>|<span data-ttu-id="34d25-225">일반적으로 디버깅 또는 애플리케이션 최적화에 이 수준을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-225">In general, you can use this level for debugging or application optimization.</span></span><br /><br /> <span data-ttu-id="34d25-226">-메시지 헤더를 이해 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-226">-   Understood message header.</span></span>|<span data-ttu-id="34d25-227">관리자</span><span class="sxs-lookup"><span data-stu-id="34d25-227">Administrators</span></span><br /><br /> <span data-ttu-id="34d25-228">애플리케이션 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-228">Application developers</span></span><br /><br /> <span data-ttu-id="34d25-229">제품 개발자</span><span class="sxs-lookup"><span data-stu-id="34d25-229">Product developers.</span></span>|  
|<span data-ttu-id="34d25-230">ActivityTracing</span><span class="sxs-lookup"><span data-stu-id="34d25-230">ActivityTracing</span></span>||<span data-ttu-id="34d25-231">처리 동작과 구성 요소 간의 흐름 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-231">Flow events between processing activities and components.</span></span>|<span data-ttu-id="34d25-232">이 수준에서 관리자와 개발자가 같은 애플리케이션 도메인의 애플리케이션을 서로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-232">This level allows administrators and developers to correlate applications in the same application domain:</span></span><br /><br /> <span data-ttu-id="34d25-233">-시작/중지와 같은 작업 경계를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-233">-   Traces for activity boundaries, such as start/stop.</span></span><br /><span data-ttu-id="34d25-234">-전송에 대 한 추적입니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-234">-   Traces for transfers.</span></span>|<span data-ttu-id="34d25-235">모두</span><span class="sxs-lookup"><span data-stu-id="34d25-235">All</span></span>|  
|<span data-ttu-id="34d25-236">모두</span><span class="sxs-lookup"><span data-stu-id="34d25-236">All</span></span>||<span data-ttu-id="34d25-237">애플리케이션이 올바르게 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-237">Application may function properly.</span></span> <span data-ttu-id="34d25-238">모든 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-238">All events are emitted.</span></span>|<span data-ttu-id="34d25-239">앞의 이벤트 모두</span><span class="sxs-lookup"><span data-stu-id="34d25-239">All previous events.</span></span>|<span data-ttu-id="34d25-240">모두</span><span class="sxs-lookup"><span data-stu-id="34d25-240">All</span></span>|  
  
 <span data-ttu-id="34d25-241">Verbose에서 Critical까지의 수준은 서로 위에 쌓입니다. 즉, 각 추적 수준에 Off 수준을 제외한 위의 모든 수준이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-241">The levels from Verbose to Critical are stacked on top of each other, that is, each trace level includes all levels above it except the Off level.</span></span> <span data-ttu-id="34d25-242">예를 들어, Warning 수준에서 수신 대기하는 수신기는 Critical, Error 및 Warning 추적을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-242">For example, a listener listening at the Warning level receives Critical, Error, and Warning traces.</span></span> <span data-ttu-id="34d25-243">모두 수준에는 Verbose에서 Critical까지의 이벤트와 동작 추적 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-243">The All level includes events from Verbose to Critical and Activity tracing events.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="34d25-244">Information, Verbose 및 ActivityTracing 수준은 컴퓨터에서 사용 가능한 모든 리소스를 모두 사용한 경우 메시지 처리량을 줄일 수도 있는 여러 가지 추적을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-244">The Information, Verbose, and ActivityTracing levels generate a lot of traces, which may negatively impact message throughput if you have used up all available resources on the machine.</span></span>  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a><span data-ttu-id="34d25-245">상관 관계를 위한 동작 추적 및 전파 구성</span><span class="sxs-lookup"><span data-stu-id="34d25-245">Configuring Activity Tracing and Propagation for Correlation</span></span>  

 <span data-ttu-id="34d25-246">ph x="1" /&gt; 특성에 대한 지정된 `switchValue` 값은 엔드포인트 내에서 동작 경계와 전송에 대한 추적을 내보내는 동작 추적을 활성화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-246">The `activityTracing` value specified for the `switchValue` attribute is used to enable activity tracing, which emits traces for activity boundaries and transfers within endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34d25-247">WCF에서 특정 확장성 기능을 사용 하는 경우 <xref:System.NullReferenceException> 작업 추적이 사용 되 면이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-247">When you use certain extensibility features in WCF, you might get a <xref:System.NullReferenceException> when activity tracing is enabled.</span></span> <span data-ttu-id="34d25-248">이 문제를 해결하려면 애플리케이션의 구성 파일을 확인하고 추적 소스의 `switchValue` 특성이 `activityTracing`으로 설정되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-248">To fix this problem, check your application's configuration file and ensure that the `switchValue` attribute for your trace source is not set to `activityTracing`.</span></span>  
  
 <span data-ttu-id="34d25-249">ph x="1" /&gt; 특성은 동작을 메시지 교환에 참여하는 다른 엔드포인트에 전파해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-249">The `propagateActivity` attribute indicates whether the activity should be propagated to other endpoints that participate in the message exchange.</span></span> <span data-ttu-id="34d25-250">이 값을 `true`로 설정하여 두 엔드포인트에서 생성된 추적 파일을 가져오고 한 엔드포인트의 추적 집합이 다른 엔드포인트의 추적 집합으로 이동한 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-250">By setting this value to `true`, you can take trace files generated by any two endpoints and observe how a set of traces on one endpoint flowed to a set of traces on another endpoint.</span></span>  
  
 <span data-ttu-id="34d25-251">활동 추적 및 전파에 대 한 자세한 내용은 [전파](propagation.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34d25-251">For more information about activity tracing and propagation, see [Propagation](propagation.md).</span></span>  
  
 <span data-ttu-id="34d25-252">`propagateActivity`및 `ActivityTracing` 부울 값은 모두 system.servicemodel TraceSource에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-252">Both `propagateActivity` and `ActivityTracing` Boolean values apply to the System.ServiceModel TraceSource.</span></span> <span data-ttu-id="34d25-253">`ActivityTracing`값은 WCF 또는 사용자 정의를 포함 하 여 모든 추적 소스에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-253">The `ActivityTracing` value also applies to any trace source, including WCF or user-defined ones.</span></span>  
  
 <span data-ttu-id="34d25-254">`propagateActivity` 특성은 사용자 정의 추적 소스에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-254">You cannot use the `propagateActivity` attribute with user-defined trace sources.</span></span> <span data-ttu-id="34d25-255">사용자 코드 동작 ID 전파를 위해 ServiceModel `ActivityTracing`은 설정하지 않고 ServiceModel `propagateActivity` 특성은 `true`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d25-255">For user code activity ID propagation, make sure you do not set ServiceModel `ActivityTracing`, while still having ServiceModel `propagateActivity` attribute set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d25-256">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34d25-256">See also</span></span>

- [<span data-ttu-id="34d25-257">추적</span><span class="sxs-lookup"><span data-stu-id="34d25-257">Tracing</span></span>](index.md)
- [<span data-ttu-id="34d25-258">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="34d25-258">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="34d25-259">방법: 추적 수신기 만들기 및 초기화</span><span class="sxs-lookup"><span data-stu-id="34d25-259">How to: Create and Initialize Trace Listeners</span></span>](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [<span data-ttu-id="34d25-260">Creating a Custom TraceListener</span><span class="sxs-lookup"><span data-stu-id="34d25-260">Creating a Custom TraceListener</span></span>](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
