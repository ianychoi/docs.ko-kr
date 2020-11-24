---
title: '방법: 사용자 정의 예외 만들기'
description: .NET의 Exception 기본 클래스에서 파생된 예외 클래스의 계층 구조의 대안인 사용자 정의 예외를 만드는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: b0a8549c9bacf322a0685c7b505185ab1d1101f6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828129"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="c3c81-103">사용자 정의 예외를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="c3c81-103">How to create user-defined exceptions</span></span>

<span data-ttu-id="c3c81-104">.NET에서는 기본 클래스 <xref:System.Exception>에서 최종적으로 파생되는 예외 클래스의 계층 구조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-104">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="c3c81-105">그러나 사용자 요구를 충족하는 미리 정의된 예외가 없는 경우 <xref:System.Exception> 클래스에서 파생하여 사용자 고유의 예외 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-105">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="c3c81-106">사용자 고유의 예외를 만드는 경우 다음 예제와 같이 사용자 정의 예외의 클래스 이름을 "Exception" 단어로 끝내고 세 가지 공통 생성자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-106">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="c3c81-107">예제에서는 `EmployeeListNotFoundException`이라는 새 예외 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-107">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="c3c81-108">클래스는 <xref:System.Exception>에서 파생되며 세 가지 생성자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-108">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="c3c81-109">원격을 사용하는 경우 사용자 정의 예외에 대한 메타데이터를 서버(호출 수신자) 및 클라이언트(프록시 개체 또는 호출자)에서 사용할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3c81-109">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="c3c81-110">자세한 내용은 [예외에 대한 모범 사례](best-practices-for-exceptions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3c81-110">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3c81-111">참조</span><span class="sxs-lookup"><span data-stu-id="c3c81-111">See also</span></span>

- [<span data-ttu-id="c3c81-112">예외</span><span class="sxs-lookup"><span data-stu-id="c3c81-112">Exceptions</span></span>](index.md)
