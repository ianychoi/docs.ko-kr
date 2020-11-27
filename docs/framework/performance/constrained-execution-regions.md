---
title: 제약이 있는 실행 지역
description: 신뢰할 수 있는 관리 코드를 작성 하기 위한 메커니즘의 일부인 CER (제약이 있는 실행 영역)을 시작 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
ms.openlocfilehash: 5014885e186b1fff16543c09d5652958f2463e3d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266859"
---
# <a name="constrained-execution-regions"></a><span data-ttu-id="ebd23-103">제약이 있는 실행 지역</span><span class="sxs-lookup"><span data-stu-id="ebd23-103">Constrained Execution Regions</span></span>

<span data-ttu-id="ebd23-104">CER(제약이 있는 실행 영역)은 신뢰할 수 있는 관리 코드를 작성하기 위한 메커니즘에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-104">A constrained execution region (CER) is part of a mechanism for authoring reliable managed code.</span></span> <span data-ttu-id="ebd23-105">CER은 CLR(공용 언어 런타임 지원)이 영역의 전체 코드가 실행되지 않도록 하는 대역 외 예외를 throw하지 못하도록 제한되는 영역을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-105">A CER defines an area in which the common language runtime (CLR) is constrained from throwing out-of-band exceptions that would prevent the code in the area from executing in its entirety.</span></span> <span data-ttu-id="ebd23-106">해당 영역 내에서 사용자 코드는 대역 외 예외 throw를 초래하는 실행이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-106">Within that region, user code is constrained from executing code that would result in the throwing of out-of-band exceptions.</span></span> <span data-ttu-id="ebd23-107"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 메서드는 `try` 블록 바로 앞에 와야 하고 `catch`, `finally` 및 `fault` 블록을 제약이 있는 실행 영역으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-107">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method must immediately precede a `try` block and marks `catch`, `finally`, and `fault` blocks as constrained execution regions.</span></span> <span data-ttu-id="ebd23-108">제약이 있는 영역으로 표시된 후 코드는 강한 안정성 계약을 사용하여 다른 코드를 호출해야 하고 코드는 실패를 처리할 준비가 된 경우에만 준비되지 않거나 신뢰할 수 없는 메서드에 대한 가상 호출을 할당하거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-108">Once marked as a constrained region, code must only call other code with strong reliability contracts, and code should not allocate or make virtual calls to unprepared or unreliable methods unless the code is prepared to handle failures.</span></span> <span data-ttu-id="ebd23-109">CLR은 CER에서 실행되는 코드의 스레드 중단을 지연합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-109">The CLR delays thread aborts for code that is executing in a CER.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="ebd23-110">CER은 .NET Framework 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-110">CER is only supported in .NET Framework.</span></span> <span data-ttu-id="ebd23-111">이 문서는 .NET Core 또는 .NET 5 이상에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-111">This article doesn't apply to .NET Core or .NET 5 and above.</span></span>

 <span data-ttu-id="ebd23-112">제약이 있는 실행 영역은 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 메서드를 사용하여 실행된 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> 클래스 및 코드에서 파생된 클래스에서 실행되는 특히 중요한 종료자인 주석이 달린 `try` 블록 이외에 CLR의 다양한 형식으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-112">Constrained execution regions are used in different forms in the CLR in addition to an annotated `try` block, notably critical finalizers executing in classes derived from the <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> class and code executed using the <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> method.</span></span>  
  
## <a name="cer-advance-preparation"></a><span data-ttu-id="ebd23-113">CER 사전 준비</span><span class="sxs-lookup"><span data-stu-id="ebd23-113">CER Advance Preparation</span></span>  

 <span data-ttu-id="ebd23-114">CLR은 메모리 부족 조건을 피하기 위해 사전에 CER을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-114">The CLR prepares CERs in advance to avoid out-of-memory conditions.</span></span> <span data-ttu-id="ebd23-115">CLR이 Just-In-Time 컴파일 또는 형식 로딩 중에 메모리 부족 조건을 초래하지 않으려면 사전 준비가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-115">Advance preparation is required so the CLR does not cause an out of memory condition during just-in-time compilation or type loading.</span></span>  
  
 <span data-ttu-id="ebd23-116">개발자는 코드 영역이 CER임을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-116">The developer is required to indicate that a code region is a CER:</span></span>  
  
