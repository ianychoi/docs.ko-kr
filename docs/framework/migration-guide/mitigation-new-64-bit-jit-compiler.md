---
title: '마이그레이션: 새로운 64비트 JIT 컴파일러'
description: .NET Framework 4.6에 포함된 새로운 64비트 JIT 컴파일러와 컴파일 중에 발생할 수 있는 예기치 않은 동작 또는 예외 사항에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 228c286f6c5620dc838df5002edc60863a0fe4e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256601"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="58a59-103">완화: 새로운 64비트 JIT 컴파일러</span><span class="sxs-lookup"><span data-stu-id="58a59-103">Mitigation: New 64-bit JIT Compiler</span></span>

<span data-ttu-id="58a59-104">.NET Framework 4.6부터는 런타임에 Just-In-Time 컴파일을 위한 새로운 64비트 JIT 컴파일러가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="58a59-105">이 변경 내용은 32비트 JIT 컴파일러를 사용하는 컴파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="58a59-106">예기치 않은 동작이나 예외</span><span class="sxs-lookup"><span data-stu-id="58a59-106">Unexpected behavior or exceptions</span></span>  

 <span data-ttu-id="58a59-107">경우에 따라 새로운 64비트 JIT 컴파일러를 사용하여 컴파일을 수행하면 이전 64비트 JIT 컴파일러로 컴파일한 코드를 실행할 때 확인되지 않던 런타임 예외 또는 동작이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="58a59-108">알려진 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58a59-109">.NET Framework 4.6.2와 함께 릴리스된 새로운 64비트 컴파일러에서 이러한 모든 알려진 문제가 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="58a59-110">Windows 업데이트에 포함된 .NET Framework 4.6 및 4.6.1의 서비스 릴리스에서도 대부분의 문제가 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="58a59-111">사용 중인 Windows 버전이 최신 버전인지 확인하거나 .NET Framework 4.6.2로 업그레이드하여 이러한 문제를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="58a59-112">특정 상황에서 최적화가 설정된 릴리스 빌드에서 Unboxing 작업으로 인해 <xref:System.NullReferenceException>이 throw될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="58a59-113">일부 경우에는 큰 메서드 본문의 프로덕션 코드가 실행될 때 <xref:System.StackOverflowException>이 throw될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="58a59-114">특정 상황에서 메서드에 전달된 구조체가 릴리스 빌드에서 값 형식이 아닌 참조 형식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="58a59-115">이 문제의 징후 중 하나는 컬렉션의 개별 항목이 예기치 않은 순서로 표시되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="58a59-116">특정 상황에서 최적화가 사용되도록 설정되어 있을 경우 <xref:System.UInt16> 값을 높은 비트의 집합과 비교하면 결과가 잘못됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="58a59-117">배열 값을 초기화할 때와 같은 특정 상황에서 <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 명령에 따라 메모리가 초기화되면 잘못된 값이 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="58a59-118">이로 인해 처리되지 않은 예외 또는 잘못된 출력이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="58a59-119">드물게 특정한 상황에서 컴파일러 최적화가 사용되도록 설정되면 조건부 비트 테스트가 잘못된 <xref:System.Boolean> 값을 반환하거나 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="58a59-120">특정 상황에서 `try` 블록을 시작하기 전에 `if` 문을 사용해서 조건을 테스트한 후에 `try` 블록을 종료하고 `catch` 또는 `finally` 블록에서 동일한 조건을 평가하면 새로운 64비트 JIT 컴파일러는 코드를 최적화할 때 `catch` 또는 `finally` 블록에서 `if` 조건을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="58a59-121">결과적으로 `catch` 또는 `finally` 블록에서 `if` 문 내의 코드가 무조건적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>

## <a name="mitigation-of-known-issues"></a><span data-ttu-id="58a59-122">알려진 문제 완화</span><span class="sxs-lookup"><span data-stu-id="58a59-122">Mitigation of known issues</span></span>  

 <span data-ttu-id="58a59-123">위에 나열된 문제가 발생하는 경우 다음 중 하나를 수행하여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="58a59-124">.NET Framework 4.6.2로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="58a59-125">.NET Framework 4.6.2에 포함된 새로운 64비트 컴파일러는 이러한 각각의 알려진 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="58a59-126">Windows 업데이트를 실행하여 사용 중인 Windows 버전을 최신 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="58a59-127">.NET Framework 4.6 및 4.6.1에 대한 서비스 업데이트는 unboxing 작업의 <xref:System.NullReferenceException>을 제외하고 이러한 각 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="58a59-128">이전 64비트 JIT 컴파일러를 사용하여 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="58a59-129">방법에 대한 자세한 내용은 [기타 문제 완화](#Other) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58a59-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>

## <a name="mitigation-of-other-issues"></a><span data-ttu-id="58a59-130">기타 문제 완화</span><span class="sxs-lookup"><span data-stu-id="58a59-130">Mitigation of other issues</span></span>  

 <span data-ttu-id="58a59-131">이전 64비트 JIT 컴파일러 및 새로운 64비트 JIT 컴파일러를 사용하여 컴파일한 코드 또는 둘 다 새로운 64비트 JIT 컴파일러를 사용하여 컴파일한 앱의 디버그 버전 및 릴리스 버전 간 동작에서 다른 차이가 발생하는 경우 다음을 수행하여 이전 64비트 JIT 컴파일러로 앱을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="58a59-132">애플리케이션별로 [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) 요소를 애플리케이션의 구성 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="58a59-133">다음은 새로운 64비트 JIT 컴파일러를 사용하는 컴파일을 사용하지 않도록 설정하고, 대신 레거시 64비트 JIT 컴파일러를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="58a59-134">사용자별로 레지스트리의 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 키에 `useLegacyJit`라는 `REG_DWORD` 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="58a59-135">값이 1이면 레거시 64비트 JIT 컴파일러가 사용되도록 설정되고 값이 0이면 새로운 64비트 JIT 컴파일러가 사용되도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="58a59-136">컴퓨터별로 레지스트리의 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 키에 `useLegacyJit`라는 `REG_DWORD` 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="58a59-137">값이 1이면 레거시 64비트 JIT 컴파일러가 사용되도록 설정되고 값이 0이면 새로운 64비트 JIT 컴파일러가 사용되도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="58a59-138">[Microsoft Connect](https://connect.microsoft.com/VisualStudio)에 버그를 보고하여 문제를 알릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a59-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a59-139">참조</span><span class="sxs-lookup"><span data-stu-id="58a59-139">See also</span></span>

- [<span data-ttu-id="58a59-140">애플리케이션 호환성</span><span class="sxs-lookup"><span data-stu-id="58a59-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="58a59-141">\<useLegacyJit> 요소</span><span class="sxs-lookup"><span data-stu-id="58a59-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
