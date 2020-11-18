---
title: 예외 디자인 지침
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: 776e559bb1629245c275cb4463531a8dd4b230ae
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821153"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="1452d-102">예외 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="1452d-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="1452d-103">예외 처리는 반환 값 기반 오류 보고 보다 많은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1452d-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="1452d-104">바람직한 프레임 워크 디자인은 응용 프로그램 개발자가 예외의 이점을 실현할 수 있도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="1452d-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="1452d-105">이 섹션에서는 예외의 이점에 대해 설명 하 고이를 효과적으로 사용 하기 위한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1452d-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1452d-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1452d-106">In This Section</span></span>  
 [<span data-ttu-id="1452d-107">예외 Throw</span><span class="sxs-lookup"><span data-stu-id="1452d-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="1452d-108">표준 예외 형식 사용</span><span class="sxs-lookup"><span data-stu-id="1452d-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="1452d-109">예외 및 성능</span><span class="sxs-lookup"><span data-stu-id="1452d-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="1452d-110">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1452d-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1452d-111">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="1452d-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1452d-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1452d-112">See also</span></span>

- [<span data-ttu-id="1452d-113">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="1452d-113">Framework Design Guidelines</span></span>](index.md)