- <span data-ttu-id="ebd23-117"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 특성이 적용된 전체 호출 그래프의 최상위 CER 영역 및 메서드는 사전에 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-117">The top level CER region and methods in the full call graph that have the <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> attribute applied are prepared in advance.</span></span> <span data-ttu-id="ebd23-118"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>는 <xref:System.Runtime.ConstrainedExecution.Cer.Success> 또는 <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>의 보장만 명시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-118">The <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> can only state guarantees of <xref:System.Runtime.ConstrainedExecution.Cer.Success> or <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span></span>  
  
- <span data-ttu-id="ebd23-119">가상 디스패치와 같이 정적으로 결정될 수 없는 호출의 경우 사전 준비를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-119">Advance preparation cannot be performed for calls that cannot be statically determined, such as virtual dispatch.</span></span> <span data-ttu-id="ebd23-120">이 경우 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-120">Use the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method in these cases.</span></span> <span data-ttu-id="ebd23-121"><xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 메서드를 사용할 경우 <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> 특성을 정리 코드에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-121">When using the <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> method, the <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> attribute should be applied to the clean up code.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="ebd23-122">제약 조건</span><span class="sxs-lookup"><span data-stu-id="ebd23-122">Constraints</span></span>  

 <span data-ttu-id="ebd23-123">사용자는 CER에서 작성할 수 있는 코드 형식이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-123">Users are constrained in the type of code they can write in a CER.</span></span> <span data-ttu-id="ebd23-124">코드는 다음 작업에서 발생할 수 있는 것과 같은 대역 외 예외를 초래할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-124">The code cannot cause an out-of-band exception, such as might result from the following operations:</span></span>  
  
- <span data-ttu-id="ebd23-125">명시적 할당</span><span class="sxs-lookup"><span data-stu-id="ebd23-125">Explicit allocation.</span></span>  
  
- <span data-ttu-id="ebd23-126">Boxing</span><span class="sxs-lookup"><span data-stu-id="ebd23-126">Boxing.</span></span>  
  
- <span data-ttu-id="ebd23-127">잠금 획득</span><span class="sxs-lookup"><span data-stu-id="ebd23-127">Acquiring a lock.</span></span>  
  
- <span data-ttu-id="ebd23-128">가상으로 준비되지 않은 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="ebd23-128">Calling unprepared methods virtually.</span></span>  
  
- <span data-ttu-id="ebd23-129">약하거나 존재하지 않는 안전성 계약을 사용하여 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="ebd23-129">Calling methods with a weak or nonexistent reliability contract.</span></span>  
  
 <span data-ttu-id="ebd23-130">.NET Framework 버전 2.0에서 이러한 제약 조건은 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-130">In the .NET Framework version 2.0, these constraints are guidelines.</span></span> <span data-ttu-id="ebd23-131">진단은 코드 분석 도구를 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-131">Diagnostics are provided through code analysis tools.</span></span>  
  
## <a name="reliability-contracts"></a><span data-ttu-id="ebd23-132">안정성 계약</span><span class="sxs-lookup"><span data-stu-id="ebd23-132">Reliability Contracts</span></span>  

 <span data-ttu-id="ebd23-133"><xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>는 특정 메서드의 안전성 보장 및 손상 상태를 설명하는 사용자 지정 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-133">The <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> is a custom attribute that documents the reliability guarantees and the corruption state of a given method.</span></span>  
  
### <a name="reliability-guarantees"></a><span data-ttu-id="ebd23-134">안전성 보장</span><span class="sxs-lookup"><span data-stu-id="ebd23-134">Reliability Guarantees</span></span>  

 <span data-ttu-id="ebd23-135"><xref:System.Runtime.ConstrainedExecution.Cer> 열거 값을 통해 표현되는 안전성 보장은 특정 메서드의 안정성 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-135">Reliability guarantees, represented by <xref:System.Runtime.ConstrainedExecution.Cer> enumeration values, indicate the degree of reliability of a given method:</span></span>  
  
- <span data-ttu-id="ebd23-136"><xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-136"><xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.</span></span> <span data-ttu-id="ebd23-137">예외 조건에서 메서드가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-137">Under exceptional conditions, the method might fail.</span></span> <span data-ttu-id="ebd23-138">이 경우 메서드는 성공 여부를 호출 메서드에 다시 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-138">In this case, the method reports back to the calling method whether it succeeded or failed.</span></span> <span data-ttu-id="ebd23-139">반환 값을 보고할 수 있으려면 메서드가 CER에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-139">The method must be contained in a CER to ensure that it can report the return value.</span></span>  
  
