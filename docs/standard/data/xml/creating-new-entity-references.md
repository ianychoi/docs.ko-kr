---
title: 새 엔터티 참조 만들기
ms.date: 03/30/2017
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 5d1411b38ee79705cad3375aea1b95265c1ab61a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829325"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="52d8c-102">새 엔터티 참조 만들기</span><span class="sxs-lookup"><span data-stu-id="52d8c-102">Creating New Entity References</span></span>
<span data-ttu-id="52d8c-103">**CreateEntityReference** 메서드는 새 **XmlEntityReference** 노드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="52d8c-104">XML DOM(문서 개체 모델)에서는 참조될 엔터티 이름이 이미 선언되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="52d8c-105">선언된 경우 **XmlEntityReference** 노드의 자식 노드가 엔터티 선언 노드에서 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="52d8c-106">일치하는 엔터티 선언이 없으면 entityreference 노드의 유일한 자식으로 빈 텍스트 노드가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="52d8c-107">**XmlEntityReference** 노드의 자식 노드는 다른 노드의 복사본이므로 이러한 자식 노드는 읽기 전용이며 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="52d8c-108">노드가 복사될 때 엔터티 참조가 있는 범위에 네임스페이스가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="52d8c-109">이 네임스페이스는 생성되는 모든 요소 또는 특성 노드의 구성에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52d8c-110">DOM에서는 **EntityReference** 노드를 문서에 삽입할 경우에만 **EntityReference** 에 자식 노드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="52d8c-111">새로 생성되는 **EntityReference** 노드에는 자식 노드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="52d8c-112">**XmlDataDocument** 가 **XmlDocument** 의 파생 클래스인 경우에도 **XmlDataDocument** 는 엔터티 참조의 생성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="52d8c-113">이는 **EntityReference** 자식 노드가 읽기 전용이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="52d8c-114">**EntityReference** 노드의 자식 노드는 둘 이상의 영역에 걸쳐 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="52d8c-115">이 경우 **EntityReference** 의 일부를 포함하는 영역과 관련된 행의 일부가 읽기 전용이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52d8c-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d8c-116">참조</span><span class="sxs-lookup"><span data-stu-id="52d8c-116">See also</span></span>

- [<span data-ttu-id="52d8c-117">XML DOM(문서 개체 모델)</span><span class="sxs-lookup"><span data-stu-id="52d8c-117">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
