---
title: '방법: 서비스에 대한 정보 로깅'
description: 서비스에 대한 정보를 로깅하는 방법을 알아봅니다. Windows 서비스 프로젝트가 애플리케이션 이벤트 로그와 상호 작용하도록 하려면 AutoLog 속성을 설정합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
ms.openlocfilehash: 2e5f1fd8ebbbb218e8d6eba9b2d30d05e7c0e62c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270578"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="1063a-104">방법: 서비스에 대한 정보 로깅</span><span class="sxs-lookup"><span data-stu-id="1063a-104">How to: Log Information About Services</span></span>

<span data-ttu-id="1063a-105">기본적으로 모든 Windows 서비스 프로젝트는 애플리케이션 이벤트 로그와 상호 작용하고 이 로그에 정보 및 예외를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-105">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="1063a-106"><xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 사용하여 애플리케이션에서 이 기능을 표시할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-106">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="1063a-107">기본적으로, 로깅은 Windows 서비스 프로젝트 템플릿으로 만드는 모든 서비스에 대해 사용 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-107">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="1063a-108"><xref:System.Diagnostics.EventLog> 클래스의 정적 형식을 사용하면 <xref:System.Diagnostics.EventLog> 구성 요소의 인스턴스를 만들거나 소스를 수동으로 등록하지 않고도 로그에 서비스 정보를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-108">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="1063a-109">서비스가 설치되어 있는 컴퓨터에 로깅이 사용 설정되어 있으면, 서비스 설치 관리자가 애플리케이션 로그를 사용하여 각 서비스를 유효한 이벤트 소스로 프로젝트에 자동으로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-109">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="1063a-110">서비스가 시작, 중지, 일시 중지, 다시 시작, 설치 또는 제거될 때마다 서비스가 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-110">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="1063a-111">발생되는 오류도 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-111">It also logs any failures that occur.</span></span> <span data-ttu-id="1063a-112">기본 동작을 사용하는 경우에는 로그에 항목을 쓰기 위해 코드를 작성할 필요가 없습니다. 서비스가 자동으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-112">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="1063a-113">애플리케이션 로그가 아닌 이벤트 로그에 작성하려면 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 `false`로 설정하고, 서비스 코드 내에 사용자 지정 이벤트 로그를 만들고, 해당 로그에 대한 유효한 항목 소스로 서비스를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-113">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="1063a-114">그런 다음 원하는 작업이 발생할 때마다 항목을 로그에 기록할 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-114">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1063a-115">사용자 지정 이벤트 로그를 사용하고 서비스 애플리케이션이 이 로그에 기록되도록 구성하는 경우, 코드에서 서비스의 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 속성을 설정하기 전에 이벤트 로그에 액세스를 시도하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-115">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="1063a-116">서비스가 유효한 이벤트 소스로 등록되려면 이벤트 로그에 이 속성 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-116">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="1063a-117">서비스에 대해 기본 이벤트 로깅을 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="1063a-117">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="1063a-118">구성 요소의 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-118">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1063a-119">기본적으로 이 속성은 `true`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-119">By default, this property is set to `true`.</span></span> <span data-ttu-id="1063a-120">조건을 평가한 다음 조건의 결과를 기반으로 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 설정하는 것과 같이 복잡한 프로세스를 구축하는 경우가 아니라면 이 속성을 명시적으로 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-120">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="1063a-121">서비스에 대해 이벤트 로깅을 비활성화하려면</span><span class="sxs-lookup"><span data-stu-id="1063a-121">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="1063a-122">구성 요소의 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="1063a-123">사용자 지정 로그에 로깅을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1063a-123">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="1063a-124"><xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 속성을 `false`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-124">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1063a-125">사용자 지정 로그를 사용하려면 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 를 false로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-125">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="1063a-126">Windows 서비스 애플리케이션에서 <xref:System.Diagnostics.EventLog> 구성 요소의 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-126">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="1063a-127"><xref:System.Diagnostics.EventLog.CreateEventSource%2A> 메서드를 호출하고 만들려는 로그 파일의 이름과 소스 문자열을 지정하여 사용자 지정 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-127">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="1063a-128"><xref:System.Diagnostics.EventLog.Source%2A> 구성 요소 인스턴스의 <xref:System.Diagnostics.EventLog> 속성을 3단계에서 만든 소스 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-128">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="1063a-129"><xref:System.Diagnostics.EventLog.WriteEntry%2A> 구성 요소 인스턴스의 <xref:System.Diagnostics.EventLog> 메서드에 액세스하여 항목을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-129">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="1063a-130">다음 코드에서는 사용자 지정 로그에 로깅을 설정하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-130">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1063a-131">이 코드 예제에서 <xref:System.Diagnostics.EventLog> 구성 요소의 인스턴스 이름은 `eventLog1` (Visual Basic의 경우`EventLog1` )입니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-131">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="1063a-132">2단계에서 다른 이름의 인스턴스를 만든 경우에는 그에 따라 코드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1063a-132">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1063a-133">참조</span><span class="sxs-lookup"><span data-stu-id="1063a-133">See also</span></span>

- [<span data-ttu-id="1063a-134">Windows 서비스 애플리케이션 소개</span><span class="sxs-lookup"><span data-stu-id="1063a-134">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
