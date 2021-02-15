---
description: '자세한 정보: 숫자 데이터 형식 (Visual Basic)'
title: 숫자 데이터 형식
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 0e44301d953ab75378aabbec82fdb6dce00a02e2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430692"
---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="62371-103">숫자 데이터 형식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62371-103">Numeric Data Types (Visual Basic)</span></span>

<span data-ttu-id="62371-104">Visual Basic는 다양 한 표현에서 숫자를 처리 하기 위한 여러 *숫자 데이터 형식을* 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-104">Visual Basic supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="62371-105">정수 *계열* 형식은 정수 (양수, 음수 및 0)만 나타내고 정수 계열 형식은 정수 부분과 소수 부분을 모두 *포함 하는* 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62371-105">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="62371-106">Visual Basic 데이터 형식을 나란히 비교 하 여 보여 주는 표는 [데이터 형식](../../../language-reference/data-types/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62371-106">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="62371-107">정수 계열 숫자 형식</span><span class="sxs-lookup"><span data-stu-id="62371-107">Integral Numeric Types</span></span>  

 <span data-ttu-id="62371-108">*정수 계열 데이터 형식은* 소수 부분이 없는 숫자만을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62371-108">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="62371-109">*부호 있는* 정수 계열 데이터 형식은 [SByte 데이터 형식](../../../language-reference/data-types/sbyte-data-type.md) (8 비트), [Short 데이터 형식](../../../language-reference/data-types/short-data-type.md) (16 비트), [정수 데이터 형식](../../../language-reference/data-types/integer-data-type.md) (32 비트) 및 [Long 데이터 형식](../../../language-reference/data-types/long-data-type.md) (64 비트)입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-109">The *signed* integral data types are [SByte Data Type](../../../language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="62371-110">변수가 항상 소수 자릿수가 아닌 정수를 저장 하는 경우 이러한 형식 중 하나로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-110">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="62371-111">*부호 없는* 정수 형식은 [Byte 데이터 형식](../../../language-reference/data-types/byte-data-type.md) (8 비트), [UShort 데이터 형식](../../../language-reference/data-types/ushort-data-type.md) (16 비트), [UInteger 데이터 형식](../../../language-reference/data-types/uinteger-data-type.md) (32 비트) 및 [ULong 데이터 형식](../../../language-reference/data-types/ulong-data-type.md) (64 비트)입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-111">The *unsigned* integral types are [Byte Data Type](../../../language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="62371-112">변수가 이진 데이터를 포함 하거나 알 수 없는 형식의 데이터를 포함 하는 경우 이러한 형식 중 하나로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-112">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="62371-113">성능</span><span class="sxs-lookup"><span data-stu-id="62371-113">Performance</span></span>  

 <span data-ttu-id="62371-114">산술 연산은 다른 데이터 형식 보다 정수 계열 형식으로 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="62371-114">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="62371-115">`Integer`Visual Basic의 및 형식이 가장 빠르게 사용 됩니다 `UInteger` .</span><span class="sxs-lookup"><span data-stu-id="62371-115">They are fastest with the `Integer` and `UInteger` types in Visual Basic.</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="62371-116">매우 많은 정수</span><span class="sxs-lookup"><span data-stu-id="62371-116">Large Integers</span></span>  

 <span data-ttu-id="62371-117">데이터 형식이 보유할 수 있는 것 보다 큰 정수를 보유 해야 하는 경우에 `Integer` 는 `Long` 데이터 형식을 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-117">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="62371-118">`Long` 변수는-9223372036854775808에서 9223372036854775807 까지의 숫자를 보유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-118">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="62371-119">를 사용 하 `Long` 는 작업은 보다 약간 느립니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="62371-119">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="62371-120">훨씬 큰 값이 필요한 경우 [Decimal 데이터 형식을](../../../language-reference/data-types/decimal-data-type.md)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-120">If you need even larger values, you can use the [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="62371-121">`Decimal`소수 자릿수를 사용 하지 않는 경우 변수에-79228162514264337593543950335 ~ 79228162514264337593543950335를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-121">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="62371-122">그러나 숫자가 있는 연산은 `Decimal` 다른 숫자 데이터 형식 보다 훨씬 느립니다.</span><span class="sxs-lookup"><span data-stu-id="62371-122">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="62371-123">작은 정수</span><span class="sxs-lookup"><span data-stu-id="62371-123">Small Integers</span></span>  

 <span data-ttu-id="62371-124">데이터 형식의 전체 범위가 필요 하지 않은 경우에는 `Integer` `Short` -32768 ~ 32767의 정수를 포함할 수 있는 데이터 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-124">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="62371-125">가장 작은 정수 범위의 경우 `SByte` 데이터 형식에는-128에서 127 까지의 정수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62371-125">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="62371-126">작은 정수를 포함 하는 변수가 매우 많은 경우 공용 언어 런타임에서는 `Short` 및 `SByte` 변수를 보다 효율적으로 저장 하 고 메모리 사용을 절약 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-126">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="62371-127">그러나 및을 사용 `Short` 하 `SByte` 는 작업은 보다 약간 느립니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="62371-127">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="62371-128">부호 없는 정수</span><span class="sxs-lookup"><span data-stu-id="62371-128">Unsigned Integers</span></span>  

 <span data-ttu-id="62371-129">변수에 음수를 포함할 필요가 없는 경우 *부호 없는 형식인*,, 및를 사용할 수 있습니다 `Byte` `UShort` `UInteger` `ULong` .</span><span class="sxs-lookup"><span data-stu-id="62371-129">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="62371-130">이러한 각 데이터 형식에는 해당 하는 부호 있는 형식 ( `SByte` ,, `Short` `Integer` 및) 만큼 양의 정수를 두 번 포함할 수 있습니다 `Long` .</span><span class="sxs-lookup"><span data-stu-id="62371-130">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="62371-131">성능 측면에서 부호 없는 각 형식은 해당 하는 부호 있는 형식과 정확히 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-131">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="62371-132">특히 `UInteger` `Integer` 모든 기본 숫자 데이터 형식에 대 한 가장 효율적인 차이점을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-132">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="62371-133">비정 때 숫자 형식</span><span class="sxs-lookup"><span data-stu-id="62371-133">Nonintegral Numeric Types</span></span>  

 <span data-ttu-id="62371-134">*비정 수 데이터 형식은* 정수 부분과 소수 부분을 모두 포함 하는 숫자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62371-134">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="62371-135">비정 수 숫자 데이터 형식은 `Decimal` (128 비트 고정 소수점), [Single 데이터 형식](../../../language-reference/data-types/single-data-type.md) (32 비트 부동 소수점) 및 [Double 데이터 형식](../../../language-reference/data-types/double-data-type.md) (64 비트 부동 소수점)입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-135">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="62371-136">모든 부호 있는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-136">They are all signed types.</span></span> <span data-ttu-id="62371-137">변수가 분수를 포함할 수 있는 경우 이러한 형식 중 하나로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-137">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="62371-138">`Decimal` 이 부동 소수점 데이터 형식이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="62371-138">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="62371-139">`Decimal` 숫자에는 이진 정수 값과 소수 소수 부분을 지정 하는 정수 배율 인수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-139">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="62371-140">`Decimal`Money 값에 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-140">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="62371-141">장점은 값의 전체 자릿수입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-141">The advantage is the precision of the values.</span></span> <span data-ttu-id="62371-142">`Double`데이터 형식은 더 빠르며 메모리가 더 필요 하지만 반올림 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-142">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="62371-143">`Decimal`데이터 형식은 전체 정확도를 28 자리로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="62371-143">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="62371-144">부동 소수점 ( `Single` 및 `Double` ) 숫자의 범위는 숫자 보다 크지만 `Decimal` 반올림 오류의 영향을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-144">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="62371-145">부동 소수점 형식은 보다 작은 유효 자릿수를 지원 `Decimal` 하지만 크기가 큰 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-145">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="62371-146">비정 수 값은 mmmEeee로 표현할 수 있습니다. 여기서 mmm은가 *수 (유효* 숫자)이 고 eee는 *지* 수 (10의 거듭제곱)입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-146">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="62371-147">비정 수 형식의 가장 높은 양수 값은 7.9228162514264337593543950335 E + 28 for, 3.4028235 E + 38,에 대 한 `Decimal` `Single` 1.79769313486231570 e + 308 `Double` 입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-147">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="62371-148">성능</span><span class="sxs-lookup"><span data-stu-id="62371-148">Performance</span></span>  

 <span data-ttu-id="62371-149">`Double` 현재 플랫폼의 프로세서에서 배정밀도의 부동 소수점 연산을 수행 하기 때문에는 소수 데이터 형식이 가장 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-149">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="62371-150">그러나를 사용 하 `Double` 는 연산은와 같은 정수 계열 형식과는 속도가 빠르지 않습니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="62371-150">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="62371-151">Small 크고 많을</span><span class="sxs-lookup"><span data-stu-id="62371-151">Small Magnitudes</span></span>  

 <span data-ttu-id="62371-152">가장 작은 크기 (0에 가장 가깝습니다)가 있는 숫자의 경우 `Double` 변수는 음수 값에 대해-4.94065645841246544 e-324로 작은 숫자를, 양수 값의 경우 4.94065645841246544 e-324을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-152">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="62371-153">작은 분수 숫자</span><span class="sxs-lookup"><span data-stu-id="62371-153">Small Fractional Numbers</span></span>  

 <span data-ttu-id="62371-154">데이터 형식의 전체 범위가 필요 하지 않은 경우 `Double` `Single` -3.4028235 e + 38에서 3.4028235 e + 38 까지의 부동 소수점 수를 포함할 수 있는 데이터 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-154">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="62371-155">변수에 대 한 최소 크고 많을는 `Single` 음수 값의 경우-1.401298 e-45이 고 양수 값의 경우 1.401298 e-45입니다.</span><span class="sxs-lookup"><span data-stu-id="62371-155">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="62371-156">작은 부동 소수점 숫자를 포함 하는 변수를 매우 많이 사용 하는 경우 공용 언어 런타임에서는 때때로 `Single` 변수를 더 효율적으로 저장 하 고 메모리 사용을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62371-156">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62371-157">추가 정보</span><span class="sxs-lookup"><span data-stu-id="62371-157">See also</span></span>

- [<span data-ttu-id="62371-158">기본 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="62371-158">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="62371-159">문자 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="62371-159">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="62371-160">기타 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="62371-160">Miscellaneous Data Types</span></span>](miscellaneous-data-types.md)
- [<span data-ttu-id="62371-161">데이터 형식 문제 해결</span><span class="sxs-lookup"><span data-stu-id="62371-161">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="62371-162">방법: 부호 없는 형식을 사용하는 Windows 함수 호출</span><span class="sxs-lookup"><span data-stu-id="62371-162">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
