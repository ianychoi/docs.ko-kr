---
title: CLR ETW 공급자
description: 두 개의 CLR (공용 언어 런타임) ETW (Windows 용 이벤트 추적) 공급자 (runtimne 공급자 및 런다운 공급자)에 대 한 세부 정보를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: f537a2e0557f1b0434d1f303d74f9cd48f157edc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283876"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="ccaad-103">CLR ETW 공급자</span><span class="sxs-lookup"><span data-stu-id="ccaad-103">CLR ETW Providers</span></span>

<span data-ttu-id="ccaad-104">CLR(공용 언어 런타임)에는 런타임 공급자 및 런다운 공급자라는 두 개의 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-104">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="ccaad-105">런타임 공급자는 사용하도록 설정된 키워드(이벤트 범주)에 따라 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-105">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="ccaad-106">예를 들어 `LoaderKeyword` 키워드를 사용하도록 설정하면 로더 이벤트를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-106">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="ccaad-107">ETW (ETW(Windows용 이벤트 추적)) 이벤트는 확장명이 .etl 인 파일에 기록 되며, 나중에 필요에 따라 쉼표로 구분 된 값 (.csv) 파일에서 나중에 처리 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-107">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="ccaad-108">.etl 파일을 .csv 파일로 변환하는 방법에 대한 자세한 내용은 [.NET Framework 로깅 제어](controlling-logging.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccaad-108">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="ccaad-109">런타임 공급자</span><span class="sxs-lookup"><span data-stu-id="ccaad-109">The Runtime Provider</span></span>  

 <span data-ttu-id="ccaad-110">런타임 공급자는 기본 CLR ETW 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-110">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="ccaad-111">CLR 런타임 공급자 GUID는 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4입니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-111">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="ccaad-112">일반적으로 사용 가능한 도구를 사용하여 CLR ETW 이벤트를 기록하고 보는 방법의 예제는 [.NET Framework 로깅 제어](controlling-logging.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccaad-112">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
 <span data-ttu-id="ccaad-113">`LoaderKeyword` 등의 키워드 사용 외에도 너무 자주 발생할 수 있는 이벤트를 기록하기 위해 키워드를 사용하도록 설정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-113">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="ccaad-114">이러한 이벤트는 `StartEnumerationKeyword` 및 `EndEnumerationKeyword` 키워드에 의해 활성화되며 두 키워드는 [CLR ETW 키워드 및 수준](clr-etw-keywords-and-levels.md)에 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-114">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="ccaad-115">런다운 공급자</span><span class="sxs-lookup"><span data-stu-id="ccaad-115">The Rundown Provider</span></span>  

 <span data-ttu-id="ccaad-116">특별한 용도에 사용하려면 런다운 공급자를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-116">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="ccaad-117">그러나 대부분의 사용자는 런타임 공급자로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-117">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="ccaad-118">CLR 런다운 공급자 GUID는 A669021C-C450-4609-A035-5AF59AF4DF18입니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-118">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="ccaad-119">일반적으로 ETW 로깅은 프로세스가 시작되기 전에 사용되고, 프로세스가 종료된 후 로깅이 꺼집니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-119">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="ccaad-120">그러나 프로세스를 실행하는 동안 ETW 로깅이 켜져 있는 경우 프로세스에 대한 추가 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-120">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="ccaad-121">예를 들어 기호를 확인하려면 로깅을 켜기 전에 이미 로드된 메서드에 대한 메서드 이벤트를 기록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-121">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="ccaad-122">`DCStart` 및 `DCEnd` 이벤트는 데이터 수집이 시작 및 중지될 때 프로세스의 상태를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-122">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="ccaad-123">상태는 이미 JIT (just-in-time) 컴파일 되었으며 로드 된 어셈블리를 포함 하 여 높은 수준의 정보를 나타냅니다. 이러한 두 이벤트는 프로세스에서 이미 발생 한 상황에 대 한 정보를 제공할 수 있습니다. 예를 들어 JIT로 컴파일된 메서드 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-123">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="ccaad-124">`DC`, `DCStart`, `DCEnd` 또는 `DCInit`가 이름에 포함된 이벤트만 런다운 공급자 아래에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-124">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="ccaad-125">또한 이들 이벤트는 런다운 공급자에서만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-125">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="ccaad-126">이벤트 키워드 필터 외에도 런다운 공급자는 대상 필터링을 제공하는 `StartRundownKeyword` 및 `EndRundownKeyword` 키워드도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-126">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="ccaad-127">시작 런다운</span><span class="sxs-lookup"><span data-stu-id="ccaad-127">Start Rundown</span></span>  

 <span data-ttu-id="ccaad-128">시작 런다운은 런다운 공급자 아래의 로깅이 `StartRundownKeyword` 키워드로 활성화된 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-128">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="ccaad-129">이 경우 `DCStart`가 발생하고 시스템 상태가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-129">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="ccaad-130">열거를 시작하기 전에 `DCStartInit` 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-130">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="ccaad-131">열거형의 끝에는 `DCStartComplete` 이벤트가 발생하여 데이터 수집이 정상적으로 종료되었음을 컨트롤러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-131">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="ccaad-132">끝 런다운</span><span class="sxs-lookup"><span data-stu-id="ccaad-132">End Rundown</span></span>  

 <span data-ttu-id="ccaad-133">끝 런다운은 런다운 공급자 아래의 로깅이 `EndRundownKeyword` 키워드로 활성화된 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-133">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="ccaad-134">끝 런다운은 계속 실행되는 프로세스에 대한 프로파일링을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-134">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="ccaad-135">`DCEnd` 이벤트는 프로파일링이 중지될 때의 시스템 상태를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-135">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="ccaad-136">열거를 시작하기 전에 `DCEndInit` 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-136">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="ccaad-137">열거형의 끝에는 `DCEndComplete` 이벤트가 발생하여 데이터 수집이 정상적으로 종료되었음을 소비자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-137">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="ccaad-138">시작 런다운 및 끝 런다운은 주로 관리되는 기호 확인에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-138">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="ccaad-139">시작 런다운은 프로파일링 세션이 시작되기 전에 이미 JIT 컴파일된 메서드에 대한 주소 범위 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-139">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="ccaad-140">끝 런다운은 프로파일링을 끌 때 JIT 컴파일된 모든 메서드에 대한 주소 범위 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-140">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="ccaad-141">끝 런다운은 프로파일링 세션을 중지할 때 자동으로 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-141">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="ccaad-142">대신, 프로파일링이 중지되기 직전에 관리되는 기호 확인을 수행하려는 도구가 `EndRundownKeyword` 키워드를 사용하여 CLR 런다운 공급자 세션을 명시적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-142">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="ccaad-143">시작 런다운 또는 끝 런다운은 관리되는 기호 확인을 위해 메서드 주소 범위 정보를 제공할 수 있지만 `StartRundownKeyword` 키워드(`DCStart` 이벤트 제공) 대신 `EndRundownKeyword` 키워드(`DCEnd` 이벤트 제공)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-143">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="ccaad-144">`StartRundownKeyword`를 사용하면 프로파일링 세션 중에 런다운이 발생하며 프로파일링된 시나리오를 방해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-144">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="ccaad-145">런타임 및 런다운 공급자를 사용한 ETW 데이터 수집</span><span class="sxs-lookup"><span data-stu-id="ccaad-145">ETW Data Collection Using Runtime and Rundown Providers</span></span>  

 <span data-ttu-id="ccaad-146">다음 예제에서는 프로세스가 프로파일링된 창 내부 또는 외부에서 시작 또는 종료되는지에 관계없이 최소한의 영향으로 관리되는 프로세스의 기호 확인을 허용하는 방식으로 CLR 런다운 공급자를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-146">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="ccaad-147">CLR 런타임 공급자를 사용하여 ETW 로깅 켜기:</span><span class="sxs-lookup"><span data-stu-id="ccaad-147">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     <span data-ttu-id="ccaad-148">로그는 clr1.etl 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-148">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="ccaad-149">프로세스를 계속 실행하는 동안 프로파일링을 중지하려면 런다운 공급자를 시작하여 `DCEnd` 이벤트를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-149">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     <span data-ttu-id="ccaad-150">이렇게 하면 `DCEnd` 이벤트 컬렉션이 런다운 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-150">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="ccaad-151">모든 이벤트가 수집되도록 30-60초 기다려야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-151">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="ccaad-152">로그는 clr1.et2 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-152">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="ccaad-153">모든 ETW 프로파일링 끄기:</span><span class="sxs-lookup"><span data-stu-id="ccaad-153">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="ccaad-154">프로필을 병합하여 하나의 로그 파일 만들기:</span><span class="sxs-lookup"><span data-stu-id="ccaad-154">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="ccaad-155">merged.etl 파일에는 런타임 및 런다운 공급자 세션의 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-155">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="ccaad-156">도구는 사용자가 프로파일링 중지를 요청할 때 프로파일링을 즉시 끄지 않고 2단계와 3단계(런다운 세션을 시작한 다음 프로파일링 종료)를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-156">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="ccaad-157">도구에서 4단계를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccaad-157">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccaad-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccaad-158">See also</span></span>

- [<span data-ttu-id="ccaad-159">공용 언어 런타임의 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="ccaad-159">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
