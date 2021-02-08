---
description: '자세한 정보: 메모리 및 범위 관련 형식'
title: 메모리 및 범위
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c151632db0fdfff388f1aba95fd9b0edc940ae0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731697"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="59c44-103">메모리 및 범위 관련 형식</span><span class="sxs-lookup"><span data-stu-id="59c44-103">Memory- and span-related types</span></span>

<span data-ttu-id="59c44-104">.NET Core 2.1부터 .NET에는 임의 메모리의 인접한 강력한 형식의 영역을 나타내는 여러 개의 상호 연결된 형식이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-104">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="59c44-105">여기에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-105">These include:</span></span>

- <span data-ttu-id="59c44-106"><xref:System.Span%601?displayProperty=nameWithType> - 메모리의 인접한 영역에 액세스하는 데 사용되는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-106"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="59c44-107"><xref:System.Span%601> 인스턴스는 `T` 형식 배열, <xref:System.String>, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)로 할당된 버퍼 또는 관리되지 않는 메모리에 대한 포인터를 통해 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-107">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="59c44-108">스택에 할당되어야 하므로 여러 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-108">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="59c44-109">예를 들어 클래스의 필드는 <xref:System.Span%601> 형식일 수 없으며, 비동기 작업에 범위를 사용할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-109">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="59c44-110"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType> - 변경할 수 없는 <xref:System.Span%601> 구조체 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-110"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="59c44-111"><xref:System.Memory%601?displayProperty=nameWithType> - 메모리의 연속 영역에 관한 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-111"><xref:System.Memory%601?displayProperty=nameWithType>, a wrapper over a contiguous region of memory.</span></span> <span data-ttu-id="59c44-112"><xref:System.Memory%601> 인스턴스는 `T` 또는 <xref:System.String> 형식의 배열이나 메모리 관리자로 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-112">A <xref:System.Memory%601> instance can be backed by an array of type `T`, or a <xref:System.String>, or a memory manager.</span></span> <span data-ttu-id="59c44-113">관리되는 힙에 저장할 수 있어 <xref:System.Memory%601>에는 <xref:System.Span%601>의 제한 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-113">As it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="59c44-114"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType> - 변경할 수 없는 <xref:System.Memory%601> 구조체 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-114"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="59c44-115"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType> - 메모리 풀에서 강력한 형식의 메모리 블록을 소유자에게 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-115"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="59c44-116"><xref:System.Buffers.IMemoryOwner%601> 인스턴스는 <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>을 호출하여 풀에서 대여하고, <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>을 호출하여 다시 풀로 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-116"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="59c44-117"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> - 메모리 블록의 소유자를 나타내고 해당 수명 관리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-117"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="59c44-118"><xref:System.Buffers.MemoryManager%601> - SafeHandle 등의 추가 형식을 통해 <xref:System.Memory%601>를 지원할 수 있도록 <xref:System.Memory%601>의 구현을 바꾸는 데 사용할 수 있는 추상 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-118"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="59c44-119"><xref:System.Buffers.MemoryManager%601>는 고급 시나리오를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-119"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="59c44-120"><xref:System.ArraySegment%601> - 특정 인덱스에서 시작하는 특정 개수의 배열 요소에 대한 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-120"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="59c44-121"><xref:System.MemoryExtensions?displayProperty=nameWithType> - 문자열, 배열 및 배열 세그먼트를 <xref:System.Memory%601> 블록으로 변환하기 위한 확장 메서드 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-121"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

<span data-ttu-id="59c44-122"><xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Memory%601?displayProperty=nameWithType> 및 그 읽기 전용 상대는 메모리를 복사하거나 관리되는 힙에 필요 이상으로 할당되는 것을 방지하는 알고리즘을 생성할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-122"><xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Memory%601?displayProperty=nameWithType>, and their readonly counterparts are designed to allow the creation of algorithms that avoid copying memory or allocating on the managed heap more than necessary.</span></span> <span data-ttu-id="59c44-123">이러한 항목을 만들 때(`Slice` 또는 해당 생성자를 통해) 기본 버퍼를 복제하는 작업과 관련되지 않아 래핑된 메모리의 "뷰"를 나타내는 관련 참조 및 오프셋만 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-123">Creating them (either via `Slice` or their constructors) does not involve duplicating the underlying buffers: only the relevant references and offsets, which represent the "view" of the wrapped memory, are updated.</span></span>

> [!NOTE]
> <span data-ttu-id="59c44-124">이전 프레임워크의 경우 [System.Memory NuGet 패키지](https://www.nuget.org/packages/System.Memory/)에서 <xref:System.Span%601> 및 <xref:System.Memory%601>를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-124">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="59c44-125">자세한 내용은 <xref:System.Buffers?displayProperty=nameWithType> 네임스페이스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59c44-125">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="59c44-126">메모리 및 범위 작업</span><span class="sxs-lookup"><span data-stu-id="59c44-126">Working with memory and span</span></span>

<span data-ttu-id="59c44-127">메모리 및 범위 관련 형식은 일반적으로 데이터를 처리 파이프라인에 저장하는 데 사용되므로 개발자가 <xref:System.Span%601>, <xref:System.Memory%601> 및 관련 형식을 사용할 때 모범 사례 세트를 따르는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-127">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="59c44-128">이러한 모범 사례는 [메모리\<T> 및 범위\<T> 사용 지침](memory-t-usage-guidelines.md)에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59c44-128">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59c44-129">참조</span><span class="sxs-lookup"><span data-stu-id="59c44-129">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
