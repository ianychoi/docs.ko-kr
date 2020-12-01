---
title: '방법: WebRequest를 사용하여 사용자 지정 프로토콜 등록'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 86ad862dbff9f4a982eec27a6806bcbb6c16f3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255808"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="24f57-102">방법: WebRequest를 사용하여 사용자 지정 프로토콜 등록</span><span class="sxs-lookup"><span data-stu-id="24f57-102">How to: Register a Custom Protocol Using WebRequest</span></span>

<span data-ttu-id="24f57-103">이 예제에서는 다른 곳에서 정의된 프로토콜별 클래스를 등록하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="24f57-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="24f57-104">이 예제에서 `CustomWebRequestCreator`는 `CustomWebRequest` 개체를 반환하는 **Create** 메서드를 구현하는 사용자가 구현한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="24f57-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="24f57-105">코드 예제에서는 사용자 지정 프로토콜을 구현하는 `CustomWebRequest` 코드를 작성했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="24f57-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f57-106">예제</span><span class="sxs-lookup"><span data-stu-id="24f57-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24f57-107">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="24f57-107">Compiling the Code</span></span>  

 <span data-ttu-id="24f57-108">이 예제에는 다음 사항이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24f57-108">This example requires:</span></span>  
  
 <span data-ttu-id="24f57-109"><xref:System.Net> 네임스페이스에 대한 참조.</span><span class="sxs-lookup"><span data-stu-id="24f57-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f57-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24f57-110">See also</span></span>

- [<span data-ttu-id="24f57-111">플러그형 프로토콜 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="24f57-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
