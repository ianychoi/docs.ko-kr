---
title: 컬렉션에서 Culture를 구분하지 않는 문자열 작업 수행
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: f0d932dcbb07253e3ea52238a81b416af148cf98
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829780"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="d05b0-102">컬렉션에서 Culture를 구분하지 않는 문자열 작업 수행</span><span class="sxs-lookup"><span data-stu-id="d05b0-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="d05b0-103"><xref:System.Collections> 네임스페이스에는 기본적으로 문화권 구분 동작을 제공하는 클래스 및 멤버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="d05b0-104"><xref:System.Collections.CaseInsensitiveComparer> 및 <xref:System.Collections.CaseInsensitiveHashCodeProvider> 클래스의 매개 변수 없는 생성자는 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 속성을 사용하여 새 인스턴스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d05b0-105"><xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> 메서드의 모든 오버로드는 기본적으로 `Thread.CurrentCulture` 속성을 사용하여 <xref:System.Collections.Hashtable> 클래스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="d05b0-106"><xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> 메서드의 오버로드는 기본적으로 `Thread.CurrentCulture`를 사용하여 문화권 구분 정렬을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="d05b0-107">문자열이 키로 사용될 경우 <xref:System.Collections.SortedList>의 정렬 및 조회는 `Thread.CurrentCulture`의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="d05b0-108">`Collections` 네임스페이스의 이러한 클래스 및 메서드에서 문화권을 구분하는 결과를 얻으려면 이 섹션에 제공된 사용 권장 사항을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="d05b0-109">비교 메서드에 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>를 전달하면 문화권을 구분하지 않는 비교가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="d05b0-110">그러나 파일 경로, 레지스트리 키 및 환경 변수 등과 같은 비언어적 비교는 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="d05b0-111">비교 결과에 따라 보안 결정을 지원하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="d05b0-112">비언어적 비교 또는 결과 기반 보안 의사 결정에 대한 지원의 경우는 애플리케이션이 <xref:System.StringComparison> 값을 수락하는 비교 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="d05b0-113">그런 다음, 애플리케이션이 <xref:System.StringComparison>을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="d05b0-114">CaseInsensitiveComparer 및 CaseInsensitiveHashCodeProvider 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="d05b0-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="d05b0-115">`CaseInsensitiveHashCodeProvider` 및 `CaseInsensitiveComparer`에 대한 매개 변수 없는 생성자는 `Thread.CurrentCulture`를 사용하여 클래스의 새 인스턴스를 초기화함으로써 문화권 구분 동작을 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="d05b0-116">다음 코드 예제에서는 `CaseInsensitiveHashCodeProvider` 및 `CaseInsensitiveComparer`에 대해 매개 변수 없는 생성자를 사용하므로 문화권을 구분하는 `Hashtable`에 대한 생성자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="d05b0-117">`CaseInsensitiveComparer` 및 `CaseInsensitiveHashCodeProvider` 클래스를 사용하여 문화권을 구분하지 않는 `Hashtable`을 만들려는 경우 `culture` 매개 변수를 수락하는 생성자를 사용하여 이러한 클래스의 새 인스턴스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="d05b0-118">`culture` 매개 변수의 경우 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d05b0-119">다음 코드 예제에서는 문화권을 구분하지 않는 `Hashtable`에 대한 생성자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="d05b0-120">CollectionsUtil.CreateCaseInsensitiveHashtable 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="d05b0-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="d05b0-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` 메서드는 문자열의 대/소문자를 무시하는 `Hashtable` 클래스의 새 인스턴스를 만드는 데 유용한 바로 가기입니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="d05b0-122">그러나 `CollectionsUtil.CreateCaseInsensitiveHashTable` 메서드의 모든 오버로드는 `Thread.CurrentCulture` 속성을 사용하기 때문에 문화권을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d05b0-123">이 메서드를 사용하여 문화권을 구분하지 않는 `Hashtable`을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="d05b0-124">문화권을 구분하지 않는 `Hashtable`을 만들려면 `culture` 매개 변수를 수락하는 `Hashtable` 생성자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="d05b0-125">`culture` 매개 변수의 경우 `CultureInfo.InvariantCulture`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d05b0-126">다음 코드 예제에서는 문화권을 구분하지 않는 `Hashtable`에 대한 생성자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="d05b0-127">SortedList 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="d05b0-127">Using the SortedList Class</span></span>

<span data-ttu-id="d05b0-128">`SortedList`는 키를 기준으로 정렬되고 키와 인덱스로 액세스할 수 있는 키/값 쌍의 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="d05b0-129">문자열이 키인 경우에 `SortedList`를 사용하면 정렬 및 조회가 `Thread.CurrentCulture` 속성의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d05b0-130">`SortedList`에서 문화권을 구분하지 않는 동작을 가져오려면 `comparer` 매개 변수를 수락하는 생성자 중 하나를 사용하여 `SortedList`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="d05b0-131">`comparer` 매개 변수는 키를 비교할 때 사용할 <xref:System.Collections.IComparer> 구현을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="d05b0-132">매개 변수의 경우 `CultureInfo.InvariantCulture`를 사용하는 사용자 지정 비교자 클래스를 지정하여 키를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="d05b0-133">다음 예제에서는 `SortedList` 생성자에 대한 `comparer` 매개 변수로 지정할 수 있는 사용자 지정 문화권 비구분 비교자 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="d05b0-134">일반적으로 사용자 지정 고정 비교자를 지정하지 않고 문자열에 대해 `SortedList`를 사용하는 경우 목록이 채워진 후에 수행한 `Thread.CurrentCulture` 변경 내용 때문에 목록이 무효화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="d05b0-135">ArrayList.Sort 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="d05b0-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="d05b0-136">`ArrayList.Sort` 메서드의 오버로드는 기본적으로 `Thread.CurrentCulture` 속성을 사용하여 문화권 구분 정렬을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d05b0-137">다른 정렬 순서로 인해 문화권마다 결과가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="d05b0-138">문화권 구분 동작을 제거하려면 `IComparer` 구현을 수락하는 이 메서드의 오버로드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="d05b0-139">`comparer` 매개 변수의 경우 `CultureInfo.InvariantCulture`를 사용하는 사용자 지정 고정 비교자 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d05b0-140">사용자 지정 고정 비교자 클래스의 예는 [SortedList 클래스 사용](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d05b0-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="d05b0-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d05b0-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="d05b0-142">Culture의 영향을 받지 않는 문자열 작업 수행</span><span class="sxs-lookup"><span data-stu-id="d05b0-142">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
