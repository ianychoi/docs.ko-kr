---
description: '자세한 정보: 클래스 정의 인스턴스가 아닌 개체에서 friend 함수를 호출할 수 없습니다.'
title: 클래스 정의 인스턴스가 아닌 개체에서 friend 함수를 호출할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: 612a169cf976881b82cb0bb0c44ac6c6e7f91755
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478700"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="a9178-103">클래스 정의 인스턴스가 아닌 개체에서 friend 함수를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9178-103">Cannot call friend function on object which is not an instance of defining class</span></span>

<span data-ttu-id="a9178-104">크로스 프로세스 또는 크로스 스레드로 클래스의 `Friend` 프로시저를 호출하려고 했거나 `Friend` 속성 또는 메서드에 액세스하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a9178-104">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="a9178-105">`Friend` 프로시저는 클래스 외부에 있지만 클래스가 정의되는 프로젝트의 일부인 모듈에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9178-105">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a9178-106">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="a9178-106">To correct this error</span></span>  
  
- <span data-ttu-id="a9178-107">클래스가 정의되는 프로젝트의 일부인 모듈에서 프로시저를 호출하거나 액세스하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9178-107">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9178-108">추가 정보</span><span class="sxs-lookup"><span data-stu-id="a9178-108">See also</span></span>

- [<span data-ttu-id="a9178-109">Friend</span><span class="sxs-lookup"><span data-stu-id="a9178-109">Friend</span></span>](../language-reference/modifiers/friend.md)
