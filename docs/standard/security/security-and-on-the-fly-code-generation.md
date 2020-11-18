---
title: 보안 및 빠른 코드 생성
description: 더 높은 신뢰 수준에서 실행 되는 더 낮은 신뢰 코드를 대신 하 여 코드를 생성 하는 것은 특히 호출자가 코드 생성에 영향을 줄 수 있는 경우 보안 문제입니다.
ms.date: 07/15/2020
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: c94da31f464a5272dd3f3c9f767a40ba7ad88a47
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824150"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="d1e7c-103">보안 및 빠른 코드 생성</span><span class="sxs-lookup"><span data-stu-id="d1e7c-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="d1e7c-104">일부 라이브러리는 코드를 생성하고 실행하여 호출자에 대한 일부 작업을 수행하는 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="d1e7c-105">기본적인 문제는 낮은 신뢰 수준의 코드를 대신하여 코드를 생성하고 높은 신뢰 수준에서 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="d1e7c-106">호출자가 코드 생성에 영향을 줄 수 있는 경우 문제가 더욱 악화되므로 안전하다고 생각하는 코드만 생성되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="d1e7c-107">항상 어떤 코드를 생성하는지 정확히 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="d1e7c-108">즉, 따옴표로 묶인 문자열(예기치 않은 코드 요소를 포함할 수 없도록 이스케이프해야 함), 식별자(유효한 식별자인지 확인해야 함) 또는 기타 값인지에 관계없이 사용자로부터 얻는 값을 엄격하게 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="d1e7c-109">보안 취약성인 경우는 드물지만 식별자에 이상한 문자가 포함되도록 컴파일된 어셈블리를 수정할 수 있고 이 경우 어셈블리가 손상되기 때문에 식별자는 위험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="d1e7c-110">리플렉션 내보내기를 사용하여 코드를 생성하는 것이 좋으며, 그러면 이러한 많은 문제를 방지하는 데 도움이 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="d1e7c-111">코드를 컴파일하는 경우 악성 프로그램이 코드를 수정할 수 있는 방법이 있는지 여부를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="d1e7c-112">컴파일러가 소스 코드를 읽기 전이나 코드가 .dll 파일을 로드하기 전에 악성 코드가 디스크의 소스 코드를 변경할 수 있는 짧은 기간이 있나요?</span><span class="sxs-lookup"><span data-stu-id="d1e7c-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="d1e7c-113">있다면 파일 시스템에서 액세스 제어 목록을 적절하게 사용하여 이러한 파일을 포함하는 디렉터리를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e7c-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e7c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1e7c-114">See also</span></span>

- [<span data-ttu-id="d1e7c-115">보안 코딩 지침</span><span class="sxs-lookup"><span data-stu-id="d1e7c-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="d1e7c-116">ASP.NET Core 보안</span><span class="sxs-lookup"><span data-stu-id="d1e7c-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