- <span data-ttu-id="ebd23-140"><xref:System.Runtime.ConstrainedExecution.Cer.None>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-140"><xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="ebd23-141">메서드, 형식 또는 어셈블리에는 CER 개념이 없으며 상태 손상으로 인한 큰 완화 없이 CER 내에서 호출하기에 안전하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-141">The method, type, or assembly has no concept of a CER and is most likely not safe to call within a CER without substantial mitigation from state corruption.</span></span> <span data-ttu-id="ebd23-142">CER 보장의 장점을 활용하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-142">It does not take advantage of CER guarantees.</span></span> <span data-ttu-id="ebd23-143">이것은 다음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-143">This implies the following:</span></span>  
  
    1. <span data-ttu-id="ebd23-144">예외 조건에서 메서드가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-144">Under exceptional conditions the method might fail.</span></span>  
  
    2. <span data-ttu-id="ebd23-145">메서드는 실패 사실을 보고할 수도 있고 보고하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-145">The method might or might not report that it failed.</span></span>  
  
    3. <span data-ttu-id="ebd23-146">메서드는 CER을 사용하도록 작성되지 않을 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-146">The method is not written to use a CER, the most likely scenario.</span></span>  
  
    4. <span data-ttu-id="ebd23-147">메서드, 형식 또는 어셈블리가 성공한 것으로 명시적으로 식별되지 않으면 암시적으로 <xref:System.Runtime.ConstrainedExecution.Cer.None>으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-147">If a method, type, or assembly is not explicitly identified to succeed, it is implicitly identified as <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span>  
  
- <span data-ttu-id="ebd23-148"><xref:System.Runtime.ConstrainedExecution.Cer.Success>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-148"><xref:System.Runtime.ConstrainedExecution.Cer.Success>.</span></span> <span data-ttu-id="ebd23-149">예외 조건에서 메서드가 성공하도록 보장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-149">Under exceptional conditions, the method is guaranteed to succeed.</span></span> <span data-ttu-id="ebd23-150">이 안전성 수준을 획득하려면 CER이 아닌 영역 내에서 호출되는 경우에도 항상 호출되는 메서드 주위에 CER을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-150">To achieve this level of reliability you should always construct a CER around the method that is called, even when it is called from within a non-CER region.</span></span> <span data-ttu-id="ebd23-151">성공을 주관적으로 볼 수 있더라도 메서드가 의도된 작업을 수행하면 성공한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-151">A method is successful if it accomplishes what is intended, although success can be viewed subjectively.</span></span> <span data-ttu-id="ebd23-152">예를 들어 `ReliabilityContractAttribute(Cer.Success)`를 사용하여 Count를 표시하는 것은 CER에서 실행되는 경우 항상 <xref:System.Collections.ArrayList>에 있는 요소 수를 반환하고 내부 필드를 결정되지 않은 상태로 남겨 두지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-152">For example, marking Count with `ReliabilityContractAttribute(Cer.Success)` implies that when it is run under a CER, it always returns a count of the number of elements in the <xref:System.Collections.ArrayList> and it can never leave the internal fields in an undetermined state.</span></span>  <span data-ttu-id="ebd23-153">그러나 성공의 경우 값이 경합 상태로 인해 새 값으로 대체될 수 없음을 의미할 수도 있다는 것을 이해하면 <xref:System.Threading.Interlocked.CompareExchange%2A> 메서드가 성공으로도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-153">However, the <xref:System.Threading.Interlocked.CompareExchange%2A> method is marked as success as well, with the understanding that success may mean the value could not be replaced with a new value due to a race condition.</span></span>  <span data-ttu-id="ebd23-154">핵심 포인트는 메서드가 설명된 방식대로 동작하고 CER 코드가 올바르지만 신뢰할 수 없는 코드가 어떻게 보이는지에 관계없이 비정상적인 동작을 예상하도록 작성될 필요가 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-154">The key point is that the method behaves in the way it is documented to behave, and CER code does not need to be written to expect any unusual behavior beyond what correct but unreliable code would look like.</span></span>  
  
### <a name="corruption-levels"></a><span data-ttu-id="ebd23-155">손상 수준</span><span class="sxs-lookup"><span data-stu-id="ebd23-155">Corruption levels</span></span>  

 <span data-ttu-id="ebd23-156"><xref:System.Runtime.ConstrainedExecution.Consistency> 열거 값을 통해 표현되는 손상 수준은 상태가 특정 환경에서 손상될 수 있는 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-156">Corruption levels, represented by <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration values, indicate how much state may be corrupted in a given environment:</span></span>  
  
