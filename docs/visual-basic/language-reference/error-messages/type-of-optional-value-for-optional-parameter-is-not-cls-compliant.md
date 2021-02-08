---
description: '자세히 알아보기: BC40042: 선택적 매개 변수에 대 한 선택적 값의 형식이 <parametername> CLS 규격이 아님'
title: 선택적 매개 변수 <parametername>에 대한 선택적 값의 형식이 CLS 규격이 아닙니다.
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 44dee07120ebcd99be69257aef6a334f9067cdb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774865"
---
# <a name="bc40042-type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="133a9-103">BC40042: 선택적 매개 변수에 대 한 선택적 값의 형식이 \<parametername> CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-103">BC40042: Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>

<span data-ttu-id="133a9-104">프로시저는 `<CLSCompliant(True)>`로 표시되지만 비규격 형식의 기본값을 가진 [선택적](../modifiers/optional.md) 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-104">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>

 <span data-ttu-id="133a9-105">프로시저가 [언어 독립성 및 언어 독립적 구성 요소](../../../standard/language-independence-and-language-independent-components.md)(CLS)와 호환되려면 CLS 규격 형식만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="133a9-106">이는 매개 변수 형식, 반환 형식 및 모든 로컬 변수 형식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="133a9-107">또한 선택적 매개 변수의 기본값에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-107">It also applies to the default values of optional parameters.</span></span>

 <span data-ttu-id="133a9-108">다음 Visual Basic 데이터 형식은 CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-108">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="133a9-109">SByte 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="133a9-109">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="133a9-110">UInteger 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="133a9-110">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="133a9-111">ULong 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="133a9-111">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="133a9-112">UShort 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="133a9-112">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="133a9-113"><xref:System.CLSCompliantAttribute> 특성을 프로그래밍 요소에 적용하는 경우 특성의 `isCompliant` 매개 변수를 `True` 또는 `False` 로 설정하여 준수 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-113">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="133a9-114">이 매개 변수에는 기본값이 없으며 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-114">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="133a9-115">요소에 <xref:System.CLSCompliantAttribute> 를 적용하지 않으면 비규격인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-115">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="133a9-116">이 메시지는 기본적으로 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-116">By default, this message is a warning.</span></span> <span data-ttu-id="133a9-117">경고를 숨기거나 오류로 처리하는 방법에 대한 자세한 내용은 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="133a9-117">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="133a9-118">**오류 ID:** BC40042</span><span class="sxs-lookup"><span data-stu-id="133a9-118">**Error ID:** BC40042</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="133a9-119">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="133a9-119">To correct this error</span></span>

- <span data-ttu-id="133a9-120">선택적 매개 변수에이 특정 형식의 기본값이 있어야 하는 경우를 제거 <xref:System.CLSCompliantAttribute> 합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-120">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="133a9-121">프로시저는 CLS 규격일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-121">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="133a9-122">프로시저가 CLS 규격이어야 하는 경우 이 기본값의 형식을 가장 가까운 CLS 규격 형식으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-122">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="133a9-123">예를 들어 2,147,483,647을 초과하는 값 범위가 필요하지 않은 경우 `UInteger` 대신 `Integer` 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-123">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="133a9-124">확장된 범위가 필요한 경우 `UInteger` 를 `Long`으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-124">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="133a9-125">Automation 또는 COM 개체와 상호 작용 하는 경우 일부 형식의 데이터 너비가 .NET Framework에 비해 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-125">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="133a9-126">예를 들어 `int`는 다른 환경에서 16비트인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-126">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="133a9-127">이러한 구성 요소에서 16 비트 정수를 허용 하는 경우 `Short` `Integer` 관리 되는 Visual Basic 코드에서 대신로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="133a9-127">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
