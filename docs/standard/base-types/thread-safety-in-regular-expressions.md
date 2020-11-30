---
title: 정규식의 스레드로부터의 안전성
ms.date: 03/30/2017
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: a10b5d01d308af3c808404608e6be1d77e6be8e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734168"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="c6d4c-102">정규식의 스레드로부터의 안전성</span><span class="sxs-lookup"><span data-stu-id="c6d4c-102">Thread Safety in Regular Expressions</span></span>

<span data-ttu-id="c6d4c-103"><xref:System.Text.RegularExpressions.Regex> 클래스 자체는 스레드로부터 안전하고 변경할 수 없습니다(읽기 전용).</span><span class="sxs-lookup"><span data-stu-id="c6d4c-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="c6d4c-104">즉, 모든 스레드에서 **Regex** 개체를 만들어 스레드 간에 공유할 수 있습니다. 일치하는 메서드는 모든 스레드에서 호출할 수 있고 전역 상태를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="c6d4c-105">그러나 **Regex** 에서 반환한 결과 개체(**Match** 및 **MatchCollection**)는 단일 스레드에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="c6d4c-106">이런 개체의 대부분은 논리적으로 변경되지 않지만 이를 구현하면 성능을 향상시키는 몇 가지 결과의 계산이 지연될 수 있고 결과적으로 호출자는 해당 개체에 대한 액세스를 직렬화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="c6d4c-107">여러 스레드에서 **Regex** 결과 개체를 공유할 수 없는 경우 이러한 개체는 동기화된 메서드를 호출하여 스레드로부터 안전한 인스턴스로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="c6d4c-108">열거자를 제외한 모든 정규식 클래스는 스레드로부터 안전하거나 동기화된 메서드에서 스레드로부터 안전한 개체로 변환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="c6d4c-109">열거자만이 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-109">Enumerators are the only exception.</span></span> <span data-ttu-id="c6d4c-110">애플리케이션은 컬렉션 열거자에 대한 호출을 직렬화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="c6d4c-111">규칙은 다음과 같습니다. 컬렉션을 둘 이상의 스레드에서 동시에 열거할 수 있는 경우 열거자에서 트래버스하는 컬렉션의 루트 개체에 대한 열거자 메서드 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d4c-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d4c-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6d4c-112">See also</span></span>

- [<span data-ttu-id="c6d4c-113">.NET 정규식</span><span class="sxs-lookup"><span data-stu-id="c6d4c-113">.NET Regular Expressions</span></span>](regular-expressions.md)
