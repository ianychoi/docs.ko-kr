---
title: 전용 생성자 - C# 프로그래밍 가이드
description: 전용 생성자는 개체를 생성할 수 있는 방법을 제한하는 데 사용되는 C#의 특수 인스턴스 생성자입니다. 팩터리 메서드 또는 다른 생성 관용구와 함께 사용할 수 있습니다.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899404"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="7c450-104">전용 생성자(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="7c450-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="7c450-105">전용 생성자는 특수 인스턴스 생성자입니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="7c450-106">일반적으로 정적 멤버만 포함하는 클래스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="7c450-107">클래스에 하나 이상의 private 생성자가 있고 public 생성자가 없는 경우 중첩 클래스를 제외한 다른 클래스는 이 클래스의 인스턴스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="7c450-108">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="7c450-108">For example:</span></span>  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 <span data-ttu-id="7c450-109">빈 생성자를 선언하면 매개 변수 없는 생성자가 자동으로 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="7c450-110">액세스 한정자를 생성자와 함께 사용하지 않는 경우 기본적으로 여전히 private입니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="7c450-111">그러나 일반적으로 [private](../../language-reference/keywords/private.md) 한정자는 명시적으로 사용되어 클래스를 인스턴스화할 수 없음을 명확하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="7c450-112">private 생성자는 <xref:System.Math> 클래스 등의 인스턴스 필드 또는 메서드가 없는 경우 또는 메서드를 호출하여 클래스 인스턴스를 가져오는 경우 클래스 인스턴스를 만들 수 없도록 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="7c450-113">클래스의 모든 메서드가 정적인 경우 전체 클래스를 정적 클래스로 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="7c450-114">자세한 내용은 [정적 클래스 및 정적 클래스 멤버](./static-classes-and-static-class-members.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c450-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c450-115">예제</span><span class="sxs-lookup"><span data-stu-id="7c450-115">Example</span></span>  

 <span data-ttu-id="7c450-116">다음은 private 생성자를 사용하는 클래스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 <span data-ttu-id="7c450-117">예제에서 다음 문의 주석 처리를 제거하는 경우 보호 수준 때문에 생성자에 액세스할 수 없어 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a><span data-ttu-id="7c450-118">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="7c450-118">C# Language Specification</span></span>  

<span data-ttu-id="7c450-119">자세한 내용은 [C# 언어 사양](/dotnet/csharp/language-reference/language-specification/introduction)의 [전용 생성자](~/_csharplang/spec/classes.md#private-constructors)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c450-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="7c450-120">언어 사양은 C# 구문 및 사용법에 대 한 신뢰할 수 있는 소스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c450-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7c450-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c450-121">See also</span></span>

- [<span data-ttu-id="7c450-122">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="7c450-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c450-123">클래스 및 구조체</span><span class="sxs-lookup"><span data-stu-id="7c450-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7c450-124">생성자</span><span class="sxs-lookup"><span data-stu-id="7c450-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="7c450-125">종료자</span><span class="sxs-lookup"><span data-stu-id="7c450-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="7c450-126">private</span><span class="sxs-lookup"><span data-stu-id="7c450-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="7c450-127">public</span><span class="sxs-lookup"><span data-stu-id="7c450-127">public</span></span>](../../language-reference/keywords/public.md)