- <span data-ttu-id="ebd23-157"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-157"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>.</span></span> <span data-ttu-id="ebd23-158">예외 조건에서 CLR(공용 언어 런타임)이 현재 애플리케이션 도메인에서 상태 일관성에 관한 보장을 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-158">Under exceptional conditions, the common language runtime (CLR) makes no guarantees regarding state consistency in the current application domain.</span></span>  
  
- <span data-ttu-id="ebd23-159"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-159"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>.</span></span> <span data-ttu-id="ebd23-160">예외 조건에서 메서드가 상태 손상을 현재 인스턴스로 제한하도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-160">Under exceptional conditions, the method is guaranteed to limit state corruption to the current instance.</span></span>  
  
- <span data-ttu-id="ebd23-161"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>. 예외 조건에서 CLR은 상태 일관성에 관한 보장을 하지 않습니다. 즉, 조건이 프로세스를 손상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-161"><xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Under exceptional conditions, the CLR makes no guarantees regarding state consistency; that is, the condition might corrupt the process.</span></span>  
  
- <span data-ttu-id="ebd23-162"><xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>.</span><span class="sxs-lookup"><span data-stu-id="ebd23-162"><xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>.</span></span> <span data-ttu-id="ebd23-163">예외 조건에서 메서드가 상태를 손상시키지 않도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-163">Under exceptional conditions, the method is guaranteed not to corrupt state.</span></span>  
  
## <a name="reliability-trycatchfinally"></a><span data-ttu-id="ebd23-164">안전성 try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="ebd23-164">Reliability try/catch/finally</span></span>  

 <span data-ttu-id="ebd23-165">안전성 `try/catch/finally`는 관리되지 않는 버전과 동일한 수준의 예측 가능성 보장을 사용하는 예외 처리 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-165">The reliability `try/catch/finally` is an exception handling mechanism with the same level of predictability guarantees as the unmanaged version.</span></span> <span data-ttu-id="ebd23-166">`catch/finally` 블록은 CER입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-166">The `catch/finally` block is the CER.</span></span> <span data-ttu-id="ebd23-167">블록에 있는 메서드의 경우 사전 준비가 필요하고 중단할 수 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-167">Methods in the block require advance preparation and must be noninterruptible.</span></span>  
  
 <span data-ttu-id="ebd23-168">.NET Framework 버전 2.0에서 코드는 try 블록 바로 전에 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>를 호출하여 try를 신뢰할 수 있음을 런타임에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-168">In the .NET Framework version 2.0, code informs the runtime that a try is reliable by calling <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> immediately preceding a try block.</span></span> <span data-ttu-id="ebd23-169"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>는 컴파일러 지원 클래스인 <xref:System.Runtime.CompilerServices.RuntimeHelpers>의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-169"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> is a member of <xref:System.Runtime.CompilerServices.RuntimeHelpers>, a compiler support class.</span></span> <span data-ttu-id="ebd23-170">컴파일러를 통해 가성을 보류하여 직접 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-170">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> directly pending its availability through compilers.</span></span>  
  
## <a name="noninterruptible-regions"></a><span data-ttu-id="ebd23-171">중단할 수 없는 영역</span><span class="sxs-lookup"><span data-stu-id="ebd23-171">Noninterruptible Regions</span></span>  

 <span data-ttu-id="ebd23-172">중단할 수 없는 영역은 명령 집합을 CER로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-172">A noninterruptible region groups a set of instructions into a CER.</span></span>  
  
 <span data-ttu-id="ebd23-173">.NET Framework 버전 2.0에서 컴파일러 지원을 통해 가용성을 보류하면 사용자 코드는 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 메서드 호출 뒤에 빈 try/catch가 포함된 신뢰할 수 있는 try/catch/finally를 사용하여 중단할 수 없는 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-173">In .NET Framework version 2.0, pending availability through compiler support, user code creates non-interruptible regions with a reliable try/catch/finally that contains an empty try/catch block preceded by a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call.</span></span>  
  
