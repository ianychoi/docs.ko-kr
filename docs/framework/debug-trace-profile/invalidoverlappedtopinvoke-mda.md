---
title: invalidOverlappedToPinvoke MDA
description: 크래시 또는 unexplainable 힙 손상 중에 활성화 될 수 있는 .NET의 invalidOverlappedToPinvoke MDA (관리 디버깅 도우미)를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 55b10af87130bd32410508cef2bc3e4e733549c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281327"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="f9cef-103">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="f9cef-103">invalidOverlappedToPinvoke MDA</span></span>

<span data-ttu-id="f9cef-104">`invalidOverlappedToPinvoke` MDA(관리 디버깅 도우미)는 가비지 수집 힙에서 만들어지지 않은 겹치는 포인터가 특정 Win32 함수에 전달되면 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9cef-105">기본적으로 P/Invoke 호출이 코드에 정의되어 있고 디버거가 각 메서드의 JustMyCode 상태를 보고하는 경우에만 이 MDA가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="f9cef-106">JustMyCode(예: 확장명이 없는 MDbg.exe)를 인식하지 않는 디버거는 이 MDA를 활성화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="f9cef-107">이러한 디버거는 구성 파일을 사용하고 .mda.config 파일에서 `justMyCode="false"`를 설정하여`(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`) 이 MDA를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f9cef-108">증상</span><span class="sxs-lookup"><span data-stu-id="f9cef-108">Symptoms</span></span>  

 <span data-ttu-id="f9cef-109">작동 중단 또는 설명할 수 없는 힙 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f9cef-110">원인</span><span class="sxs-lookup"><span data-stu-id="f9cef-110">Cause</span></span>  

 <span data-ttu-id="f9cef-111">가비지 수집 힙에서 만들어지지 않은 겹치는 포인터가 특정 운영 체제 함수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="f9cef-112">다음 표에서는 이 MDA가 추적하는 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="f9cef-113">모듈</span><span class="sxs-lookup"><span data-stu-id="f9cef-113">Module</span></span>|<span data-ttu-id="f9cef-114">기능</span><span class="sxs-lookup"><span data-stu-id="f9cef-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="f9cef-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="f9cef-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="f9cef-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="f9cef-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="f9cef-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="f9cef-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="f9cef-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="f9cef-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="f9cef-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="f9cef-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="f9cef-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="f9cef-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="f9cef-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="f9cef-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="f9cef-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="f9cef-129">호출을 수행하는 <xref:System.AppDomain>이 언로드될 수 있어 이 조건에서는 힙이 손상될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="f9cef-130"><xref:System.AppDomain>이 언로드되면 애플리케이션 코드는 겹치는 포인터에 대한 메모리를 해제하므로 작업 완료 시 손상이 발생하거나 메모리 누수를 초래하므로 나중에 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f9cef-131">해결 방법</span><span class="sxs-lookup"><span data-stu-id="f9cef-131">Resolution</span></span>  

 <span data-ttu-id="f9cef-132"><xref:System.Threading.Overlapped.Pack%2A> 메서드를 호출하는 <xref:System.Threading.Overlapped> 개체를 사용하여 함수에 전달될 수 있는 <xref:System.Threading.NativeOverlapped> 구조체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="f9cef-133"><xref:System.AppDomain>이 언로드되면 CLR은 포인터를 해제하기 전에 비동기 작업이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f9cef-134">런타임에 대한 영향</span><span class="sxs-lookup"><span data-stu-id="f9cef-134">Effect on the Runtime</span></span>  

 <span data-ttu-id="f9cef-135">MDA는 CLR에 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f9cef-136">출력</span><span class="sxs-lookup"><span data-stu-id="f9cef-136">Output</span></span>  

 <span data-ttu-id="f9cef-137">이 MDA의 출력 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f9cef-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="f9cef-138">구성</span><span class="sxs-lookup"><span data-stu-id="f9cef-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9cef-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9cef-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f9cef-140">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="f9cef-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f9cef-141">interop 마샬링</span><span class="sxs-lookup"><span data-stu-id="f9cef-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
