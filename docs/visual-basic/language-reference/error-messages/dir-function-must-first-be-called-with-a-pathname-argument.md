---
description: "자세한 내용은 다음에 대 한 자세한 정보: Dir ' 함수는 먼저 ' PathName ' 인수를 사용 하 여 호출 해야 합니다."
title: "'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다."
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: ee492a269d41e8c9fe1fddbd59210b59fbe8618c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796589"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="bee14-103">'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bee14-103">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="bee14-104">함수에 대 한 초기 호출에는 `Dir` 인수가 포함 되지 않습니다 `PathName` .</span><span class="sxs-lookup"><span data-stu-id="bee14-104">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="bee14-105">에 대 한 첫 번째 호출에 `Dir` 는를 포함 해야 `PathName` 하지만에 대 한 후속 호출에서는 `Dir` 다음 항목을 검색 하기 위한 매개 변수를 포함할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bee14-105">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bee14-106">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="bee14-106">To correct this error</span></span>

- <span data-ttu-id="bee14-107">`PathName`함수 호출에 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bee14-107">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="bee14-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bee14-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
