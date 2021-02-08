---
description: BC36647 및 BC36644에 대 한 자세한 정보:이 인수에서 형식 매개 변수의 데이터 형식을 유추할 수 없습니다.
title: 이 인수에서 형식 매개 변수의 데이터 형식을 유추할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 8689a0b95ed11a2eee5814e0171ae8ecd8b206b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796693"
---
# <a name="bc36647-and-bc36644-data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="ad2bb-103">BC36647 및 BC36644:이 인수에서 형식 매개 변수의 데이터 형식을 유추할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-103">BC36647 and BC36644: Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="ad2bb-104">이 인수에서 형식 매개 변수의 데이터 형식을 유추할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-104">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="ad2bb-105">데이터 형식을 명시적으로 지정하면 이 오류를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-105">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="ad2bb-106">이 오류는 오버로드 확인에 실패한 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-106">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="ad2bb-107">특정 오버로드 후보가 제거된 이유를 나타내는 하위 메시지로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-107">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="ad2bb-108">오류 메시지는 컴파일러에서 형식 유추를 사용 하 여 형식 매개 변수에 대 한 데이터 형식을 찾을 수 없음을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-108">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="ad2bb-109">인수 지정이 옵션이 아닌 경우(예: 쿼리 식의 쿼리 연산자) 두 번째 문장 없이 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-109">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="ad2bb-110">다음 코드에서는 오류를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-110">The following code demonstrates the error.</span></span>

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

<span data-ttu-id="ad2bb-111">**오류 ID:** BC36647 및 BC36644</span><span class="sxs-lookup"><span data-stu-id="ad2bb-111">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ad2bb-112">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="ad2bb-112">To correct this error</span></span>

<span data-ttu-id="ad2bb-113">형식 유추를 사용하지 않고 형식 매개 변수에 대한 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-113">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad2bb-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad2bb-114">See also</span></span>

- [<span data-ttu-id="ad2bb-115">완화된 대리자 변환</span><span class="sxs-lookup"><span data-stu-id="ad2bb-115">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="ad2bb-116">Visual Basic의 제네릭 프로시저</span><span class="sxs-lookup"><span data-stu-id="ad2bb-116">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="ad2bb-117">Visual Basic의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="ad2bb-117">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
