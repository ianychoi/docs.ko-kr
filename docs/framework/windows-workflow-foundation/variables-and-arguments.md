---
title: 변수 및 인수
description: 이 문서에서는 데이터 저장소를 나타내는 변수와 Workflow Foundation의 작업 간 데이터 흐름을 나타내는 인수를 설명 합니다.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 9d593fa5a974524cf976361de9871d3877e58c2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293886"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="ce2ff-103">변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="ce2ff-103">Variables and Arguments</span></span>

<span data-ttu-id="ce2ff-104">WF (Windows Workflow Foundation)에서 변수는 데이터의 저장소를 나타내고 인수는 활동에 대 한 데이터의 흐름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="ce2ff-105">활동에는 인수 집합이 있으며 인수는 활동의 시그니처를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="ce2ff-106">또한 활동은 개발자가 워크플로 디자인 중에 변수를 추가하거나 제거할 수 있는 변수 목록을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="ce2ff-107">인수는 값을 반환하는 식을 사용하여 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="ce2ff-108">변수</span><span class="sxs-lookup"><span data-stu-id="ce2ff-108">Variables</span></span>  

 <span data-ttu-id="ce2ff-109">변수는 데이터의 스토리지 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-109">Variables are storage locations for data.</span></span> <span data-ttu-id="ce2ff-110">변수는 워크플로 정의의 일부로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="ce2ff-111">변수는 런타임에 값을 가져오고 이 값은 워크플로 인스턴스 상태의 일부로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="ce2ff-112">변수 정의는 변수의 형식과 선택적으로 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="ce2ff-113">다음 코드에서는 변수를 선언하고 <xref:System.Activities.Statements.Assign%601> 활동을 사용하여 변수에 값을 할당한 다음 <xref:System.Activities.Statements.WriteLine> 활동을 사용하여 콘솔에 값을 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="ce2ff-114">변수 선언의 일부로 기본값 식을 선택적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="ce2ff-115">변수도 한정자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-115">Variables also can have modifiers.</span></span> <span data-ttu-id="ce2ff-116">예를 들어 변수가 읽기 전용이면 읽기 전용 <xref:System.Activities.VariableModifiers> 한정자를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="ce2ff-117">다음 예제에서는 기본값이 할당되는 읽기 전용 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="ce2ff-118">변수 범위 지정</span><span class="sxs-lookup"><span data-stu-id="ce2ff-118">Variable Scoping</span></span>  

 <span data-ttu-id="ce2ff-119">런타임에 변수의 수명은 변수를 선언하는 활동의 수명과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="ce2ff-120">활동이 완료되면 변수가 정리되고 변수를 더 이상 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="ce2ff-121">인수</span><span class="sxs-lookup"><span data-stu-id="ce2ff-121">Arguments</span></span>  

 <span data-ttu-id="ce2ff-122">활동 작성자는 인수를 사용하여 데이터가 활동 내부 및 외부로 흐르는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="ce2ff-123">각 인수에는 <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out> 또는 <xref:System.Activities.ArgumentDirection.InOut>과 같은 지정된 방향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="ce2ff-124">워크플로 런타임은 활동 내부 및 외부로 데이터가 이동하는 타이밍에 대해 다음을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="ce2ff-125">활동이 실행되기 시작하면 모든 입력 및 입/출력 인수의 값이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="ce2ff-126">예를 들어 <xref:System.Activities.Argument.Get%2A>이 호출되는 시간과 상관없이, 반환되는 값은 `Execute` 호출 전에 런타임에서 계산된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="ce2ff-127"><xref:System.Activities.InOutArgument%601.Set%2A>이 호출되면 런타임은 값을 즉시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="ce2ff-128">인수는 선택적으로 <xref:System.Activities.Argument.EvaluationOrder%2A>를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="ce2ff-129"><xref:System.Activities.Argument.EvaluationOrder%2A>는 인수를 평가하는 순서를 지정하는 0부터 시작하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="ce2ff-130">기본적으로 인수의 평가 순서는 지정되지 않으며 <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> 값과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="ce2ff-131"><xref:System.Activities.Argument.EvaluationOrder%2A>를 0보다 크거나 같은 값으로 설정하여 이 인수의 평가 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="ce2ff-132">Windows Workflow Foundation에는 오름차순에서 지정한 평가 순서의 인수를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="ce2ff-133">평가 순서가 지정되지 않은 인수는 평가 순서가 지정된 인수 이전에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="ce2ff-134">활동 작성자는 강력한 형식의 메커니즘을 사용 하 여 해당 인수를 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-134">An activity author can use a strongly typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="ce2ff-135">이 작업은 <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> 및 <xref:System.Activities.InOutArgument%601> 형식의 속성을 선언하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="ce2ff-136">이렇게 하면 활동 작성자가 활동 내부 및 외부로 이동하는 데이터에 대한 특정 계약을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="ce2ff-137">활동에서 인수 정의</span><span class="sxs-lookup"><span data-stu-id="ce2ff-137">Defining the Arguments on an Activity</span></span>  

 <span data-ttu-id="ce2ff-138"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> 및 <xref:System.Activities.InOutArgument%601> 형식의 속성을 지정하여 활동에서 인수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="ce2ff-139">다음 코드에서는 사용자에게 표시할 문자열을 가져와서 사용자 응답을 포함하는 문자열을 반환하는 `Prompt` 활동에 대한 인수를 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="ce2ff-140">단일 값을 반환하는 활동은 <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601> 또는 <xref:System.Activities.CodeActivity%601>에서 파생될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="ce2ff-141">이 활동에는 활동의 반환 값을 포함하는 <xref:System.Activities.OutArgument%601>라는 잘 정의된 <xref:System.Activities.Activity%601.Result%2A>이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="ce2ff-142">워크플로에서 변수 및 인수 사용</span><span class="sxs-lookup"><span data-stu-id="ce2ff-142">Using Variables and Arguments in Workflows</span></span>  

 <span data-ttu-id="ce2ff-143">다음 예제에서는 워크플로에서 변수와 인수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="ce2ff-144">워크플로는 `var1`, `var2` 및 `var3`이라는 세 가지 변수를 선언하는 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="ce2ff-145">워크플로의 첫 번째 활동은 `Assign` 변수에 `var1` 변수의 값을 할당하는 `var2` 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="ce2ff-146">다음은 `WriteLine` 변수의 값을 인쇄하는 `var2` 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="ce2ff-147">그 다음은 `Assign` 변수에 `var2` 변수의 값을 할당하는 다른 `var3` 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="ce2ff-148">마지막으로 `WriteLine` 변수의 값을 인쇄하는 다른 `var3` 활동이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="ce2ff-149">첫 번째 `Assign` 활동은 활동의 인수에 대한 바인딩을 명시적으로 나타내는 `InArgument<string>` 및 `OutArgument<string>` 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="ce2ff-150">`InArgument<string>`에서는 값은 <xref:System.Activities.Statements.Assign.Value%2A> 인수를 통해 <xref:System.Activities.Statements.Assign%601> 활동으로 전달되기 때문에 <xref:System.Activities.Statements.Assign.Value%2A>이 사용되고 `OutArgument<string>`에서는 값이 <xref:System.Activities.Statements.Assign.To%2A> 인수에서 변수로 전달되기 때문에 <xref:System.Activities.Statements.Assign.To%2A>이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="ce2ff-151">두 번째 `Assign` 활동은 암시적 캐스트를 사용하는 더 간단하지만 동일한 구문을 사용하여 같은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="ce2ff-152">`WriteLine` 활동도 간단한 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="ce2ff-153">코드 기반 활동에서 변수 및 인수 사용</span><span class="sxs-lookup"><span data-stu-id="ce2ff-153">Using Variables and Arguments in Code-Based Activities</span></span>  

 <span data-ttu-id="ce2ff-154">이전 예제에서는 워크플로 및 선언적 활동에서 인수와 변수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="ce2ff-155">인수와 변수는 코드 기반 활동에서도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="ce2ff-156">개념상 사용법은 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="ce2ff-157">변수는 활동 내의 데이터 스토리지를 나타내고 인수는 활동 내부 및 외부로 흐르는 데이터 흐름을 나타내며 워크플로 작성자는 데이터가 흐르는 방향을 나타내는 워크플로의 다른 변수나 인수에 이를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="ce2ff-158">활동에서 변수 또는 인수의 값을 가져오거나 설정하려면 활동의 현재 실행 환경을 나타내는 활동 컨텍스트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="ce2ff-159">이 컨텍스트는 워크플로 런타임에서 활동의 <xref:System.Activities.CodeActivity%601.Execute%2A> 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="ce2ff-160">이 예제에서는 `Add` 인수가 두 개 있는 사용자 지정 <xref:System.Activities.ArgumentDirection.In> 활동을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="ce2ff-161">인수의 값에 액세스하려면 <xref:System.Activities.Argument.Get%2A> 메서드를 사용하고 워크플로 런타임에서 전달된 컨텍스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="ce2ff-162">코드에서 인수, 변수 및 식을 사용 하는 방법에 대 한 자세한 내용은 명령적 코드 및 [필수 인수 및 오버 로드 그룹](required-arguments-and-overload-groups.md)을 [사용 하 여 워크플로, 활동 및 식 작성](authoring-workflows-activities-and-expressions-using-imperative-code.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce2ff-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
