---
title: '방법: 파이프라인에서 차단 컬렉션 배열 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 55dc3e9934efa153c61322f63b7dde8077442fd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733466"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="162aa-102">방법: 파이프라인에서 차단 컬렉션 배열 사용</span><span class="sxs-lookup"><span data-stu-id="162aa-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>

<span data-ttu-id="162aa-103">다음 예제에서는 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> 및 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A>와 같은 정적 메서드와 함께 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 개체의 배열을 사용하여 구성 요소 간에 빠르고 유연한 데이터 전송을 구현하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="162aa-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="162aa-104">예제</span><span class="sxs-lookup"><span data-stu-id="162aa-104">Example</span></span>  

 <span data-ttu-id="162aa-105">다음 예제에서는 각 개체에서 동시에 입력 컬렉션으로부터 데이터를 가져와 변환하고 출력 컬렉션에 전달하는 기본 파이프라인 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="162aa-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="162aa-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="162aa-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="162aa-107">스레드로부터 안전한 컬렉션</span><span class="sxs-lookup"><span data-stu-id="162aa-107">Thread-Safe Collections</span></span>](index.md)
