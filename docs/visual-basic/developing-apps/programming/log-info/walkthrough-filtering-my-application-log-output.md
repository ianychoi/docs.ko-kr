---
description: '자세한 정보: 연습: My.Application.Log 출력 필터링(Visual Basic)'
title: My.Application.Log 출력 필터링
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 0fa64bde27be17b1809e45bfe294e70c7dd33563
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792260"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="7d815-103">연습: My.Application.Log 출력 필터링(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d815-103">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="7d815-104">이 연습에서는 `My.Application.Log` 개체에 대한 기본 로그 필터링을 변경하여 `Log` 개체에서 수신기로 전달되는 정보 및 수신기가 작성하는 정보를 제어하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-104">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="7d815-105">구성 정보가 애플리케이션의 구성 파일에 저장되므로 애플리케이션을 빌드한 후에도 로깅 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-105">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="7d815-106">시작하기</span><span class="sxs-lookup"><span data-stu-id="7d815-106">Getting Started</span></span>

<span data-ttu-id="7d815-107">`My.Application.Log`에서 작성하는 각 메시지에는 연결된 심각도 수준이 있으며, 필터링 메커니즘은 로그 출력을 제어하는 데 이를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-107">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="7d815-108">이 샘플 애플리케이션은 `My.Application.Log` 메서드를 사용하여 서로 다른 심각도 수준으로 여러 로그 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-108">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="7d815-109">샘플 애플리케이션을 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="7d815-109">To build the sample application</span></span>

1. <span data-ttu-id="7d815-110">새 Visual Basic Windows 애플리케이션 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-110">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="7d815-111">Button1이라는 단추를 Form1에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-111">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="7d815-112">Button1에 대한 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-112">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="7d815-113">디버거에서 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-113">Run the application in the debugger.</span></span>

5. <span data-ttu-id="7d815-114">**Button1** 을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-114">Press **Button1**.</span></span>

     <span data-ttu-id="7d815-115">애플리케이션이 다음 정보를 애플리케이션의 디버그 출력 및 로그 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-115">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="7d815-116">애플리케이션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-116">Close the application.</span></span>

     <span data-ttu-id="7d815-117">애플리케이션의 디버그 출력 창을 보는 방법에 대한 자세한 내용은 [출력 창](/visualstudio/ide/reference/output-window)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d815-117">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="7d815-118">애플리케이션 로그 파일의 위치에 대한 자세한 내용은 [연습: My.Application.Log가 정보를 기록하는 위치 확인](walkthrough-determining-where-my-application-log-writes-information.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d815-118">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d815-119">기본적으로 애플리케이션을 닫으면 애플리케이션이 로그 파일 출력을 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-119">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="7d815-120">위의 예제에서 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> 메서드에 대한 두 번째 호출 및 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> 메서드에 대한 호출은 로그 출력을 생성하지만, `WriteEntry` 메서드에 대한 첫 번째 및 마지막 호출은 로그 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-120">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="7d815-121">`WriteEntry` 및 `WriteException`의 심각도 수준은 "정보" 및 "오류"이므로, 둘 다 `My.Application.Log` 개체의 기본 로그 필터링에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-121">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="7d815-122">그러나 "시작" 및 "중지" 심각도 수준의 이벤트는 로그 출력 생성이 금지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-122">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="7d815-123">모든 My.Application.Log 수신기에 대한 필터링</span><span class="sxs-lookup"><span data-stu-id="7d815-123">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="7d815-124">`My.Application.Log` 개체는 `DefaultSwitch`라고 명명된 <xref:System.Diagnostics.SourceSwitch>를 사용하여 `WriteEntry` 및 `WriteException` 메서드에서 로그 수신기로 전달할 메시지를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-124">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="7d815-125">해당 값을 <xref:System.Diagnostics.SourceLevels> 열거형 값 중 하나로 설정하여 애플리케이션의 구성 파일에서 `DefaultSwitch`를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-125">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="7d815-126">기본적으로 값은 "정보"입니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-126">By default, its value is "Information".</span></span>

