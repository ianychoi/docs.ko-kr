---
title: 컬렉션 작업 - C# 소개 자습서
description: 이 자습서에서는 목록 컬렉션을 살펴보면서 C#에 대해 학습합니다.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 4ecd2cfebddf460d3766d708d2f6740bd1c6e29a
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585665"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="6d538-103">일반 목록 형식을 사용하여 데이터 컬렉션을 관리하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="6d538-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="6d538-104">이 소개 자습서에서는 C# 언어 및 <xref:System.Collections.Generic.List%601> 클래스의 기본 사항을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d538-105">사전 준비 사항</span><span class="sxs-lookup"><span data-stu-id="6d538-105">Prerequisites</span></span>

<span data-ttu-id="6d538-106">이 자습서에서는 컴퓨터가 로컬 개발용으로 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="6d538-107">Windows, Linux 또는 macOS에서 .NET CLI를 사용하여 애플리케이션을 만들고, 빌드하고, 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="6d538-108">Windows에서 Visual Studio 2019를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="6d538-109">설정 지침은 [로컬 환경 설정](local-environment.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d538-109">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="6d538-110">기본 목록 예제</span><span class="sxs-lookup"><span data-stu-id="6d538-110">A basic list example</span></span>

<span data-ttu-id="6d538-111">*list-tutorial* 이라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-111">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="6d538-112">현재 디렉터리로 지정하고 `dotnet new console`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-112">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="6d538-113">편집기에서 *Program.cs* 를 열고 기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-113">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="6d538-114">`<name>`을 사용자의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="6d538-115">*Program.cs* 를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-115">Save *Program.cs*.</span></span> <span data-ttu-id="6d538-116">콘솔 창에 `dotnet run`을 입력하여 시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6d538-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="6d538-117">문자열 목록을 만들고, 해당 목록에 세 개의 이름을 추가하고, 모든 CAPS에 이름을 인쇄했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-117">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="6d538-118">이전 자습서에서 학습한 개념을 사용하여 목록을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-118">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="6d538-119">이름을 표시하는 코드는 [문자열 보간](../../language-reference/tokens/interpolated.md) 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-119">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="6d538-120">`string` 앞에 `$` 문자를 넣으면 문자열 선언에 C# 코드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="6d538-121">실제 문자열은 C# 코드를 생성하는 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="6d538-122">이 예제에서는 <xref:System.String.ToUpper%2A> 메서드를 호출했기 때문에 `{name.ToUpper()}`를 대문자로 변환된 각 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="6d538-123">계속해서 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-123">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="6d538-124">목록 콘텐츠 수정</span><span class="sxs-lookup"><span data-stu-id="6d538-124">Modify list contents</span></span>

<span data-ttu-id="6d538-125">생성한 컬렉션은 <xref:System.Collections.Generic.List%601> 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="6d538-126">이 형식은 요소의 시퀀스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-126">This type stores sequences of elements.</span></span> <span data-ttu-id="6d538-127">꺾쇠 괄호 사이의 요소 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-127">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="6d538-128">이 <xref:System.Collections.Generic.List%601> 형식은 늘리거나 줄일 수 있어 요소를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="6d538-129">`Main` 메서드에서 `}`를 닫기 전에 이 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-129">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="6d538-130">목록 끝에 이름을 두 개 더 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="6d538-131">또한 이름을 하나 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-131">You've also removed one as well.</span></span> <span data-ttu-id="6d538-132">파일을 저장하고 `dotnet run`을 입력하여 시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6d538-132">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="6d538-133"><xref:System.Collections.Generic.List%601>를 사용하면 **인덱스** 별로 각 항목을 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="6d538-134">목록 이름 뒤 `[`와 `]` 토큰 사이에 인덱스를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="6d538-135">C#은 첫 번째 인덱스에 0을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="6d538-136">방금 추가한 코드 바로 아래에 이 코드를 추가하여 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="6d538-137">목록의 끝을 벗어나는 인덱스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-137">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="6d538-138">인덱스는 0부터 시작하므로, 가장 큰 유효 인덱스는 목록의 항목 수보다 하나 작습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="6d538-139"><xref:System.Collections.Generic.List%601.Count%2A> 속성을 사용하여 목록의 길이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="6d538-140">Main 메서드의 끝에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="6d538-141">파일을 저장하고 `dotnet run`을 다시 입력하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-141">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="6d538-142">목록 검색 및 정렬</span><span class="sxs-lookup"><span data-stu-id="6d538-142">Search and sort lists</span></span>

<span data-ttu-id="6d538-143">샘플에서는 상대적으로 작은 목록을 사용하지만 애플리케이션에서는 수천에 달하는 많은 요소가 포함된 목록을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="6d538-144">이러한 큰 컬렉션에서 요소를 찾으려면 여러 항목의 목록을 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="6d538-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> 메서드는 항목을 검색하고 항목의 인덱스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="6d538-146">목록에 항목이 없으면 `IndexOf`가 `-1`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-146">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="6d538-147">`Main` 메서드의 맨 아래에 이 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-147">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="6d538-148">목록의 항목도 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-148">The items in your list can be sorted as well.</span></span> <span data-ttu-id="6d538-149"><xref:System.Collections.Generic.List%601.Sort%2A> 메서드는 일반적인 순서(문자열의 경우 사전순)로 목록의 모든 항목을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-149">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="6d538-150">`Main` 메서드의 맨 아래에 이 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-150">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="6d538-151">파일을 저장하고 `dotnet run`을 입력하여 이 최신 버전을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6d538-151">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="6d538-152">다음 섹션을 시작하기 전에 현재 코드를 별도의 메서드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-152">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="6d538-153">이렇게 하면 새 예제 작업을 쉽게 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-153">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="6d538-154">`Main` 메서드의 이름을 `WorkingWithStrings`로 바꾸고 `WorkingWithStrings`를 호출하는 새 `Main` 메서드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-154">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="6d538-155">작업을 마치면 코드가 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-155">When you've finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="6d538-156">다른 형식 목록</span><span class="sxs-lookup"><span data-stu-id="6d538-156">Lists of other types</span></span>

<span data-ttu-id="6d538-157">지금까지 목록에 `string` 형식을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-157">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="6d538-158">다른 형식을 사용하여 <xref:System.Collections.Generic.List%601>를 만들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-158">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="6d538-159">숫자 집합을 빌드하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-159">Let's build a set of numbers.</span></span>

<span data-ttu-id="6d538-160">새 `Main` 메서드의 맨 아래에 다음을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-160">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="6d538-161">정수 목록을 만들고 처음 두 정수를 값 1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-161">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="6d538-162">숫자 시퀀스인 *피보나치 시퀀스* 의 첫 번째 두 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-162">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="6d538-163">다음 각 피보나치 수는 이전의 두 수의 합계를 사용하여 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-163">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="6d538-164">이 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-164">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="6d538-165">파일을 저장하고 `dotnet run`을 입력하여 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-165">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="6d538-166">이 섹션에만 집중하려면 `WorkingWithStrings();`를 호출하는 코드를 주석으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-166">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="6d538-167">`// WorkingWithStrings();`처럼 호출 앞에 `/` 문자를 두 개 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-167">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="6d538-168">과제</span><span class="sxs-lookup"><span data-stu-id="6d538-168">Challenge</span></span>

<span data-ttu-id="6d538-169">이 단원과 이전 단원에서 학습한 개념을 함께 적용할 수 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6d538-169">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="6d538-170">피보나치 수를 사용하여 지금까지 빌드한 내용을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-170">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="6d538-171">코드를 작성하여 시퀀스에서 처음 20개 수를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-171">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="6d538-172">(힌트: 20번째 피보나치 수는 6765입니다.)</span><span class="sxs-lookup"><span data-stu-id="6d538-172">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="6d538-173">과제 완료</span><span class="sxs-lookup"><span data-stu-id="6d538-173">Complete challenge</span></span>

<span data-ttu-id="6d538-174">[GitHub에서 완료된 샘플 코드를 보고](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23) 예제 솔루션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-174">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="6d538-175">루프의 각 반복을 통해 목록의 마지막 두 정수를 사용하고, 더하고, 해당 값을 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-175">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="6d538-176">목록에 20개의 항목이 추가될 때까지 루프가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-176">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="6d538-177">축하합니다. 목록 자습서를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-177">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="6d538-178">자체 개발 환경에서 [클래스 소개](introduction-to-classes.md) 자습서를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-178">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="6d538-179">.NET 기본 사항 문서의 [컬렉션](../../../standard/collections/index.md)에서 `List` 형식 작업에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-179">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="6d538-180">다른 많은 컬렉션 형식에 대해서도 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="6d538-180">You'll also learn about many other collection types.</span></span>
