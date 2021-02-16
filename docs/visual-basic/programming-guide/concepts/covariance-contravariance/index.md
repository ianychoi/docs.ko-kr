---
description: '자세한 정보: 공 분산 및 반공 분산 (Visual Basic)'
title: 공 분산 및 반공 분산
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 6569b2c6c4790a5fcf53a9991543286ad6c4314c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485252"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="bb762-103">공변성(Covariance) 및 반공변성(Contravariance)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-103">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="bb762-104">Visual Basic에서 공변성(Covariance)과 반공변성(Contravariance)은 배열 형식, 대리자 형식 및 제네릭 형식 인수에 대한 암시적 참조 변환을 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-104">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="bb762-105">공변성(Covariance)은 할당 호환성을 유지하고 반공변성(Contravariance)은 할당 호환성을 유지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-105">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="bb762-106">다음 코드에서는 할당 호환성, 공변성(Covariance) 및 반공변성(Contravariance) 간의 차이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-106">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="bb762-107">배열에 대한 공변성(Covariance)은 더 많이 파생된 형식의 배열을 더 적게 파생된 형식의 배열로 암시적 변환을 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-107">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="bb762-108">하지만 다음 코드 예제와 같이 이 작업은 형식이 안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-108">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="bb762-109">메서드 그룹에 대한 공변성(Covariance) 및 반공변성(Contravariance) 지원으로 대리자 형식과 메서드 시그니처를 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-109">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="bb762-110">일치하는 시그니처가 있는 메서드뿐만이 아니라 더 많이 파생된 형식(공변성(covariance))을 반환하는 메서드 또는 대리자 형식에 지정된 것보다 더 적게 파생된 형식(반공변성(contravariance))을 가지고 있는 매개 변수를 수락하는 메서드도 대리자에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-110">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="bb762-111">자세한 내용은 [대리자의 가변성(Visual Basic)](variance-in-delegates.md) 및 [대리자의 가변성 사용(Visual Basic)](using-variance-in-delegates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb762-111">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md).</span></span>

<span data-ttu-id="bb762-112">다음 코드 예제에서는 메서드 그룹에 대한 공변성(Covariance) 및 반공변성(Contravariance) 지원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-112">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="bb762-113">.NET Framework 4 Visual Basic 이상에서는 제네릭 인터페이스 및 대리자에서 공 분산 및 반공 분산을 지원 하 고 제네릭 형식 매개 변수를 암시적으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-113">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="bb762-114">자세한 내용은 참조 [제네릭 인터페이스의 가변성(Visual Basic)](variance-in-generic-interfaces.md) 및 [대리자의 가변성(Visual Basic)](variance-in-delegates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb762-114">For more information, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

<span data-ttu-id="bb762-115">다음 코드 예제에서는 제네릭 인터페이스에 대한 암시적 참조 변환을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-115">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="bb762-116">제네릭 매개 변수가 선언된 공변(covariant) 또는 반공변(contravariant)인 경우 제네릭 인터페이스 또는 대리자를 *variant* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-116">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="bb762-117">Visual Basic에서는 사용자 고유의 variant 인터페이스 및 대리자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-117">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="bb762-118">자세한 내용은 [Variant 제네릭 인터페이스 만들기(Visual Basic)](creating-variant-generic-interfaces.md) 및 [대리자의 가변성(Visual Basic)](variance-in-delegates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb762-118">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="bb762-119">관련 항목</span><span class="sxs-lookup"><span data-stu-id="bb762-119">Related Topics</span></span>

|<span data-ttu-id="bb762-120">제목</span><span class="sxs-lookup"><span data-stu-id="bb762-120">Title</span></span>|<span data-ttu-id="bb762-121">설명</span><span class="sxs-lookup"><span data-stu-id="bb762-121">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="bb762-122">제네릭 인터페이스의 가변성(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-122">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)|<span data-ttu-id="bb762-123">제네릭 인터페이스의 공분산 및 반공분산에 대해 설명하고 .NET Framework의 Variant 제네릭 인터페이스의 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-123">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="bb762-124">Variant 제네릭 인터페이스 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-124">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)|<span data-ttu-id="bb762-125">사용자 지정 variant 인터페이스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-125">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="bb762-126">제네릭 컬렉션용 인터페이스의 가변성 사용(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-126">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="bb762-127"><xref:System.Collections.Generic.IEnumerable%601> 및 <xref:System.IComparable%601> 인터페이스의 공변성(Covariance) 및 반공변성(Contravariance) 지원을 통해 코드를 다시 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-127">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="bb762-128">대리자의 가변성(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-128">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)|<span data-ttu-id="bb762-129">제네릭 및 제네릭이 아닌 대리자의 공변성(Covariance) 및 반공변성(Contravariance)을 설명하고 .NET Framework의 Variant 제네릭 인터페이스의 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-129">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="bb762-130">대리자의 가변성 사용(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-130">Using Variance in Delegates (Visual Basic)</span></span>](using-variance-in-delegates.md)|<span data-ttu-id="bb762-131">제네릭이 아닌 대리자의 공변성(Covariance) 및 반공변성(Contravariance) 지원을 사용하여 메서드 시그니처를 대리자 형식과 일치시키는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-131">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="bb762-132">Func 및 Action 제네릭 대리자에 가변성 사용(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb762-132">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="bb762-133">`Func` 및 `Action` 대리자의 공변성(Covariance) 및 반공변성(Contravariance) 지원을 통해 코드를 다시 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb762-133">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
