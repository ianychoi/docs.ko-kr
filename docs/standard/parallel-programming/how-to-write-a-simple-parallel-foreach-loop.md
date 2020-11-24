---
title: Parallel.ForEach를 사용하여 단순 병렬 프로그램 작성
description: 이 문서에서는 .NET에서 데이터 병렬 처리를 사용하도록 설정하는 방법을 알아봅니다. IEnumerable 또는 IEnumerable<T> 데이터 소스에 대한 Parallel.ForEach 루프를 작성합니다.
ms.date: 02/14/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: e4f67f6fbe5a79e925ecd6aaec3f833704cda38c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825418"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="ca0eb-104">방법: 간단한 Parallel.ForEach 루프 작성</span><span class="sxs-lookup"><span data-stu-id="ca0eb-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="ca0eb-105">이 예제는 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 루프를 사용하여 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 또는 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 데이터 소스에 대해 데이터 병렬 처리를 사용하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="ca0eb-106">이 문서에서는 람다 식을 사용하여 PLINQ에 대리자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="ca0eb-107">C# 또는 Visual Basic의 람다 식을 잘 모르는 경우 [PLINQ 및 TPL의 람다 식](lambda-expressions-in-plinq-and-tpl.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="ca0eb-108">예제</span><span class="sxs-lookup"><span data-stu-id="ca0eb-108">Example</span></span>

<span data-ttu-id="ca0eb-109">이 예제에서는 *C:\Users\Public\Pictures\Sample Pictures* 폴더에 여러 .jpg 파일이 있다고 가정하고 *Modified* 라는 새 하위 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-109">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="ca0eb-110">예제를 실행할 때 *Sample Pictures* 의 각 .jpg 이미지를 회전시키고 *Modified* 에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-110">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="ca0eb-111">필요에 따라 두 경로를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-111">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="ca0eb-112"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 루프는 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 루프처럼 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-112">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="ca0eb-113">해당 루프는 원본 컬렉션을 분할하고 시스템 환경에 따라 여러 스레드에서 작업을 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-113">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="ca0eb-114">시스템에 프로세서가 많을수록 병렬 메서드가 더 빠르게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-114">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="ca0eb-115">일부 원본 컬렉션의 경우 원본의 크기 및 수행되는 루프 작업의 종류에 따라 순차 루프가 더 빠를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-115">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="ca0eb-116">성능에 대한 자세한 내용은 [데이터 및 작업 병렬 처리에서 발생할 수 있는 문제](potential-pitfalls-in-data-and-task-parallelism.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-116">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="ca0eb-117">병렬 루프에 대한 자세한 내용은 [방법: 간단한 Parallel.For 루프 작성](how-to-write-a-simple-parallel-for-loop.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-117">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="ca0eb-118">제네릭이 아닌 컬렉션에 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>를 사용하려면 다음 예제와 같이 <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 확장 메서드를 사용하여 컬렉션을 일반 컬렉션으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-118">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="ca0eb-119">병렬 LINQ(PLINQ)를 사용하여 <xref:System.Collections.Generic.IEnumerable%601> 데이터 소스의 처리를 병렬 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-119">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="ca0eb-120">PLINQ를 통해 선언 쿼리 구문을 사용하여 루프 동작을 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-120">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="ca0eb-121">자세한 내용은 [PLINQ(병렬 LINQ)](introduction-to-plinq.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-121">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="ca0eb-122">코드 컴파일 및 실행</span><span class="sxs-lookup"><span data-stu-id="ca0eb-122">Compile and run the code</span></span>

<span data-ttu-id="ca0eb-123">.NET Framework의 콘솔 애플리케이션 또는 .NET Core의 콘솔 애플리케이션으로 코드를 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-123">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="ca0eb-124">Visual Studio에는 Windows Desktop 및 .NET Core용 Visual Basic 및 C# 콘솔 애플리케이션 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-124">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="ca0eb-125">명령줄에서 .NET Core CLI 명령(예: `dotnet new console` 또는 `dotnet new console -lang vb`)을 사용하거나 .NET Framework 애플리케이션에서 파일을 만들고 명령줄 컴파일러를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-125">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="ca0eb-126">.NET Core 프로젝트에서 **System.Drawing.Common** NuGet 패키지를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-126">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="ca0eb-127">Visual Studio에서 NuGet 패키지 관리자를 사용하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-127">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="ca0eb-128">혹은 \*.csproj 또는 \*.vbproj 파일에서 패키지에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-128">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="ca0eb-129">명령줄의 .NET Core 콘솔 애플리케이션을 실행하려면 애플리케이션이 포함된 폴더에서 `dotnet run`을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-129">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="ca0eb-130">Visual Studio에서 콘솔 애플리케이션을 실행하려면 **F5** 키를 누르세요.</span><span class="sxs-lookup"><span data-stu-id="ca0eb-130">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca0eb-131">참조</span><span class="sxs-lookup"><span data-stu-id="ca0eb-131">See also</span></span>

- [<span data-ttu-id="ca0eb-132">데이터 병렬 처리</span><span class="sxs-lookup"><span data-stu-id="ca0eb-132">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="ca0eb-133">병렬 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="ca0eb-133">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="ca0eb-134">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="ca0eb-134">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
