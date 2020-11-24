---
title: Sorted 컬렉션 형식
ms.date: 04/30/2020
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: 62e0ffde31d91ea2b0bbe3b5c37cddb87349b5a3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823825"
---
# <a name="sorted-collection-types"></a><span data-ttu-id="fe3dd-102">Sorted 컬렉션 형식</span><span class="sxs-lookup"><span data-stu-id="fe3dd-102">Sorted Collection Types</span></span>

<span data-ttu-id="fe3dd-103"><xref:System.Collections.SortedList?displayProperty=nameWithType> 클래스, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> 제네릭 클래스 및 <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> 제네릭 클래스는 <xref:System.Collections.Hashtable> 클래스 및 <xref:System.Collections.Generic.Dictionary%602> 제네릭 클래스와 유사합니다. 해당 항목은 여기서 <xref:System.Collections.IDictionary> 인터페이스를 구현하지만 키를 기준으로 한 정렬 순서로 해당 요소를 유지 관리하고 O(1) 삽입 및 해시 테이블의 검색 특성을 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-103">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="fe3dd-104">세 가지 클래스에는 공통적으로 다음과 같은 몇 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-104">The three classes have several features in common:</span></span>

- <span data-ttu-id="fe3dd-105">세 가지 클래스는 모두 <xref:System.Collections.IDictionary?displayProperty=nameWithType> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="fe3dd-106">두 개의 제네릭 인터페이스는 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> 제네릭 클래스도 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>

- <span data-ttu-id="fe3dd-107">각 요소는 열거형에 사용할 키/값 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-107">Each element is a key/value pair for enumeration purposes.</span></span>

   > [!NOTE]
   > <span data-ttu-id="fe3dd-108">제네릭 클래스가 아닌 <xref:System.Collections.SortedList> 클래스는 열거될 때 <xref:System.Collections.DictionaryEntry> 개체를 반환하지만 두 개의 제네릭 형식은 <xref:System.Collections.Generic.KeyValuePair%602> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>

- <span data-ttu-id="fe3dd-109">요소는 <xref:System.Collections.IComparer?displayProperty=nameWithType> 구현(제네릭 클래스가 아닌 <xref:System.Collections.SortedList>의 경우) 또는 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 구현(두 개의 제네릭 클래스의 경우)에 따라 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>

- <span data-ttu-id="fe3dd-110">각 클래스는 키만 포함하거나 값만 포함하는 컬렉션을 반환하는 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>

<span data-ttu-id="fe3dd-111">다음 표에서는 두 개의 정렬된 목록 클래스 및 <xref:System.Collections.Generic.SortedDictionary%602> 클래스 간의 차이점을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>

| <span data-ttu-id="fe3dd-112"><xref:System.Collections.SortedList> 제네릭이 아닌 클래스 및 <xref:System.Collections.Generic.SortedList%602> 제네릭 클래스</span><span class="sxs-lookup"><span data-stu-id="fe3dd-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span> | <span data-ttu-id="fe3dd-113"><xref:System.Collections.Generic.SortedDictionary%602> 제네릭 클래스</span><span class="sxs-lookup"><span data-stu-id="fe3dd-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span> |
|--|--|
| <span data-ttu-id="fe3dd-114">키와 값을 반환하는 속성은 인덱스되어 인덱싱된 효율적인 검색을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span> | <span data-ttu-id="fe3dd-115">인덱스된 검색이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-115">No indexed retrieval.</span></span> |
| <span data-ttu-id="fe3dd-116">검색은 O(로그 `n`)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-116">Retrieval is O(log `n`).</span></span> | <span data-ttu-id="fe3dd-117">검색은 O(로그 `n`)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-117">Retrieval is O(log `n`).</span></span> |
| <span data-ttu-id="fe3dd-118">삽입 및 제거는 일반적으로 O(`n`)이지만 정렬 순서로 나열된 데이터의 경우 삽입은 O(로그 `n`)이므로 각 요소가 목록 끝에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="fe3dd-119">(여기서는 크기 조정이 필요하지 않다고 가정합니다.)</span><span class="sxs-lookup"><span data-stu-id="fe3dd-119">(This assumes that a resize is not required.)</span></span> | <span data-ttu-id="fe3dd-120">삽입과 제거는 O(로그 `n`)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-120">Insertion and removal are O(log `n`).</span></span> |
| <span data-ttu-id="fe3dd-121"><xref:System.Collections.Generic.SortedDictionary%602>보다 적은 메모리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span> | <span data-ttu-id="fe3dd-122"><xref:System.Collections.SortedList> 제네릭이 아닌 클래스와 <xref:System.Collections.Generic.SortedList%602> 제네릭 클래스보다 더 많은 메모리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span> |

<span data-ttu-id="fe3dd-123">여러 스레드에서 동시에 액세스할 수 있어야 하는 정렬된 목록 또는 사전의 경우 정렬 논리를 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>에서 파생된 클래스에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span> <span data-ttu-id="fe3dd-124">불변성을 고려할 때 다음에 해당하는 변경할 수 없는 형식은 <xref:System.Collections.Immutable.ImmutableSortedSet%601> 및 <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>와 유사한 정렬 의미 체계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-124">When considering immutability, the following corresponding immutable types follow similar sorting semantics: <xref:System.Collections.Immutable.ImmutableSortedSet%601> and <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>.</span></span>

> [!NOTE]
> <span data-ttu-id="fe3dd-125">고유한 키를 포함하는 값(예: 직원 ID 번호를 포함하는 직원 레코드)의 경우 <xref:System.Collections.ObjectModel.KeyedCollection%602> 제네릭 클래스에서 파생하여 목록의 일부 특성 및 사전의 일부 특성을 가진 키가 지정된 컬렉션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-125">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>

<span data-ttu-id="fe3dd-126">.NET Framework 4부터 <xref:System.Collections.Generic.SortedSet%601> 클래스는 삽입, 삭제, 검색 후에 정렬된 순서에 따라 데이터를 유지 관리하는 자체 균형 조정 트리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-126">Starting with .NET Framework 4, the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="fe3dd-127">이 클래스와 <xref:System.Collections.Generic.HashSet%601> 클래스는 <xref:System.Collections.Generic.ISet%601> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3dd-127">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe3dd-128">참조</span><span class="sxs-lookup"><span data-stu-id="fe3dd-128">See also</span></span>

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [<span data-ttu-id="fe3dd-129">일반적으로 사용되는 컬렉션 형식</span><span class="sxs-lookup"><span data-stu-id="fe3dd-129">Commonly Used Collection Types</span></span>](commonly-used-collection-types.md)