## <a name="critical-finalizer-object"></a><span data-ttu-id="ebd23-174">중요 종료자 개체</span><span class="sxs-lookup"><span data-stu-id="ebd23-174">Critical Finalizer Object</span></span>  

 <span data-ttu-id="ebd23-175"><xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>는 가비지 수집이 종료자를 실행하도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-175">A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> guarantees that garbage collection will execute the finalizer.</span></span> <span data-ttu-id="ebd23-176">할당 시 종료자 및 해당 호출 그래프는 사전에 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-176">Upon allocation, the finalizer and its call graph are prepared in advance.</span></span> <span data-ttu-id="ebd23-177">종료자 메서드는 CER에서 실행되고 CER 및 종료자에 대한 모든 제약 조건을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-177">The finalizer method executes in a CER, and must obey all the constraints on CERs and finalizers.</span></span>  
  
 <span data-ttu-id="ebd23-178"><xref:System.Runtime.InteropServices.SafeHandle> 및 <xref:System.Runtime.InteropServices.CriticalHandle>에서 상속되는 모든 형식은 CER 내에 종료자 실행이 포함되도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-178">Any types inheriting from <xref:System.Runtime.InteropServices.SafeHandle> and <xref:System.Runtime.InteropServices.CriticalHandle> are guaranteed to have their finalizer execute within a CER.</span></span> <span data-ttu-id="ebd23-179">핸들을 해제하는 데 필요한 코드를 실행하도록 <xref:System.Runtime.InteropServices.SafeHandle> 파생 클래스에서 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-179">Implement <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> in <xref:System.Runtime.InteropServices.SafeHandle> derived classes to execute any code that is required to free the handle.</span></span>  
  
## <a name="code-not-permitted-in-cers"></a><span data-ttu-id="ebd23-180">CER에서 허용되지 않는 코드</span><span class="sxs-lookup"><span data-stu-id="ebd23-180">Code Not Permitted in CERs</span></span>  

 <span data-ttu-id="ebd23-181">다음 작업은 CER에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-181">The following operations are not permitted in CERs:</span></span>  
  
- <span data-ttu-id="ebd23-182">명시적 할당.</span><span class="sxs-lookup"><span data-stu-id="ebd23-182">Explicit allocations.</span></span>  
  
- <span data-ttu-id="ebd23-183">잠금 획득</span><span class="sxs-lookup"><span data-stu-id="ebd23-183">Acquiring a lock.</span></span>  
  
- <span data-ttu-id="ebd23-184">Boxing</span><span class="sxs-lookup"><span data-stu-id="ebd23-184">Boxing.</span></span>  
  
- <span data-ttu-id="ebd23-185">다차원 배열 액세스.</span><span class="sxs-lookup"><span data-stu-id="ebd23-185">Multidimensional array access.</span></span>  
  
- <span data-ttu-id="ebd23-186">리플렉션을 통한 메서드 호출.</span><span class="sxs-lookup"><span data-stu-id="ebd23-186">Method calls through reflection.</span></span>  
  
- <span data-ttu-id="ebd23-187"><xref:System.Threading.Monitor.Enter%2A> 또는 <xref:System.IO.FileStream.Lock%2A></span><span class="sxs-lookup"><span data-stu-id="ebd23-187"><xref:System.Threading.Monitor.Enter%2A> or <xref:System.IO.FileStream.Lock%2A>.</span></span>  
  
- <span data-ttu-id="ebd23-188">보안 검사.</span><span class="sxs-lookup"><span data-stu-id="ebd23-188">Security checks.</span></span> <span data-ttu-id="ebd23-189">링크 요청만 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebd23-189">Do not perform demands, only link demands.</span></span>  
  
- <span data-ttu-id="ebd23-190">COM 개체 및 프록시에 대한 <xref:System.Reflection.Emit.OpCodes.Isinst> 및 <xref:System.Reflection.Emit.OpCodes.Castclass></span><span class="sxs-lookup"><span data-stu-id="ebd23-190"><xref:System.Reflection.Emit.OpCodes.Isinst> and <xref:System.Reflection.Emit.OpCodes.Castclass> for COM objects and proxies</span></span>  
  
- <span data-ttu-id="ebd23-191">투명 프록시에 대한 필드 가져오기 또는 설정.</span><span class="sxs-lookup"><span data-stu-id="ebd23-191">Getting or setting fields on a transparent proxy.</span></span>  
  
- <span data-ttu-id="ebd23-192">serialization.</span><span class="sxs-lookup"><span data-stu-id="ebd23-192">Serialization.</span></span>  
  
- <span data-ttu-id="ebd23-193">함수 포인터 및 대리자.</span><span class="sxs-lookup"><span data-stu-id="ebd23-193">Function pointers and delegates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd23-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ebd23-194">See also</span></span>

- [<span data-ttu-id="ebd23-195">안전성 모범 사례</span><span class="sxs-lookup"><span data-stu-id="ebd23-195">Reliability Best Practices</span></span>](reliability-best-practices.md)
