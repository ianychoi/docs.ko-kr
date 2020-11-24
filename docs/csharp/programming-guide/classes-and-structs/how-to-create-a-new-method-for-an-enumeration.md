---
title: 새 열거형 메서드를 만드는 방법 - C# 프로그래밍 가이드
description: 확장 메서드를 사용하여 C#의 열거형에 기능을 추가하는 방법에 대해 알아봅니다. 이 예제에서는 성적이라는 열거형에 Passing이라는 확장 메서드를 보여줍니다.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 862eb86a5b0cc6b95302260874222bbc09d98132
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099414"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="b8a0c-104">새 열거형 메서드를 만드는 방법(C# 프로그래밍 가이드)</span><span class="sxs-lookup"><span data-stu-id="b8a0c-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>

<span data-ttu-id="b8a0c-105">확장 메서드를 사용하여 특정 열거형 형식과 관련된 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a0c-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8a0c-106">예제</span><span class="sxs-lookup"><span data-stu-id="b8a0c-106">Example</span></span>  

 <span data-ttu-id="b8a0c-107">다음 예제에서 `Grades` 열거형은 학생이 클래스에서 받을 수 있는 문자 성적을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8a0c-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="b8a0c-108">해당 형식의 각 인스턴스가 이제 합격 성적을 나타내는지 여부를 "알 수 있도록" `Passing`이라는 확장 메서드가 `Grades` 형식에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a0c-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="b8a0c-109">또한 `Extensions` 클래스에는 동적으로 업데이트되는 정적 변수가 포함되며, 확장 메서드의 반환 값이 해당 변수의 현재 값을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a0c-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="b8a0c-110">이는 확장 메서드가 정의된 정적 클래스에서 내부적으로 직접 호출됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8a0c-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8a0c-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8a0c-111">See also</span></span>

- [<span data-ttu-id="b8a0c-112">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="b8a0c-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b8a0c-113">확장명 메서드</span><span class="sxs-lookup"><span data-stu-id="b8a0c-113">Extension Methods</span></span>](./extension-methods.md)
