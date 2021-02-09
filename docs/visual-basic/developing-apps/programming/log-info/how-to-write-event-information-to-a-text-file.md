---
description: '자세한 정보: 방법: 텍스트 파일에 이벤트 정보 쓰기(Visual Basic)'
title: '방법: 텍스트 파일에 이벤트 정보 쓰기'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: eb6fab9976c010080c0cffa37edd4f790dc73956
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775138"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="9b084-103">방법: 텍스트 파일에 이벤트 정보 쓰기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b084-103">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="9b084-104">`My.Application.Log` 및 `My.Log` 개체를 사용하여 애플리케이션에서 발생하는 이벤트에 대한 정보를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="9b084-105">이 예제에서는 `My.Application.Log.WriteEntry` 메서드를 사용하여 추적 정보를 로그 파일에 기록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-105">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="9b084-106">파일 로그 수신기를 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9b084-106">To add and configure the file log listener</span></span>

1. <span data-ttu-id="9b084-107">**솔루션 탐색기** 에서 app.config를 마우스 오른쪽 단추로 클릭하고 **열기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-107">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="9b084-108">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="9b084-108">\- or -</span></span>

     <span data-ttu-id="9b084-109">app.config 파일이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="9b084-109">If there is no app.config file:</span></span>

    1. <span data-ttu-id="9b084-110">**프로젝트** 메뉴에서 **새 항목 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-110">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="9b084-111">**새 항목 추가** 대화 상자에서 **애플리케이션 구성 파일** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-111">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="9b084-112">**추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-112">Click **Add**.</span></span>

2. <span data-ttu-id="9b084-113">애플리케이션 구성 파일에서 `<listeners>` 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-113">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="9b084-114">최상위 \<listeners> 섹션 아래의 \<source> 섹션 아래에서 이름 특성이 "DefaultSource"인 \<system.diagnostics> 섹션에 \<configuration> 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-114">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="9b084-115">다음 요소를 `<listeners>` 섹션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-115">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="9b084-116">최상위 `<configuration>` 섹션 아래에 중첩된 `<system.diagnostics>` 섹션에서 `<sharedListeners>` 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-116">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="9b084-117">다음 요소를 `<sharedListeners>` 섹션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-117">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="9b084-118">`customlocation` 특성의 값을 로그 디렉터리로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-118">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b084-119">수신기 속성의 값을 설정하려면 속성과 이름이 같고 이름에 있는 모든 문자가 소문자인 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-119">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="9b084-120">예를 들어 `location` 및 `customlocation` 특성은 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> 및 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> 속성의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-120">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="9b084-121">이벤트 정보를 파일 로그에 쓰려면</span><span class="sxs-lookup"><span data-stu-id="9b084-121">To write event information to the file log</span></span>

<span data-ttu-id="9b084-122">`My.Application.Log.WriteEntry` 또는 `My.Application.Log.WriteException` 메서드를 사용하여 파일 로그에 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-122">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="9b084-123">자세한 내용은 [방법: 로그 메시지 쓰기](how-to-write-log-messages.md) 및 [방법: 예외 기록](how-to-log-exceptions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b084-123">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="9b084-124">어셈블리에 대한 파일 로그 수신기를 구성하면 수신기는 `My.Application.Log`가 해당 어셈블리에서 쓰는 모든 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="9b084-124">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b084-125">참조</span><span class="sxs-lookup"><span data-stu-id="9b084-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="9b084-126">애플리케이션 로그 작업</span><span class="sxs-lookup"><span data-stu-id="9b084-126">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="9b084-127">방법: 로그 예외</span><span class="sxs-lookup"><span data-stu-id="9b084-127">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
