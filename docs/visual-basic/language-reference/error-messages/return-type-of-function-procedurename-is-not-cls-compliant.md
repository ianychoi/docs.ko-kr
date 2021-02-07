---
description: "자세한 정보: BC40027: ' ' 함수의 반환 형식이 <procedurename> CLS 규격이 아닙니다."
title: "'<procedurename>' 함수의 반환 형식이 CLS 규격이 아닙니다."
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: df0cdb10ebc62a833cef89d3e82bc1ed756c556e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675119"
---
# <a name="bc40027-return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="414e6-103">BC40027: ' ' 함수의 반환 형식이 \<procedurename> CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-103">BC40027: Return type of function '\<procedurename>' is not CLS-compliant</span></span>

<span data-ttu-id="414e6-104">`Function`프로시저는로 표시 `<CLSCompliant(True)>` 되지만로 표시 되었거나 `<CLSCompliant(False)>` , 표시 되지 않았거나, 비규격 형식 이므로 한정 되지 않는 형식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-104">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>

 <span data-ttu-id="414e6-105">프로시저가 [언어 독립성 및 언어 독립적 구성 요소](../../../standard/language-independence-and-language-independent-components.md)(CLS)와 호환되려면 CLS 규격 형식만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-105">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="414e6-106">이는 매개 변수 형식, 반환 형식 및 모든 로컬 변수 형식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-106">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>

 <span data-ttu-id="414e6-107">다음 Visual Basic 데이터 형식은 CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="414e6-108">SByte 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="414e6-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="414e6-109">UInteger 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="414e6-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="414e6-110">ULong 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="414e6-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="414e6-111">UShort 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="414e6-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="414e6-112"><xref:System.CLSCompliantAttribute> 를 프로그래밍 요소에 적용하는 경우 특성의 `isCompliant` 매개 변수를 `True` 또는 `False` 로 설정하여 준수 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-112">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="414e6-113">이 매개 변수에는 기본값이 없으며 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-113">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="414e6-114">요소에 <xref:System.CLSCompliantAttribute> 를 적용하지 않으면 비규격인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-114">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="414e6-115">이 메시지는 기본적으로 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-115">By default, this message is a warning.</span></span> <span data-ttu-id="414e6-116">경고를 숨기거나 오류로 처리하는 방법에 대한 자세한 내용은 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="414e6-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="414e6-117">**오류 ID:** BC40027</span><span class="sxs-lookup"><span data-stu-id="414e6-117">**Error ID:** BC40027</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="414e6-118">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="414e6-118">To correct this error</span></span>

- <span data-ttu-id="414e6-119">`Function`프로시저가이 특정 형식을 반환 해야 하는 경우를 제거 <xref:System.CLSCompliantAttribute> 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-119">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="414e6-120">프로시저는 CLS 규격일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-120">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="414e6-121">프로시저가 CLS 규격 이어야 하는 경우 `Function` 반환 형식을 가장 가까운 cls 규격 형식으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-121">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="414e6-122">예를 들어 2,147,483,647을 초과하는 값 범위가 필요하지 않은 경우 `UInteger` 대신 `Integer` 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="414e6-123">확장된 범위가 필요한 경우 `UInteger` 를 `Long`으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="414e6-124">Automation 또는 COM 개체와 상호 작용 하는 경우 일부 형식의 데이터 너비가 .NET Framework에 비해 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="414e6-125">예를 들어 `int`는 다른 환경에서 16비트인 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="414e6-126">이러한 구성 요소에 16 비트 정수를 반환 하는 경우 `Short` `Integer` 관리 되는 Visual Basic 코드에서 대신로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="414e6-126">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
