---
description: "BC30202: ' Optional ' 필요에 대해 자세히 알아보세요."
title: "'Optional'이 필요합니다."
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 543dbf6226d4d298d46764ee506b55e770c91604
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795549"
---
# <a name="bc30202-optional-expected"></a><span data-ttu-id="6e28b-103">BC30202: ' Optional '가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e28b-103">BC30202: 'Optional' expected</span></span>

<span data-ttu-id="6e28b-104">프로시저 선언에서 선택적 인수 뒤에는 필수 인수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e28b-104">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="6e28b-105">선택적 인수 다음에 나오는 모든 인수는 선택 사항 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e28b-105">Every argument following an optional argument must also be optional.</span></span>

 <span data-ttu-id="6e28b-106">**오류 ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="6e28b-106">**Error ID:** BC30202</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6e28b-107">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="6e28b-107">To correct this error</span></span>

- <span data-ttu-id="6e28b-108">인수가 필요한 경우 인수 목록의 첫 번째 선택적 인수 앞에 오도록 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e28b-108">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>

- <span data-ttu-id="6e28b-109">인수를 선택적으로 사용 하려면 키워드를 사용 `Optional` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e28b-109">If the argument is intended to be optional, use the `Optional` keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e28b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e28b-110">See also</span></span>

- [<span data-ttu-id="6e28b-111">선택적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6e28b-111">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
