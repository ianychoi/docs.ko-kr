---
description: "B C 42104: ' ' 변수를 <variablename> 사용 하 여 값이 할당 되기 전에 자세히 알아보세요."
title: 값이 할당되기 전에 '<variablename>' 변수를 사용했습니다.
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701497"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="aeaca-103">B C 42104: 값이 \<variablename> 할당 되기 전에 ' ' 변수를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-103">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="aeaca-104">값이 \<variablename> 할당 되기 전에 ' ' 변수를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-104">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="aeaca-105">런타임에 null 참조 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-105">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="aeaca-106">응용 프로그램에는 값이 할당 되기 전에 변수를 읽는 코드를 통해 하나 이상의 가능한 경로가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-106">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="aeaca-107">변수에 값이 할당되지 않으면 해당 데이터 형식에 대한 기본값을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-107">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="aeaca-108">참조 데이터 형식의 경우 해당 기본값은 [Nothing](../nothing.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-108">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="aeaca-109">값이 `Nothing` 인 참조 변수를 읽으면 일부 환경에서 <xref:System.NullReferenceException> 이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-109">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="aeaca-110">이 메시지는 기본적으로 경고입니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-110">By default, this message is a warning.</span></span> <span data-ttu-id="aeaca-111">경고를 숨기거나 오류로 처리하는 방법에 대한 자세한 내용은 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aeaca-111">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="aeaca-112">**오류 ID:** B C 42104</span><span class="sxs-lookup"><span data-stu-id="aeaca-112">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="aeaca-113">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="aeaca-113">To correct this error</span></span>

- <span data-ttu-id="aeaca-114">제어 흐름 논리를 확인 하 고 변수가이를 읽는 문으로 제어가 전달 되기 전에 유효한 값을 포함 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-114">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="aeaca-115">변수를 항상 유효한 값으로 보장 하는 한 가지 방법은 선언의 일부로 초기화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aeaca-115">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="aeaca-116">[Dim 문에서](../statements/dim-statement.md)"초기화"를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aeaca-116">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aeaca-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aeaca-117">See also</span></span>

- [<span data-ttu-id="aeaca-118">Dim 문</span><span class="sxs-lookup"><span data-stu-id="aeaca-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="aeaca-119">변수 선언</span><span class="sxs-lookup"><span data-stu-id="aeaca-119">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="aeaca-120">변수 문제 해결</span><span class="sxs-lookup"><span data-stu-id="aeaca-120">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
