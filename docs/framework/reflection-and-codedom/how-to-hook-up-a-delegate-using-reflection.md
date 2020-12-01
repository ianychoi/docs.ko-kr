---
title: '방법: 리플렉션을 사용하여 대리자 후크'
description: .NET에서 리플렉션을 사용하여 대리자를 연결하는 방법을 참조하세요. 리플렉션을 통해 필요한 형식을 가져와 기존 메서드를 이벤트에 연결합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: 9a92afd1c2aeadeb0cf7bc1e626b5bd1fb3cecea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263427"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="51c04-104">방법: 리플렉션을 사용하여 대리자 후크</span><span class="sxs-lookup"><span data-stu-id="51c04-104">How to: Hook Up a Delegate Using Reflection</span></span>

<span data-ttu-id="51c04-105">리플렉션을 사용하여 어셈블리를 로드하고 실행하는 경우 C# `+=` 연산자 또는 Visual Basic [AddHandler 문](../../visual-basic/language-reference/statements/addhandler-statement.md)과 같은 언어 기능을 사용하여 이벤트를 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="51c04-106">다음 절차에서는 리플렉션을 통해 필요한 모든 형식을 가져와 기존 메서드를 이벤트에 연결하는 방법 및 리플렉션 내보내기를 사용하여 동적 메서드를 만들고 이벤트에 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51c04-107">이벤트 처리 대리자를 연결하는 다른 방법은 <xref:System.Reflection.EventInfo> 클래스의 <xref:System.Reflection.EventInfo.AddEventHandler%2A> 메서드에 대한 코드 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51c04-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="51c04-108">리플렉션을 사용하여 대리자를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="51c04-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="51c04-109">이벤트를 발생시키는 형식을 포함하는 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="51c04-110">어셈블리는 일반적으로 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 메서드를 사용하여 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="51c04-111">이 예제를 단순하게 유지하기 위해 현재 어셈블리의 파생 양식이 사용되므로 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 메서드가 현재 어셈블리를 로드하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="51c04-112">형식을 나타내는 <xref:System.Type> 개체를 가져오고 형식 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="51c04-113">양식에 매개 변수가 없는 생성자가 있기 때문에 다음 코드에서는 <xref:System.Activator.CreateInstance%28System.Type%29> 메서드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="51c04-114">만들려는 형식에 매개 변수가 없는 생성자가 없는 경우 사용할 수 있는 <xref:System.Activator.CreateInstance%2A> 메서드의 여러 다른 오버로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="51c04-115">새 인스턴스는 어셈블리에 대해 알려진 것이 없다는 가정을 유지하기 위해 <xref:System.Object> 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="51c04-116">이름을 미리 알지 못해도 리플렉션을 통해 어셈블리의 형식을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="51c04-117">이벤트를 나타내는 <xref:System.Reflection.EventInfo> 개체를 가져오고, <xref:System.Reflection.EventInfo.EventHandlerType%2A> 속성을 사용하여 이벤트를 처리하는 데 사용되는 대리자 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="51c04-118">다음 코드에서는 <xref:System.Windows.Forms.Control.Click> 이벤트에 대한 <xref:System.Reflection.EventInfo>를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="51c04-119">이벤트를 처리하는 메서드를 나타내는 <xref:System.Reflection.MethodInfo> 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="51c04-120">이 항목의 뒷부분에 나오는 예제 섹션의 완성된 프로그램 코드에 <xref:System.EventHandler> 이벤트를 처리하는 <xref:System.Windows.Forms.Control.Click> 대리자의 시그니처와 일치하는 메서드가 포함되어 있지만, 런타임에 동적 메서드를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="51c04-121">동적 메서드를 사용하여 런타임에 이벤트 처리기를 생성하는 것에 대한 자세한 내용은 다음에 나오는 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51c04-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="51c04-122"><xref:System.Delegate.CreateDelegate%2A> 메서드를 사용하여 대리자 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="51c04-123">이 메서드는 static(Visual Basic에서는 `Shared`)이므로 대리자 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="51c04-124"><xref:System.Reflection.MethodInfo>를 사용하는 <xref:System.Delegate.CreateDelegate%2A>의 오버로드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="51c04-125">`add` 접근자 메서드를 가져온 다음 호출하여 이벤트를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="51c04-126">모든 이벤트에는 상위 수준 언어 구문에서 숨겨지는 `add` 접근자 및 `remove` 접근자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="51c04-127">예를 들어 C#에서는 `+=` 연산자를 사용하여 이벤트를 연결하고, Visual Basic에서는 [AddHandler 문](../../visual-basic/language-reference/statements/addhandler-statement.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="51c04-128">다음 코드는 <xref:System.Windows.Forms.Control.Click> 이벤트의 `add` 접근자를 가져온 다음 대리자 인스턴스를 전달하여 런타임에 바인딩해서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="51c04-129">인수를 배열로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="51c04-130">이벤트를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-130">Test the event.</span></span> <span data-ttu-id="51c04-131">다음 코드는 코드 예제에서 정의된 양식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="51c04-132">양식을 클릭하면 이벤트 처리기가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>

### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="51c04-133">동적 메서드를 사용하여 런타임에 이벤트 처리기를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="51c04-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="51c04-134">경량 동적 메서드 및 리플렉션 내보내기를 사용하여 런타임에 이벤트 처리기 메서드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="51c04-135">이벤트 처리기를 생성하려면 대리자의 매개 변수 형식과 반환 형식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="51c04-136">대리자의 `Invoke` 메서드를 검사하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="51c04-137">다음 코드는 `GetDelegateReturnType` 및 `GetDelegateParameterTypes` 메서드를 사용하여 이 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="51c04-138">이러한 메서드에 대한 코드는 이 항목의 뒷부분에 나오는 예제 섹션에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="51c04-139"><xref:System.Reflection.Emit.DynamicMethod>에 이름을 지정할 필요는 없으므로 빈 문자열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="51c04-140">다음 코드에서 마지막 인수는 동적 메서드를 현재 형식과 연결하여 대리자가 `Example` 클래스의 모든 public 및 private 멤버에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="51c04-141">메서드 본문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-141">Generate a method body.</span></span> <span data-ttu-id="51c04-142">이 메서드는 문자열을 로드하고, 문자열을 사용하는 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 메서드의 오버로드를 호출한 다음 스택에서 반환 값을 팝하고(처리기에 반환 형식이 없으므로) 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="51c04-143">동적 메서드를 내보내는 방법에 대한 자세한 내용은 [방법: 동적 메서드 정의 및 실행](how-to-define-and-execute-dynamic-methods.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51c04-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="51c04-144">해당 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 메서드를 호출하여 동적 메서드를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="51c04-145">`add` 접근자를 사용하여 이벤트에 대한 호출 목록에 대리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="51c04-146">이벤트를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-146">Test the event.</span></span> <span data-ttu-id="51c04-147">다음 코드는 코드 예제에서 정의된 양식을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="51c04-148">양식을 클릭하면 미리 정의된 이벤트 처리기와 내보낸 이벤트 처리기가 둘 다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="51c04-149">예제</span><span class="sxs-lookup"><span data-stu-id="51c04-149">Example</span></span>  

 <span data-ttu-id="51c04-150">다음 코드 예제에서는 리플렉션을 사용하여 기존 메서드를 이벤트에 연결하는 방법 및 <xref:System.Reflection.Emit.DynamicMethod> 클래스를 사용하여 런타임에 메서드를 내보내고 이벤트에 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51c04-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="51c04-151">참조</span><span class="sxs-lookup"><span data-stu-id="51c04-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="51c04-152">방법: 동적 메서드 정의 및 실행</span><span class="sxs-lookup"><span data-stu-id="51c04-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="51c04-153">리플렉션</span><span class="sxs-lookup"><span data-stu-id="51c04-153">Reflection</span></span>](reflection.md)
