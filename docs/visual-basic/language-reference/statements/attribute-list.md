---
description: '자세한 정보: 특성 목록 (Visual Basic)'
title: 특성 목록
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: bde9387a48001a2696a6f69454edc311e7597bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674040"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="ba0bb-103">특성 목록(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba0bb-103">Attribute List (Visual Basic)</span></span>

<span data-ttu-id="ba0bb-104">선언 된 프로그래밍 요소에 적용할 특성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-104">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="ba0bb-105">여러 특성은 쉼표로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-105">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="ba0bb-106">다음은 한 특성에 대 한 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-106">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba0bb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba0bb-107">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ba0bb-108">부분</span><span class="sxs-lookup"><span data-stu-id="ba0bb-108">Parts</span></span>  

|||
|---|---|
|`attributemodifier`|<span data-ttu-id="ba0bb-109">소스 파일의 시작 부분에 적용 되는 특성에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-109">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="ba0bb-110">[어셈블리](../modifiers/assembly.md) 또는 [모듈인](../modifiers/module-keyword.md)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-110">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="ba0bb-111">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-111">Required.</span></span> <span data-ttu-id="ba0bb-112">특성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-112">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="ba0bb-113">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-113">Optional.</span></span> <span data-ttu-id="ba0bb-114">이 특성의 위치 인수 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-114">List of positional arguments for this attribute.</span></span> <span data-ttu-id="ba0bb-115">여러 인수를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-115">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="ba0bb-116">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-116">Optional.</span></span> <span data-ttu-id="ba0bb-117">이 특성에 대 한 변수 또는 속성 이니셜라이저의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-117">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="ba0bb-118">여러 이니셜라이저는 쉼표로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-118">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="ba0bb-119">설명</span><span class="sxs-lookup"><span data-stu-id="ba0bb-119">Remarks</span></span>  

 <span data-ttu-id="ba0bb-120">거의 모든 프로그래밍 요소 (형식, 프로시저, 속성 등)에 하나 이상의 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-120">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="ba0bb-121">특성은 어셈블리의 메타 데이터에 표시 되며, 코드에 주석을 달고 특정 프로그래밍 요소를 사용 하는 방법을 지정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-121">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="ba0bb-122">Visual Basic 및 .NET Framework에 의해 정의 된 특성을 적용 하 고 사용자 고유의 특성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-122">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="ba0bb-123">특성을 사용 하는 경우에 대 한 자세한 내용은 [특성 개요](../../programming-guide/concepts/attributes/index.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-123">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="ba0bb-124">특성 이름에 대 한 자세한 내용은 [선언 된 요소 이름](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-124">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ba0bb-125">규칙</span><span class="sxs-lookup"><span data-stu-id="ba0bb-125">Rules</span></span>  
  
- <span data-ttu-id="ba0bb-126">**배치가.**</span><span class="sxs-lookup"><span data-stu-id="ba0bb-126">**Placement.**</span></span> <span data-ttu-id="ba0bb-127">대부분의 선언 된 프로그래밍 요소에 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-127">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="ba0bb-128">하나 이상의 특성을 적용 하려면 요소 선언의 시작 부분에 *특성 블록* 을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-128">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="ba0bb-129">특성 목록의 각 항목은 적용 하려는 특성을 지정 하 고이 특성 호출에 사용 하는 한정자 및 인수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-129">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="ba0bb-130">**꺾쇠 괄호입니다.**</span><span class="sxs-lookup"><span data-stu-id="ba0bb-130">**Angle Brackets.**</span></span> <span data-ttu-id="ba0bb-131">특성 목록을 제공 하는 경우 꺾쇠 괄호 (" `<` " 및 "")로 묶어야 합니다 `>` .</span><span class="sxs-lookup"><span data-stu-id="ba0bb-131">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="ba0bb-132">**선언의 일부입니다.**</span><span class="sxs-lookup"><span data-stu-id="ba0bb-132">**Part of the Declaration.**</span></span> <span data-ttu-id="ba0bb-133">특성은 별도의 문이 아니라 요소 선언의 일부 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-133">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="ba0bb-134">줄 연속 시퀀스 (" `_` ")를 사용 하 여 선언 문을 여러 소스 코드 줄로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-134">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="ba0bb-135">**수정자.**</span><span class="sxs-lookup"><span data-stu-id="ba0bb-135">**Modifiers.**</span></span> <span data-ttu-id="ba0bb-136">`Assembly` `Module` 소스 파일의 시작 부분에서 프로그래밍 요소에 적용 되는 모든 특성에는 특성 한정자 (또는)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-136">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="ba0bb-137">소스 파일의 시작 부분이 아닌 요소에 적용 된 특성에는 특성 한정자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-137">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="ba0bb-138">**인수의.**</span><span class="sxs-lookup"><span data-stu-id="ba0bb-138">**Arguments.**</span></span> <span data-ttu-id="ba0bb-139">특성의 모든 위치 인수는 모든 변수 또는 속성 이니셜라이저 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-139">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba0bb-140">예제</span><span class="sxs-lookup"><span data-stu-id="ba0bb-140">Example</span></span>  

 <span data-ttu-id="ba0bb-141">다음 예에서는 특성을 <xref:System.Runtime.InteropServices.DllImportAttribute> 프로시저의 기본 정의에 적용 합니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="ba0bb-141">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="ba0bb-142"><xref:System.Runtime.InteropServices.DllImportAttribute> 특성 사용 프로시저가 관리 되지 않는 DLL (동적 연결 라이브러리)의 진입점을 나타내는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-142"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="ba0bb-143">특성은 DLL 이름을 위치 인수로 제공 하 고 다른 정보를 변수 이니셜라이저로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-143">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba0bb-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba0bb-144">See also</span></span>

- [<span data-ttu-id="ba0bb-145">어셈블리</span><span class="sxs-lookup"><span data-stu-id="ba0bb-145">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="ba0bb-146">모듈 \<keyword></span><span class="sxs-lookup"><span data-stu-id="ba0bb-146">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="ba0bb-147">특성 개요</span><span class="sxs-lookup"><span data-stu-id="ba0bb-147">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="ba0bb-148">방법: 코드에서 명령문 분리 및 결합</span><span class="sxs-lookup"><span data-stu-id="ba0bb-148">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
