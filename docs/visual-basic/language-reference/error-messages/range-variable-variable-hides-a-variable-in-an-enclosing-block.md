---
description: '자세히 알아보기: BC36633: 범위 변수는 <variable> 바깥쪽 블록의 변수, 이전에 정의한 범위 변수 또는 쿼리 식에 암시적으로 선언한 변수를 숨깁니다.'
title: <variable> 범위 변수가 바깥쪽 블록의 변수, 이전에 정의한 범위 변수 또는 쿼리 식에 암시적으로 선언한 변수를 숨깁니다.
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f8e5c109274af9c00963e8a9f18384a299d17a4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792078"
---
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="ec733-103">BC36633: 범위 변수는 \<variable> 바깥쪽 블록의 변수, 이전에 정의한 범위 변수 또는 쿼리 식에 암시적으로 선언한 변수를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="ec733-103">BC36633: Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>

<span data-ttu-id="ec733-104">,, 또는 절에 지정 된 범위 변수 이름이 `Select` `From` `Aggregate` `Let` 쿼리에서 이미 이전에 지정 된 범위 변수의 이름 또는 쿼리에서 암시적으로 선언 된 변수 이름 (예: 필드 이름 또는 집계 함수의 이름)을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec733-104">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>

 <span data-ttu-id="ec733-105">**오류 ID:** BC36633</span><span class="sxs-lookup"><span data-stu-id="ec733-105">**Error ID:** BC36633</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec733-106">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="ec733-106">To correct this error</span></span>

- <span data-ttu-id="ec733-107">특정 쿼리 범위의 모든 범위 변수 이름이 고유한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec733-107">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="ec733-108">쿼리를 괄호로 묶어 중첩 된 쿼리에 고유한 범위가 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec733-108">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec733-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec733-109">See also</span></span>

- [<span data-ttu-id="ec733-110">Visual Basic의 LINQ 소개</span><span class="sxs-lookup"><span data-stu-id="ec733-110">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ec733-111">From 절</span><span class="sxs-lookup"><span data-stu-id="ec733-111">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="ec733-112">Let 절</span><span class="sxs-lookup"><span data-stu-id="ec733-112">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="ec733-113">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="ec733-113">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="ec733-114">Select 절</span><span class="sxs-lookup"><span data-stu-id="ec733-114">Select Clause</span></span>](../queries/select-clause.md)
