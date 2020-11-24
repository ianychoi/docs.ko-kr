---
title: 특성 적용
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 83cfb1d5b5aa3ebc8651406850a758146fd329d4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829104"
---
# <a name="apply-attributes"></a><span data-ttu-id="2e473-102">특성 적용</span><span class="sxs-lookup"><span data-stu-id="2e473-102">Apply attributes</span></span>

<span data-ttu-id="2e473-103">다음 프로세스를 사용하여 코드 요소에 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-103">Use the following process to apply an attribute to an element of your code.</span></span>

1. <span data-ttu-id="2e473-104">새 특성을 정의하거나 기존 .NET 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-104">Define a new attribute or use an existing .NET attribute.</span></span>

2. <span data-ttu-id="2e473-105">코드 요소 바로 앞에 특성을 배치하여 이 요소에 해당 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>

     <span data-ttu-id="2e473-106">각 언어마다 고유한 특성 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="2e473-107">C++ 및 C#의 경우 특성은 대괄호로 묶고, 공백으로 요소와 구분되며, 줄 바꿈 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="2e473-108">Visual Basic의 경우 특성은 꺾쇠 괄호로 묶고, 같은 논리 줄에 있어야 합니다. 줄 바꿈이 필요하면 줄 연속 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>

3. <span data-ttu-id="2e473-109">특성에 대한 위치 매개 변수와 명명된 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-109">Specify positional parameters and named parameters for the attribute.</span></span>

     <span data-ttu-id="2e473-110">*위치* 매개 변수는 필수 요소로서 명명된 매개 변수 앞에 와야 하며, 특성의 생성자 중 하나의 매개 변수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-110">*Positional* parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="2e473-111">*명명된* 매개 변수는 선택적 요소이며, 특성의 읽기/쓰기 속성에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-111">*Named* parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="2e473-112">C++ 및 C#의 경우 각 선택적 매개 변수에 `name=value`를 지정합니다. 여기서 `name`은 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-112">In C++, and C#, specify `name=value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="2e473-113">Visual Basic의 경우 `name:=value`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-113">In Visual Basic, specify `name:=value`.</span></span>

 <span data-ttu-id="2e473-114">특성은 코드를 컴파일할 때 메타데이터로 내보내지며, 공용 언어 런타임과 사용자 지정 도구 또는 애플리케이션에서 런타임 리플렉션 서비스를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>

 <span data-ttu-id="2e473-115">모든 특성 이름은 규칙에 따라 "Attribute"로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-115">By convention, all attribute names end with "Attribute".</span></span> <span data-ttu-id="2e473-116">하지만 런타임을 목적으로 하는 일부 언어(예: Visual Basic 및 C#)에서는 특성의 전체 이름을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="2e473-117">예를 들어 <xref:System.ObsoleteAttribute?displayProperty=nameWithType>를 초기화하려는 경우 **Obsolete** 로만 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>

## <a name="apply-an-attribute-to-a-method"></a><span data-ttu-id="2e473-118">메서드에 특성 적용</span><span class="sxs-lookup"><span data-stu-id="2e473-118">Apply an attribute to a method</span></span>

 <span data-ttu-id="2e473-119">다음 코드 예제에서는 코드를 오래된 것으로 표시하는 **System.ObsoleteAttribute** 를 사용하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-119">The following code example shows how to use **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="2e473-120">`"Will be removed in next version"` 문자열이 특성에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="2e473-121">이 특성이 설명하는 코드가 호출되면 이 특성으로 인해 전달된 문자열을 표시하는 컴파일러 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a><span data-ttu-id="2e473-122">어셈블리 수준에서 특성 적용</span><span class="sxs-lookup"><span data-stu-id="2e473-122">Apply attributes at the assembly level</span></span>

 <span data-ttu-id="2e473-123">어셈블리 수준에서 특성을 적용하려면 `assembly`(Visual Basic에서는 `Assembly`) 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-123">If you want to apply an attribute at the assembly level, use the `assembly` (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="2e473-124">다음 코드에서는 어셈블리 수준에서 적용된 **AssemblyTitleAttribute** 를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 <span data-ttu-id="2e473-125">이 특성을 적용하면 `"My Assembly"` 문자열이 해당 파일의 메타데이터 부분에 있는 어셈블리 매니페스트에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="2e473-126">[Ildasm.exe(MSIL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md)를 사용하거나 특성을 검색하는 사용자 지정 프로그램을 만들어 이 특성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e473-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e473-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e473-127">See also</span></span>

- [<span data-ttu-id="2e473-128">특성</span><span class="sxs-lookup"><span data-stu-id="2e473-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="2e473-129">특성에 저장된 정보 검색</span><span class="sxs-lookup"><span data-stu-id="2e473-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="2e473-130">개념</span><span class="sxs-lookup"><span data-stu-id="2e473-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="2e473-131">특성(C#)</span><span class="sxs-lookup"><span data-stu-id="2e473-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="2e473-132">특성 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e473-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
