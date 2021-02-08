---
description: 자세한 내용은 다음에 대해 자세히 알아보세요. BC40035:은 (는 <proceduresignature1> ) 배열 <proceduresignature2> 매개 변수 형식의 배열 또는 배열 매개 변수 형식의 차수만 다른 오버 로드로 인해 CLS 규격이 아닙니다.
title: <proceduresignature1>는 배열 매개 변수 형식의 배열만 다르거나 배열 매개 변수 형식의 차수만 다른 <proceduresignature2>를 오버로드하므로 CLS 규격이 아닙니다.
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 056683033a4eacdc6ad783f5056b639e849e3507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795393"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="0be79-103">BC40035: \<proceduresignature1> 는 배열 \<proceduresignature2> 매개 변수 형식의 배열 또는 배열 매개 변수 형식의 차수만 다른 오버 로드 이므로 CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-103">BC40035: \<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="0be79-104">프로시저 또는 속성은 `<CLSCompliant(True)>` 다른 프로시저 또는 속성을 재정의 하는 경우로 표시 되 고, 매개 변수 목록 간의 유일한 차이점은 가변 배열의 중첩 수준 또는 배열의 차수입니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-104">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>

 <span data-ttu-id="0be79-105">다음 선언에서 두 번째와 세 번째 선언은이 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-105">In the following declarations, the second and third declarations generate this error:</span></span>

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 <span data-ttu-id="0be79-106">두 번째 선언은 원래 1 차원 매개 변수를 `arrayParam` 배열의 배열로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-106">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="0be79-107">세 번째 선언은 `arrayParam` 2 차원 배열 (rank 2)로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-107">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="0be79-108">Visual Basic 오버 로드는 이러한 변경 내용 중 하나에 의해서만 달라질 수 있지만 이러한 오버 로드는 [언어 독립성 및 Language-Independent 구성 요소](../../../standard/language-independence-and-language-independent-components.md) (CLS)와 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-108">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>

 <span data-ttu-id="0be79-109"><xref:System.CLSCompliantAttribute> 를 프로그래밍 요소에 적용하는 경우 특성의 `isCompliant` 매개 변수를 `True` 또는 `False` 로 설정하여 준수 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-109">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0be79-110">이 매개 변수에는 기본값이 없으며 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-110">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="0be79-111">요소에 <xref:System.CLSCompliantAttribute> 를 적용하지 않으면 비규격인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-111">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="0be79-112">이 메시지는 기본적으로 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-112">By default, this message is a warning.</span></span> <span data-ttu-id="0be79-113">경고를 숨기거나 오류로 처리하는 방법에 대한 자세한 내용은 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0be79-113">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="0be79-114">**오류 ID:** BC40035</span><span class="sxs-lookup"><span data-stu-id="0be79-114">**Error ID:** BC40035</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0be79-115">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="0be79-115">To correct this error</span></span>

- <span data-ttu-id="0be79-116">CLS 규격이 필요한 경우이 도움말 페이지에 언급 된 변경 내용 보다 더 다양 한 방식으로 서로 다른 오버 로드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0be79-116">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="0be79-117">이 도움말 페이지에 언급 된 변경 사항만 다른 오버 로드를 수행 해야 하는 경우 해당 <xref:System.CLSCompliantAttribute> 정의에서를 제거 하거나로 표시 합니다 `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="0be79-117">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0be79-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0be79-118">See also</span></span>

- [<span data-ttu-id="0be79-119">프로시저 오버로딩</span><span class="sxs-lookup"><span data-stu-id="0be79-119">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="0be79-120">오버로드</span><span class="sxs-lookup"><span data-stu-id="0be79-120">Overloads</span></span>](../modifiers/overloads.md)
