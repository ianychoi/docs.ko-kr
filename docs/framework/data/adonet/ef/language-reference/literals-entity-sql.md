---
description: '자세한 정보: 리터럴 (Entity SQL)'
title: 리터럴(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: cae2ec7ab8cf19166dc3100a85473fca2ed0a7be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791883"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="6d8ed-103">리터럴(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6d8ed-103">Literals (Entity SQL)</span></span>

<span data-ttu-id="6d8ed-104">이 항목에서는 리터럴에 대한 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 지원을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-104">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="6d8ed-105">Null</span><span class="sxs-lookup"><span data-stu-id="6d8ed-105">Null</span></span>  

 <span data-ttu-id="6d8ed-106">null 리터럴은 모든 형식의 null 값을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-106">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="6d8ed-107">null 리터럴은 모든 형식과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-107">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="6d8ed-108">형식화된 null은 null 리터럴에 대한 캐스트를 통해 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-108">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="6d8ed-109">자세한 내용은 [CAST](cast-entity-sql.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-109">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="6d8ed-110">자유 부동 null 리터럴을 사용할 수 있는 위치에 대 한 규칙은 [Null 리터럴 및 형식 유추](null-literals-and-type-inference-entity-sql.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-110">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="6d8ed-111">부울</span><span class="sxs-lookup"><span data-stu-id="6d8ed-111">Boolean</span></span>  

 <span data-ttu-id="6d8ed-112">Boolean 리터럴은 `true` 및 `false` 키워드로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-112">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="6d8ed-113">정수</span><span class="sxs-lookup"><span data-stu-id="6d8ed-113">Integer</span></span>  

 <span data-ttu-id="6d8ed-114">Integer 리터럴은 <xref:System.Int32> 또는 <xref:System.Int64> 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-114">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="6d8ed-115"><xref:System.Int32> 리터럴은 일련의 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-115">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="6d8ed-116"><xref:System.Int64> 리터럴은 맨 뒤에 대문자 L이 오는 일련의 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-116">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="6d8ed-117">Decimal</span><span class="sxs-lookup"><span data-stu-id="6d8ed-117">Decimal</span></span>  

 <span data-ttu-id="6d8ed-118">고정 소수점 수는 일련의 숫자, 점(.) 및 다른 일련의 숫자로 구성되며 맨 뒤에 대문자로 된 "M"이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-118">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="6d8ed-119">Float, Double</span><span class="sxs-lookup"><span data-stu-id="6d8ed-119">Float, Double</span></span>  

 <span data-ttu-id="6d8ed-120">배정밀도 부동 소수점 수는 일련의 숫자, 점(.) 및 다른 일련의 숫자로 구성되며 맨 뒤에 지수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-120">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="6d8ed-121">단정밀도 부동 소수점 수(또는 float)는 배정밀도 부동 소수점 수 구문 뒤에 소문자 f가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-121">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="6d8ed-122">String</span><span class="sxs-lookup"><span data-stu-id="6d8ed-122">String</span></span>  

 <span data-ttu-id="6d8ed-123">문자열은 따옴표로 묶인 일련의 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-123">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="6d8ed-124">따옴표는 양쪽 모두 작은따옴표(`'`)이거나 큰따옴표(")일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-124">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="6d8ed-125">문자열 리터럴은 유니코드이거나 비유니코드일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-125">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="6d8ed-126">문자열 리터럴을 유니코드로 선언하려면 리터럴 앞에 대문자 "N"을 접두사로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-126">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="6d8ed-127">기본값은 비유니코드 문자열 리터럴입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-127">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="6d8ed-128">N과 문자열 리터럴 페이로드 사이에는 공백을 사용할 수 없으며 N은 대문자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-128">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="6d8ed-129">DateTime</span><span class="sxs-lookup"><span data-stu-id="6d8ed-129">DateTime</span></span>  

 <span data-ttu-id="6d8ed-130">datetime 리터럴은 로캘과 무관하며 날짜 부분과 시간 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-130">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="6d8ed-131">날짜 및 시간 부분은 모두 필수 요소이며 기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-131">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="6d8ed-132">날짜 부분의 형식은 다음과 같아야 합니다. `YYYY` - `MM` - `DD` 여기서 `YYYY` 은 0001과 9999 사이의 4 자리 연도 값이 고,은 `MM` 1에서 12 사이의 월 이며,는 `DD` 지정 된 월에 유효한 일 값입니다 `MM` .</span><span class="sxs-lookup"><span data-stu-id="6d8ed-132">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="6d8ed-133">시간 부분의 형식은 `HH`:`MM`[:`SS`[.fffffff]]이어야 하며, 여기서 `HH`는 0에서 23 사이의 시간 값이고, `MM`은 0에서 59 사이의 분 값이며, `SS`는 0에서 59 사이의 초 값이며, fffffff는 0에서 9999999 사이의 소수로 나타낸 초 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-133">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="6d8ed-134">모든 값 범위에서 해당 시작 값과 끝 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-134">All value ranges are inclusive.</span></span> <span data-ttu-id="6d8ed-135">소수로 나타낸 초는 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-135">Fractional seconds are optional.</span></span> <span data-ttu-id="6d8ed-136">소수로 나타낸 초가 지정되지 않은 경우 초를 선택하며, 이 경우 초는 필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-136">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6d8ed-137">초 또는 소수로 나타낸 초가 지정되지 않은 경우에는 기본값 0이 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-137">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="6d8ed-138">DATETIME 기호와 리터럴 페이로드 사이에 들어갈 수 있는 공백의 수는 제한이 없지만 줄 바꿈은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-138">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="6d8ed-139">시간</span><span class="sxs-lookup"><span data-stu-id="6d8ed-139">Time</span></span>  

 <span data-ttu-id="6d8ed-140">time 리터럴은 로캘과 무관하며 시간 부분만으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-140">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="6d8ed-141">시간 부분은 필수 요소이며 기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-141">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="6d8ed-142">이 형식은 HH:MM[:SS[.fffffff]]이어야 하며, 여기서 HH는 0에서 23 사이의 시간 값이고, MM은 0에서 59 사이의 분 값이며, SS는 0에서 59 사이의 초 값이며, fffffff는 0에서 9999999 사이의 소수로 나타낸 초 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-142">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="6d8ed-143">모든 값 범위에서 해당 시작 값과 끝 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-143">All value ranges are inclusive.</span></span> <span data-ttu-id="6d8ed-144">소수로 나타낸 초는 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-144">Fractional seconds are optional.</span></span> <span data-ttu-id="6d8ed-145">소수로 나타낸 초가 지정되지 않은 경우 초를 선택하며, 이 경우 초는 필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-145">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6d8ed-146">초 또는 소수로 나타낸 초가 지정되지 않은 경우에는 기본값 0이 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-146">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="6d8ed-147">TIME 기호와 리터럴 페이로드 사이에 들어갈 수 있는 공백의 수는 제한이 없지만 줄 바꿈은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-147">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="6d8ed-148">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6d8ed-148">DateTimeOffset</span></span>  

 <span data-ttu-id="6d8ed-149">datetimeoffset 리터럴은 로캘과 무관하며 날짜 부분, 시간 부분 및 오프셋 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-149">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="6d8ed-150">날짜, 시간, 오프셋 부분은 모두 필수 요소이며 기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-150">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="6d8ed-151">날짜 부분의 형식은 YYYY-MM-DD여야 하며, 여기서 YYYY는 0001에서 9999 사이의 4자리 연도 값이고, MM은 1에서 12 사이의 월이며, DD는 지정된 월에 유효한 일 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-151">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="6d8ed-152">시간 부분의 형식은 HH:MM[:SS[.fffffff]]이어야 하며, 여기서 HH는 0에서 23 사이의 시간 값이고, MM은 0에서 59 사이의 분 값이며, SS는 0에서 59 사이의 초 값이며, fffffff는 0에서 9999999 사이의 소수로 나타낸 초 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-152">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="6d8ed-153">모든 값 범위에서 해당 시작 값과 끝 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-153">All value ranges are inclusive.</span></span> <span data-ttu-id="6d8ed-154">소수로 나타낸 초는 선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-154">Fractional seconds are optional.</span></span> <span data-ttu-id="6d8ed-155">소수로 나타낸 초가 지정되지 않은 경우 초를 선택하며, 이 경우 초는 필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-155">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6d8ed-156">초 또는 소수로 나타낸 초가 지정되지 않은 경우에는 기본값 0이 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-156">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="6d8ed-157">오프셋 부분은 {+&#124;-} HH: MM 형식 이어야 합니다. 여기서 HH와 MM은 시간 부분과 동일한 의미를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-157">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="6d8ed-158">하지만 오프셋의 경우 범위가 -14:00과 + 14:00 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-158">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="6d8ed-159">DATETIMEOFFSET 기호와 리터럴 페이로드 사이에 들어갈 수 있는 공백의 수는 제한이 없지만 줄 바꿈은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-159">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="6d8ed-160">유효한 Entity SQL 리터럴 값이 CLR 또는 데이터 소스에 대한 지원 범위를 벗어날 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="6d8ed-160">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="6d8ed-161">이런 경우 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-161">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="6d8ed-162">이진</span><span class="sxs-lookup"><span data-stu-id="6d8ed-162">Binary</span></span>  

 <span data-ttu-id="6d8ed-163">이진 문자열 리터럴은 키워드 binary 또는 바로 가기 기호 `X` 또는 `x` 뒤에 작은따옴표로 구분되는 16진수 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-163">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="6d8ed-164">바로 가기 기호인 `X`는 대소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-164">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="6d8ed-165">키워드 `binary`와 이진 문자열 값 사이에는 하나 이상의 공백을 사용하거나 사용하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-165">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="6d8ed-166">16진수 문자도 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-166">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="6d8ed-167">리터럴을 구성하는 16진수의 자릿수가 홀수인 경우 해당 리터럴의 맨 앞에 16진수 0이 추가되어 다음 짝수의 16진수에 맞춰 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-167">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="6d8ed-168">이진 문자열 크기에 대한 공식적인 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-168">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="6d8ed-169">GUID</span><span class="sxs-lookup"><span data-stu-id="6d8ed-169">Guid</span></span>  

 <span data-ttu-id="6d8ed-170">`GUID` 리터럴은 GUID(Globally Unique Identifier)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-170">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="6d8ed-171">이 시퀀스는 키워드에 의해 구성 된 시퀀스로, `GUID` *레지스트리* 형식 (8-4-4-4-12) 형식으로 된 16 진수 숫자 (작은따옴표로 묶여 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-171">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="6d8ed-172">16진수는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-172">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="6d8ed-173">GUID 기호와 리터럴 페이로드 사이에 들어갈 수 있는 공백의 수는 제한이 없지만 줄 바꿈은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d8ed-173">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d8ed-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d8ed-174">See also</span></span>

- [<span data-ttu-id="6d8ed-175">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="6d8ed-175">Entity SQL Overview</span></span>](entity-sql-overview.md)