<span data-ttu-id="7d815-127">다음 표는 특정 `DefaultSwitch` 설정이 지정된 경우 로그가 메시지를 수신기에 기록하는 데 필요한 심각도 수준을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-127">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="7d815-128">DefaultSwitch 값</span><span class="sxs-lookup"><span data-stu-id="7d815-128">DefaultSwitch Value</span></span>|<span data-ttu-id="7d815-129">출력에 필요한 메시지 심각도</span><span class="sxs-lookup"><span data-stu-id="7d815-129">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="7d815-130">`Critical` 또는 `Error`</span><span class="sxs-lookup"><span data-stu-id="7d815-130">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="7d815-131">`Critical`, `Error`또는 `Warning`</span><span class="sxs-lookup"><span data-stu-id="7d815-131">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="7d815-132">`Critical`, `Error`, `Warning` 또는 `Information`</span><span class="sxs-lookup"><span data-stu-id="7d815-132">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="7d815-133">`Critical`, `Error`, `Warning`, `Information` 또는 `Verbose`</span><span class="sxs-lookup"><span data-stu-id="7d815-133">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="7d815-134">`Start`, `Stop`, `Suspend`, `Resume` 또는 `Transfer`</span><span class="sxs-lookup"><span data-stu-id="7d815-134">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="7d815-135">모든 메시지를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-135">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="7d815-136">모든 메시지를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-136">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="7d815-137">`WriteEntry` 및 `WriteException` 메서드는 각각 심각도 수준을 지정하지 않는 오버로드를 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-137">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="7d815-138">`WriteEntry` 오버로드에 대한 암시적 심각도 수준은 "정보"이며, `WriteException` 오버로드에 대한 암시적 심각도 수준은 "오류"입니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-138">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="7d815-139">다음 표는 이전 예제에 나와 있는 로그 출력을 설명합니다. 기본 `DefaultSwitch` 설정이 "정보"인 경우 `WriteEntry` 메서드에 대한 두 번째 호출 및 `WriteException` 메서드에 대한 호출만이 로그 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-139">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="7d815-140">작업 추적 이벤트만 기록하려면</span><span class="sxs-lookup"><span data-stu-id="7d815-140">To log only activity tracing events</span></span>

1. <span data-ttu-id="7d815-141">**솔루션 탐색기** 에서 app.config를 마우스 오른쪽 단추로 클릭하고 **열기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-141">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="7d815-142">또는</span><span class="sxs-lookup"><span data-stu-id="7d815-142">-or-</span></span>

     <span data-ttu-id="7d815-143">app.config 파일이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="7d815-143">If there is no app.config file:</span></span>

    1. <span data-ttu-id="7d815-144">**프로젝트** 메뉴에서 **새 항목 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-144">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7d815-145">**새 항목 추가** 대화 상자에서 **애플리케이션 구성 파일** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-145">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7d815-146">**추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-146">Click **Add**.</span></span>

2. <span data-ttu-id="7d815-147">최상위 `<configuration>` 섹션의 `<system.diagnostics>` 섹션에 있는 `<switches>` 섹션으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-147">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="7d815-148">스위치 컬렉션에 `DefaultSwitch`를 추가하는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-148">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="7d815-149">이 요소는 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-149">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="7d815-150">`value` 특성의 값을 "ActivityTracing"으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-150">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="7d815-151">app.config 파일의 내용은 다음 XML과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-151">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. <span data-ttu-id="7d815-152">디버거에서 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-152">Run the application in the debugger.</span></span>

7. <span data-ttu-id="7d815-153">**Button1** 을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-153">Press **Button1**.</span></span>

     <span data-ttu-id="7d815-154">애플리케이션이 다음 정보를 애플리케이션의 디버그 출력 및 로그 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-154">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="7d815-155">애플리케이션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-155">Close the application.</span></span>

9. <span data-ttu-id="7d815-156">`value` 특성의 값을 다시 "정보"로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-156">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d815-157">`DefaultSwitch` 스위치 설정은 `My.Application.Log`만 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-157">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="7d815-158">.NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 및 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 클래스의 동작은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-158">It does not change how the .NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="7d815-159">My.Application.Log 수신기에 대한 개별 필터링</span><span class="sxs-lookup"><span data-stu-id="7d815-159">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="7d815-160">이전 예제에서는 모든 `My.Application.Log` 출력에 대한 필터링을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-160">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="7d815-161">이 예제에서는 개별 로그 수신기를 필터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-161">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="7d815-162">기본적으로 애플리케이션에는 각각 애플리케이션의 디버그 출력 및 로그 파일에 기록하는 두 개의 수신기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-162">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="7d815-163">구성 파일은 각 로그 수신기에 `My.Application.Log`용 스위치와 비슷한 필터를 허용하여 로그 수신기의 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-163">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="7d815-164">로그 수신기는 로그의 `DefaultSwitch` 및 로그 수신기의 필터에서 메시지의 심각도를 허용하는 경우에만 메시지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-164">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="7d815-165">이 예제는 새 디버그 수신기에 대한 필터링을 구성하고 `Log` 개체에 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-165">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="7d815-166">기본 디버그 수신기는 `Log` 개체에서 제거해야 하므로, 디버그 메시지가 새 디버그 수신기에서 오는 것이 분명합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-166">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="7d815-167">동작 추적 이벤트만 기록하려면</span><span class="sxs-lookup"><span data-stu-id="7d815-167">To log only activity-tracing events</span></span>

