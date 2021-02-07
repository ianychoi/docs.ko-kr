---
description: '자세한 정보: 형식 생성 (Entity SQL)'
title: 형식 생성(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 5963c34ffd8e9273d400cc16ba93f72ded2ede46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724845"
---
# <a name="constructing-types-entity-sql"></a><span data-ttu-id="ab6c9-103">형식 생성(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ab6c9-103">Constructing Types (Entity SQL)</span></span>

<!-- markdownlint-disable DOCSMD001 -->
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ab6c9-104">에서는 행 생성자, 명명 된 형식 생성자 및 컬렉션 생성자 라는 세 가지 종류의 생성자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-104">provides three kinds of constructors: row constructors, named type constructors, and collection constructors.</span></span>

## <a name="row-constructors"></a><span data-ttu-id="ab6c9-105">행 생성자</span><span class="sxs-lookup"><span data-stu-id="ab6c9-105">Row Constructors</span></span>

<span data-ttu-id="ab6c9-106">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 행 생성자를 사용하여 값 하나 이상을 기반으로 구조적으로 형식화된 익명 레코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-106">You use row constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="ab6c9-107">행 생성자의 결과 형식은 필드 형식이 행 생성에 사용된 값의 형식과 동일한 행 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-107">The result type of a row constructor is a row type whose field types correspond to the types of the values used to construct the row.</span></span> <span data-ttu-id="ab6c9-108">예를 들어 다음 식은 `Record(a int, b string, c int)` 형식의 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-108">For example, the following expression constructs a value of type `Record(a int, b string, c int)`:</span></span>

`ROW(1 AS a, "abc" AS b, a + 34 AS c)`

<span data-ttu-id="ab6c9-109">행 생성자에서 식의 별칭을 제공하지 않으면 Entity Framework에서 별칭을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-109">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="ab6c9-110">자세한 내용은 [식별자](identifiers-entity-sql.md)의 "별칭 규칙" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-110">For more information, see the "Aliasing Rules" section in [Identifiers](identifiers-entity-sql.md).</span></span>

<span data-ttu-id="ab6c9-111">행 생성자에서 식에 별칭을 지정하는 데 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-111">The following rules apply to expression aliasing in a row constructor:</span></span>

- <span data-ttu-id="ab6c9-112">행 생성자의 식은 동일한 생성자 내의 다른 별칭을 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-112">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>
- <span data-ttu-id="ab6c9-113">동일한 행 생성자 내의 서로 다른 두 식은 별칭이 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-113">Two expressions in the same row constructor cannot have the same alias.</span></span>

<span data-ttu-id="ab6c9-114">행 생성자에 대 한 자세한 내용은 [row](row-entity-sql.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-114">For more information about row constructors, see [ROW](row-entity-sql.md).</span></span>

## <a name="collection-constructors"></a><span data-ttu-id="ab6c9-115">컬렉션 생성자</span><span class="sxs-lookup"><span data-stu-id="ab6c9-115">Collection Constructors</span></span>

<span data-ttu-id="ab6c9-116">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 컬렉션 생성자를 사용하여 값 목록에서 multiset 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-116">You use collection constructors in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="ab6c9-117">생성자의 모든 값은 상호 호환되는 `T` 형식이어야 하며, 생성자는 `Multiset<T>` 형식의 컬렉션을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-117">All the values in the constructor must be of mutually compatible type `T`, and the constructor produces a collection of type `Multiset<T>`.</span></span> <span data-ttu-id="ab6c9-118">예를 들어, 다음 식은 정수 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-118">For example, the following expression creates a collection of integers:</span></span>

`Multiset(1, 2, 3)`

`{1, 2, 3}`

<span data-ttu-id="ab6c9-119">빈 multiset 생성자는 요소 형식을 확인할 수 없으므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-119">Empty multiset constructors are not allowed because the type of the elements cannot be determined.</span></span> <span data-ttu-id="ab6c9-120">다음은 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-120">The following is not valid:</span></span>

`multiset() {}`

<span data-ttu-id="ab6c9-121">자세한 내용은 [MULTISET](multiset-entity-sql.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-121">For more information, see [MULTISET](multiset-entity-sql.md).</span></span>

## <a name="named-type-constructors-namedtype-initializers"></a><span data-ttu-id="ab6c9-122">명명된 형식 생성자(NamedType 이니셜라이저)</span><span class="sxs-lookup"><span data-stu-id="ab6c9-122">Named Type Constructors (NamedType Initializers)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ab6c9-123">에서 형식 생성자(이니셜라이저)는 명명된 복합 형식과 엔터티 형식 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-123">allows type constructors (initializers) to create instances of named complex types and entity types.</span></span> <span data-ttu-id="ab6c9-124">예를 들어, 다음 식은 `Person` 형식의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-124">For example, the following expression creates an instance of a `Person` type.</span></span>

`Person("abc", 12)`

<span data-ttu-id="ab6c9-125">다음 식은 복합 형식의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-125">The following expression creates an instance of a complex type.</span></span>

`MyModel.ZipCode(‘98118’, ‘4567’)`

<span data-ttu-id="ab6c9-126">다음 식은 중첩된 복합 형식의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-126">The following expression creates an instance of a nested complex type.</span></span>

`MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`

<span data-ttu-id="ab6c9-127">다음 식은 중첩된 복합 형식을 가진 엔터티의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-127">The following expression creates an instance of an entity with a nested complex type.</span></span>

`MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`

<span data-ttu-id="ab6c9-128">다음 예제에서는 복합 형식의 속성을 null로 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-128">The following example shows how to initialize a property of a complex type to null.</span></span> `MyModel.ZipCode(‘98118’, null)`

<span data-ttu-id="ab6c9-129">생성자의 인수는 형식의 특성 선언과 동일한 순서인 것으로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-129">The arguments to the constructor are assumed to be in the same order as the declaration of the attributes of the type.</span></span>

<span data-ttu-id="ab6c9-130">자세한 내용은 [명명 된 형식 생성자](named-type-constructor-entity-sql.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab6c9-130">For more information, see [Named Type Constructor](named-type-constructor-entity-sql.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab6c9-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab6c9-131">See also</span></span>

- [<span data-ttu-id="ab6c9-132">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="ab6c9-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ab6c9-133">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="ab6c9-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ab6c9-134">유형 시스템</span><span class="sxs-lookup"><span data-stu-id="ab6c9-134">Type System</span></span>](type-system-entity-sql.md)
