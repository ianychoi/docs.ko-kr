---
title: 기존 노드 복사
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 651e9fc9dc0d1a50a2d15d382b3ca65f7fd4b7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701434"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="d8bef-102">기존 노드 복사</span><span class="sxs-lookup"><span data-stu-id="d8bef-102">Copy Existing Nodes</span></span>

<span data-ttu-id="d8bef-103">XML DOM(문서 개체 모델)에는 **SelectSingleNode**, **ChildNodes[int i]** , **Attributes[int i]** 등 노드를 선택하는 데 사용할 수 있는 여러 메서드와 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8bef-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="d8bef-104">노드를 선택하면 특정 노드 형식에 작동하는 삽입 메서드 중 하나를 사용하여 트리에 해당 노드를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8bef-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="d8bef-105">트리에 노드를 삽입하는 경우 유일한 제한 사항은 노드가 삽입된 후에도 문서가 제대로 구성되어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d8bef-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="d8bef-106">기존 노드를 DOM 트리에 삽입할 경우 해당 노드가 원래 위치에서 제거된 후에 대상 위치에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8bef-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bef-107">참조</span><span class="sxs-lookup"><span data-stu-id="d8bef-107">See also</span></span>

- [<span data-ttu-id="d8bef-108">XML DOM(문서 개체 모델)</span><span class="sxs-lookup"><span data-stu-id="d8bef-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