1. <span data-ttu-id="7d815-168">**솔루션 탐색기** 에서 app.config를 마우스 오른쪽 단추로 클릭하고 **열기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-168">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="7d815-169">\-또는-</span><span class="sxs-lookup"><span data-stu-id="7d815-169">\-or-</span></span>

     <span data-ttu-id="7d815-170">app.config 파일이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="7d815-170">If there is no app.config file:</span></span>

    1. <span data-ttu-id="7d815-171">**프로젝트** 메뉴에서 **새 항목 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-171">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7d815-172">**새 항목 추가** 대화 상자에서 **애플리케이션 구성 파일** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-172">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7d815-173">**추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-173">Click **Add**.</span></span>

2. <span data-ttu-id="7d815-174">**솔루션 탐색기** 에서 app.config를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-174">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="7d815-175">**열기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-175">Choose **Open**.</span></span>

3. <span data-ttu-id="7d815-176">`<sources>` 섹션 아래에서 `name` 특성이 "DefaultSource"인 `<source>` 섹션에서 `<listeners>` 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-176">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="7d815-177">`<sources>` 섹션은 최상위 `<configuration>` 섹션의 `<system.diagnostics>` 섹션에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-177">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="7d815-178">이 요소를 `<listeners>` 섹션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-178">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="7d815-179">최상위 `<sharedListeners>` 섹션의 `<system.diagnostics>` 섹션에서 `<configuration>` 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-179">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="7d815-180">다음 요소를 `<sharedListeners>` 섹션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-180">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     <span data-ttu-id="7d815-181"><xref:System.Diagnostics.EventTypeFilter> 필터는 <xref:System.Diagnostics.SourceLevels> 열거형 값 중 하나를 해당 `initializeData` 특성으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-181">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="7d815-182">app.config 파일의 내용은 다음 XML과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-182">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. <span data-ttu-id="7d815-183">디버거에서 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-183">Run the application in the debugger.</span></span>

9. <span data-ttu-id="7d815-184">**Button1** 을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-184">Press **Button1**.</span></span>

     <span data-ttu-id="7d815-185">애플리케이션이 다음 정보를 애플리케이션의 로그 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-185">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="7d815-186">애플리케이션은 좀 더 제한적인 필터링 때문에 애플리케이션의 디버그 출력에 정보를 더 적게 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-186">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="7d815-187">애플리케이션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d815-187">Close the application.</span></span>

<span data-ttu-id="7d815-188">배포 후 로그 설정을 변경하는 방법에 대한 자세한 내용은 [애플리케이션 로그 작업](working-with-application-logs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7d815-188">For more information about changing log settings after deployment, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d815-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d815-189">See also</span></span>

- [<span data-ttu-id="7d815-190">연습: My.Application.Log가 정보를 기록하는 위치 확인</span><span class="sxs-lookup"><span data-stu-id="7d815-190">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="7d815-191">연습: My.Application.Log가 정보를 기록하는 위치 변경</span><span class="sxs-lookup"><span data-stu-id="7d815-191">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="7d815-192">연습: 사용자 지정 로그 수신기 만들기</span><span class="sxs-lookup"><span data-stu-id="7d815-192">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="7d815-193">방법: 로그 메시지 쓰기</span><span class="sxs-lookup"><span data-stu-id="7d815-193">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="7d815-194">추적 스위치</span><span class="sxs-lookup"><span data-stu-id="7d815-194">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="7d815-195">애플리케이션의 정보 기록</span><span class="sxs-lookup"><span data-stu-id="7d815-195">Logging Information from the Application</span></span>](index.md)
