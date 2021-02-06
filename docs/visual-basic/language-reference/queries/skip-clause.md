---
description: '자세한 정보: Skip 절 (Visual Basic)'
title: Skip 절
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 6af702f65a724ea8c3d5a6122fb5f7a0ed5f6755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653552"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="d6ff4-103">Skip 절 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6ff4-103">Skip Clause (Visual Basic)</span></span>

<span data-ttu-id="d6ff4-104">컬렉션에서 지정된 수의 요소를 무시하고 나머지 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-104">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ff4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d6ff4-105">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="d6ff4-106">부분</span><span class="sxs-lookup"><span data-stu-id="d6ff4-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="d6ff4-107">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-107">Required.</span></span> <span data-ttu-id="d6ff4-108">건너뛸 시퀀스의 요소 수로 계산 되는 값 또는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-108">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ff4-109">설명</span><span class="sxs-lookup"><span data-stu-id="d6ff4-109">Remarks</span></span>  

 <span data-ttu-id="d6ff4-110">절을 사용 `Skip` 하면 쿼리가 결과 목록의 시작 부분에 있는 요소를 무시 하 고 나머지 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-110">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="d6ff4-111">건너뛸 요소의 수는 `count` 매개 변수로 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-111">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="d6ff4-112">절 `Skip` 과 함께 절을 사용 `Take` 하 여 쿼리 세그먼트의 데이터 범위를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-112">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="d6ff4-113">이렇게 하려면 범위의 첫 번째 요소 인덱스를 절에 전달 하 `Skip` 고 범위의 크기를 절에 전달 `Take` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="d6ff4-114">쿼리에서 절을 사용 하는 경우 절에서 의도 한 결과를 무시 하도록 하는 `Skip` 순서로 결과가 반환 되는지 확인 해야 할 수도 있습니다 `Skip` .</span><span class="sxs-lookup"><span data-stu-id="d6ff4-114">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="d6ff4-115">쿼리 결과를 정렬 하는 방법에 대 한 자세한 내용은 [Order By 절](order-by-clause.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="d6ff4-116">`SkipWhile`제공 된 조건에 따라 특정 요소만 무시 되도록 지정 하려면 절을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-116">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ff4-117">예제</span><span class="sxs-lookup"><span data-stu-id="d6ff4-117">Example</span></span>  

 <span data-ttu-id="d6ff4-118">다음 코드 예에서는 절과 함께 절을 사용 하 여 `Skip` `Take` 페이지의 쿼리에서 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-118">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="d6ff4-119">함수는 절을 사용 하 여 `GetCustomers` `Skip` 제공 된 시작 인덱스 값까지 목록의 고객을 우회 하 고 절을 사용 하 여 `Take` 해당 인덱스 값에서 시작 하는 고객의 페이지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6ff4-119">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ff4-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6ff4-120">See also</span></span>

- [<span data-ttu-id="d6ff4-121">Visual Basic의 LINQ 소개</span><span class="sxs-lookup"><span data-stu-id="d6ff4-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d6ff4-122">쿼리</span><span class="sxs-lookup"><span data-stu-id="d6ff4-122">Queries</span></span>](index.md)
- [<span data-ttu-id="d6ff4-123">Select 절</span><span class="sxs-lookup"><span data-stu-id="d6ff4-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d6ff4-124">From 절</span><span class="sxs-lookup"><span data-stu-id="d6ff4-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="d6ff4-125">Order By 절</span><span class="sxs-lookup"><span data-stu-id="d6ff4-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="d6ff4-126">Skip While 절</span><span class="sxs-lookup"><span data-stu-id="d6ff4-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="d6ff4-127">Take 절</span><span class="sxs-lookup"><span data-stu-id="d6ff4-127">Take Clause</span></span>](take-clause.md)
