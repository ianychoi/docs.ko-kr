---
description: '자세한 정보: 문자열과 다른 형식 간 변환 (Visual Basic)'
title: 문자열과 다른 형식 사이의 변환
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: c0f7f7637d173d039d58b2516fba41ae55b990ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477218"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="5946c-103">문자열과 다른 형식 사이의 변환(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5946c-103">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="5946c-104">숫자, `Boolean` 또는 날짜/시간 값을으로 변환할 수 있습니다 `String` .</span><span class="sxs-lookup"><span data-stu-id="5946c-104">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="5946c-105">문자열 `Boolean` `Date` 의 내용이 대상 데이터 형식의 유효한 값으로 해석 될 수 있는 경우 문자열 값에서 숫자, 또는로 역방향 방향을 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-105">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="5946c-106">사용할 수 없는 경우 런타임 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-106">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="5946c-107">어느 방향에서 든 이러한 모든 할당에 대 한 변환은 축소 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-107">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="5946c-108">형식 변환 키워드 (,,,,,,,,,,,,, `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` `CStr` `CUInt` `CULng` `CUShort` 및 `CType` )를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-108">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="5946c-109"><xref:Microsoft.VisualBasic.Strings.Format%2A>및 함수를 통해 <xref:Microsoft.VisualBasic.Conversion.Val%2A> 문자열과 숫자 간의 변환을 추가로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-109">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="5946c-110">클래스 또는 구조체를 정의한 경우 `String` 와 클래스 또는 구조체의 형식 간에 형식 변환 연산자를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-110">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="5946c-111">자세한 내용은 [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5946c-111">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="5946c-112">숫자를 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="5946c-112">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="5946c-113">함수를 사용 하 여 `Format` 숫자를 서식이 지정 된 문자열로 변환할 수 있습니다. 여기에는 해당 숫자 뿐만 아니라 통화 기호 (예: `$` ), 천 단위 구분 기호 또는 *자릿수 그룹화 기호* (예:) `,` 및 소수 구분 기호 (예:)와 같은 기호에 대 한 서식 지정도 포함 될 수 있습니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="5946c-113">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="5946c-114">`Format`는 Windows **제어판** 에 지정 된 **국가별 옵션** 설정에 따라 적절 한 기호를 자동으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-114">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="5946c-115">`&`다음 예제에 나와 있는 것 처럼 연결 () 연산자는 숫자를 암시적으로 문자열로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-115">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="5946c-116">문자열을 숫자로 변환</span><span class="sxs-lookup"><span data-stu-id="5946c-116">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="5946c-117">함수를 사용 하 여 `Val` 문자열의 숫자를 숫자로 명시적으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-117">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="5946c-118">`Val` 숫자, 공백, 탭, 줄 바꿈 또는 마침표 이외의 문자가 나타날 때까지 문자열을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-118">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="5946c-119">"&O" 및 "&H" 시퀀스는 번호 시스템의 밑수를 변경 하 고 검색을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-119">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="5946c-120">에서 읽기를 중지할 때까지는 `Val` 적절 한 모든 문자를 숫자 값으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-120">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="5946c-121">예를 들어 다음 문은 값을 반환 합니다 `141.825` .</span><span class="sxs-lookup"><span data-stu-id="5946c-121">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="5946c-122">Visual Basic 문자열을 숫자 값으로 변환 하는 경우 Windows **제어판** 에 지정 된 **국가별 옵션** 설정을 사용 하 여 천 단위 구분 기호, 소수 구분 기호 및 통화 기호를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-122">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="5946c-123">즉, 한 설정에서는 변환이 성공 하지만 다른 설정에는 성공 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-123">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="5946c-124">예를 들어 `"$14.20"` 은 영어 (미국) 로캘에서는 사용할 수 있지만 프랑스어 로캘에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5946c-124">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5946c-125">추가 정보</span><span class="sxs-lookup"><span data-stu-id="5946c-125">See also</span></span>

- [<span data-ttu-id="5946c-126">Visual Basic의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="5946c-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5946c-127">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="5946c-127">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5946c-128">암시적 변환과 명시적 변환</span><span class="sxs-lookup"><span data-stu-id="5946c-128">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5946c-129">방법: Visual Basic에서 Object를 다른 형식으로 변환</span><span class="sxs-lookup"><span data-stu-id="5946c-129">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="5946c-130">배열 규칙</span><span class="sxs-lookup"><span data-stu-id="5946c-130">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="5946c-131">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5946c-131">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5946c-132">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="5946c-132">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5946c-133">세계화 및 지역화된 앱 개발</span><span class="sxs-lookup"><span data-stu-id="5946c-133">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
