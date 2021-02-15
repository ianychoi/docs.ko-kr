---
description: '자세한 정보: 방법: Visual Basic에서 배열 변수 초기화'
title: '방법: 배열 변수 초기화'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 05cca98457a56db52ee99cfc4ac93c860da7a51d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427611"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="9f3cd-103">방법: Visual Basic에서 배열 변수 초기화</span><span class="sxs-lookup"><span data-stu-id="9f3cd-103">How to: Initialize an Array Variable in Visual Basic</span></span>

<span data-ttu-id="9f3cd-104">배열 리터럴을 절에 포함 하 `New` 고 배열의 초기 값을 지정 하 여 배열 변수를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-104">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="9f3cd-105">형식을 지정 하거나 배열 리터럴의 값에서 유추 되도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-105">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="9f3cd-106">형식을 유추 하는 방법에 대 한 자세한 내용은 [배열의](index.md)"초기 값으로 배열 채우기"를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-106">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="9f3cd-107">배열 리터럴을 사용 하 여 배열 변수를 초기화 하려면</span><span class="sxs-lookup"><span data-stu-id="9f3cd-107">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="9f3cd-108">`New`절에서 또는 배열 값을 할당 하는 경우 요소 값을 중괄호 () 안에 제공 `{}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-108">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="9f3cd-109">다음 예제에서는 형식의 요소가 포함 된 배열을 포함 하는 변수를 선언 하 고, 만들고, 초기화 하는 여러 가지 방법을 보여 줍니다 `Char` .</span><span class="sxs-lookup"><span data-stu-id="9f3cd-109">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="9f3cd-110">각 문이 실행 된 후 생성 된 배열의 길이는 3이 고 인덱스 0부터 인덱스 2 까지의 요소는 초기 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-110">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="9f3cd-111">상한과 값을 모두 제공 하는 경우 인덱스 0부터 상한 까지의 모든 요소에 대 한 값을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-111">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="9f3cd-112">배열 리터럴에 요소 값을 제공 하는 경우에는 인덱스 상한을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-112">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="9f3cd-113">상한을 지정 하지 않으면 배열 리터럴의 값 수를 기반으로 배열의 크기가 유추 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-113">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="9f3cd-114">배열 리터럴을 사용 하 여 다차원 배열 변수를 초기화 하려면</span><span class="sxs-lookup"><span data-stu-id="9f3cd-114">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="9f3cd-115">중괄호 내의 중괄호 () 안에 값을 중첩 `{}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-115">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="9f3cd-116">중첩 된 배열 리터럴이 모두 동일한 형식 및 길이의 배열로 유추 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-116">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="9f3cd-117">다음 코드 예제에서는 다차원 배열 초기화의 몇 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-117">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="9f3cd-118">배열 범위를 명시적으로 지정 하거나, 그대로 두고, 컴파일러가 배열 리터럴의 값을 기준으로 배열 범위를 유추 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-118">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="9f3cd-119">상한 및 값을 모두 제공 하는 경우 인덱스 0부터 모든 차원의 상한 사이의 모든 요소에 대 한 값을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-119">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="9f3cd-120">다음 예제에서는 형식의 요소가 있는 2 차원 배열을 포함 하는 변수를 선언 하 고, 만들고, 초기화 하는 여러 가지 방법을 보여 줍니다. `Short`</span><span class="sxs-lookup"><span data-stu-id="9f3cd-120">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="9f3cd-121">각 문이 실행 된 후 생성 된 배열에는,,,, 및 인덱스를 포함 하는 6 개의 초기화 된 요소가 포함 `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-121">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="9f3cd-122">각 배열 위치에는 값이 포함 `10` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-122">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="9f3cd-123">다음 예제에서는 다차원 배열을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-123">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="9f3cd-124">Visual Basic으로 작성 된 Windows 콘솔 응용 프로그램에서 메서드 안에 코드를 붙여넣습니다 `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="9f3cd-124">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="9f3cd-125">마지막 주석은 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-125">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="9f3cd-126">배열 리터럴을 사용 하 여 가변 배열 변수를 초기화 하려면</span><span class="sxs-lookup"><span data-stu-id="9f3cd-126">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="9f3cd-127">개체 값을 중괄호 () 안에 중첩 시킵니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="9f3cd-127">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="9f3cd-128">가변 배열의 경우에는 길이가 다른 배열을 지정 하는 배열 리터럴을 중첩할 수도 있지만 중첩 된 배열 리터럴이 괄호 ()로 묶여 있는지 확인 `()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-128">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="9f3cd-129">괄호는 중첩 된 배열 리터럴을 강제로 계산 하 고 결과 배열은 가변 배열의 초기 값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-129">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="9f3cd-130">다음 코드 예제에서는 가변 배열 초기화의 두 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-130">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="9f3cd-131">다음 예제에서는 가변 배열을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-131">The following example iterates through a jagged array.</span></span> <span data-ttu-id="9f3cd-132">Visual Basic으로 작성 된 Windows 콘솔 응용 프로그램에서 메서드 안에 코드를 붙여넣습니다 `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="9f3cd-132">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="9f3cd-133">코드의 마지막 주석은 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f3cd-133">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="9f3cd-134">참조</span><span class="sxs-lookup"><span data-stu-id="9f3cd-134">See also</span></span>

- [<span data-ttu-id="9f3cd-135">배열</span><span class="sxs-lookup"><span data-stu-id="9f3cd-135">Arrays</span></span>](index.md)
- [<span data-ttu-id="9f3cd-136">배열 문제 해결</span><span class="sxs-lookup"><span data-stu-id="9f3cd-136">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
