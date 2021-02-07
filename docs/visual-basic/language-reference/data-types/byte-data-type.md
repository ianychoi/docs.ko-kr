---
description: '자세한 정보: Byte 데이터 형식 (Visual Basic)'
title: Byte 데이터 형식
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 983af36d8340b5df7ac44782bf56349901460c20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731229"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="c1275-103">Byte 데이터 형식 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1275-103">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="c1275-104">0에서 255 사이의 값 범위에 해당 하는 부호 없는 8 비트 (1 바이트) 정수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-104">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1275-105">설명</span><span class="sxs-lookup"><span data-stu-id="c1275-105">Remarks</span></span>

<span data-ttu-id="c1275-106">`Byte`데이터 형식을 사용 하 여 이진 데이터를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-106">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="c1275-107">`Byte`의 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-107">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="c1275-108">리터럴 할당</span><span class="sxs-lookup"><span data-stu-id="c1275-108">Literal assignments</span></span>

<span data-ttu-id="c1275-109">`Byte`10 진수 리터럴, 16 진수 리터럴, 8 진수 리터럴 또는 (Visual Basic 2017부터) 이진 리터럴을 할당 하 여 변수를 선언 하 고 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-109">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="c1275-110">정수 리터럴이의 범위 밖에 있는 경우 (즉 보다 `Byte` 작거나 보다 <xref:System.Byte.MinValue?displayProperty=nameWithType> 큰 경우 <xref:System.Byte.MaxValue?displayProperty=nameWithType> ) 컴파일 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-110">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="c1275-111">다음 예제에서는 10 진수, 16 진수 및 이진 리터럴로 표현 된 201와 동일한 정수를 암시적으로 [정수](integer-data-type.md) 에서 값으로 변환 `byte` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-111">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="c1275-112">접두사 또는를 사용 하 여 `&h` `&H` 16 진수 리터럴을 표시 하거나, 접두사 또는을 사용 하 여 이진 리터럴을 표시 하 고, 접두사 또는를 사용 하 여 `&b` `&B` `&o` `&O` 8 진수 리터럴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="c1275-113">10진수 리터럴에는 접두사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c1275-114">Visual Basic 2017부터 `_` 다음 예제와 같이 밑줄 문자를 자릿수 구분 기호로 사용 하 여 가독성을 높일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="c1275-115">Visual Basic 15.5부터 `_` 접두사와 16 진수, 이진 또는 8 진수 숫자 사이의 선행 구분 기호로 밑줄 문자 ()를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="c1275-116">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c1275-116">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="c1275-117">프로그래밍 팁</span><span class="sxs-lookup"><span data-stu-id="c1275-117">Programming tips</span></span>

- <span data-ttu-id="c1275-118">**음수.**</span><span class="sxs-lookup"><span data-stu-id="c1275-118">**Negative Numbers.**</span></span> <span data-ttu-id="c1275-119">`Byte`는 부호 없는 형식이 기 때문에 음수를 나타낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-119">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="c1275-120">`-`형식을 반환 하는 식에 단항 빼기 () 연산자를 사용 하는 경우 `Byte` Visual Basic는 식을 `Short` 먼저 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="c1275-121">**형식 변환.**</span><span class="sxs-lookup"><span data-stu-id="c1275-121">**Format Conversions.**</span></span> <span data-ttu-id="c1275-122">Visual Basic 파일을 읽거나 쓸 때 또는 Dll, 메서드 및 속성을 호출 하는 경우 데이터 형식 간에 자동으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-122">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="c1275-123">변수 및 배열에 저장 된 이진 데이터 `Byte` 는 이러한 형식 변환 중에 보존 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-123">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="c1275-124">`String`ANSI 및 유니코드 형식 간에 변환 하는 동안 해당 내용이 손상 될 수 있으므로 이진 데이터에 대해 변수를 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-124">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="c1275-125">**넓혀.**</span><span class="sxs-lookup"><span data-stu-id="c1275-125">**Widening.**</span></span> <span data-ttu-id="c1275-126">`Byte`데이터 형식은,,,,,,, 또는로 확대 변환 `Short` `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` `Double` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-126">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="c1275-127">즉, `Byte` 오류가 발생 하지 않고 이러한 형식으로 변환할 수 있습니다 <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c1275-127">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="c1275-128">**문자를 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="c1275-128">**Type Characters.**</span></span> <span data-ttu-id="c1275-129">`Byte` 에는 리터럴 형식 문자 또는 식별자 형식 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-129">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="c1275-130">**Framework 형식.**</span><span class="sxs-lookup"><span data-stu-id="c1275-130">**Framework Type.**</span></span> <span data-ttu-id="c1275-131">.NET Framework에서 해당하는 형식은 <xref:System.Byte?displayProperty=nameWithType> 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-131">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="c1275-132">예제</span><span class="sxs-lookup"><span data-stu-id="c1275-132">Example</span></span>

 <span data-ttu-id="c1275-133">다음 예에서는 `b` 가 `Byte` 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-133">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="c1275-134">문은 변수의 범위와 비트 시프트 연산자의 응용 프로그램을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c1275-134">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="c1275-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1275-135">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="c1275-136">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c1275-136">Data Types</span></span>](index.md)
- [<span data-ttu-id="c1275-137">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="c1275-137">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="c1275-138">변환 요약</span><span class="sxs-lookup"><span data-stu-id="c1275-138">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="c1275-139">데이터 형식의 효율적 사용</span><span class="sxs-lookup"><span data-stu-id="c1275-139">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
