---
description: '엔터티 데이터 모델: 네임 스페이스에 대 한 자세한 정보'
title: '엔터티 데이터 모델: 네임스페이스'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: c18178672ebab0e323c9712af2668c3cb92e0300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672766"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="a0771-103">엔터티 데이터 모델: 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="a0771-103">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="a0771-104">EDM (엔터티 데이터 모델)의 네임 스페이스는 [엔터티 형식](entity-type.md), [복합 형식](complex-type.md)및 [연결](association-type.md)에 대 한 추상 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-104">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="a0771-105">EDM의 네임스페이스는 프로그래밍 언어의 네임스페이스와 유사하며, 포함하는 개체에 대한 컨텍스트를 제공하고 이름은 같지만 다른 네임스페이스에 포함된 개체를 구분하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-105">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0771-106">예제</span><span class="sxs-lookup"><span data-stu-id="a0771-106">Example</span></span>  

 <span data-ttu-id="a0771-107">[ADO.NET Entity Framework](./ef/index.md) 에서는[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(개념 스키마 정의 언어) 이라는 DSL (도메인별 언어)을 사용 하 여 개념적 모델을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-107">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="a0771-108">다음 CSDL 코드에서는 네임스페이스를 사용하여 다른 개념적 모델에서 정의된 형식을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-108">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="a0771-109">다음 예제에서는 `Publisher` 네임스페이스에서 가져온 복합 형식 속성(`Address`)이 있는 엔터티 형식(`ExtendedBooksModel`)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-109">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="a0771-110">`Using` 요소는 네임스페이스를 가져왔음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-110">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="a0771-111">`Address` 속성의 형식은 정규화된 이름(`ExtendedBooksModel.Address`)을 사용하여 정의되며, 이 형식이 `ExtendedBooksModel` 네임스페이스에 정의되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0771-111">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="a0771-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0771-112">See also</span></span>

- [<span data-ttu-id="a0771-113">엔터티 데이터 모델의 주요 개념</span><span class="sxs-lookup"><span data-stu-id="a0771-113">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="a0771-114">엔터티 데이터 모델</span><span class="sxs-lookup"><span data-stu-id="a0771-114">Entity Data Model</span></span>](entity-data-model.md)
