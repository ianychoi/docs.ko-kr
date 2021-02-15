---
description: '자세한 정보: XML 파일 처리 (Visual Basic)'
title: XML 파일 처리
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468397"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="c71d9-103">XML 파일 처리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c71d9-103">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="c71d9-104">컴파일러는 문서 생성을 위해 태그가 지정되는 코드의 각 구문에 대해 ID 문자열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-104">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="c71d9-105">코드에 태그를 설정 하는 방법에 대 한 자세한 내용은 [XML 주석 태그](../../language-reference/xmldoc/index.md)를 참조 하세요. ID 문자열은 구문을 고유 하 게 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-105">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="c71d9-106">XML 파일을 처리 하는 프로그램은 ID 문자열을 사용 하 여 해당 하는 .NET Framework metadata/reflection 항목을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-106">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="c71d9-107">XML 파일은 코드의 계층적 표현이 아닙니다. 각 요소에 대해 생성 된 ID가 있는 단순 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-107">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="c71d9-108">컴파일러는 ID 문자열을 생성할 때 다음 규칙을 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-108">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="c71d9-109">문자열에 공백이 배치되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-109">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="c71d9-110">ID 문자열의 첫 부분이 뒤에 콜론이 붙은 한 글자로 식별 대상 멤버를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-110">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="c71d9-111">다음 멤버 유형이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-111">The following member types are used.</span></span>  
  
|<span data-ttu-id="c71d9-112">문자</span><span class="sxs-lookup"><span data-stu-id="c71d9-112">Character</span></span>|<span data-ttu-id="c71d9-113">설명</span><span class="sxs-lookup"><span data-stu-id="c71d9-113">Description</span></span>|  
|---|---|  
|<span data-ttu-id="c71d9-114">N</span><span class="sxs-lookup"><span data-stu-id="c71d9-114">N</span></span>|<span data-ttu-id="c71d9-115">namespace</span><span class="sxs-lookup"><span data-stu-id="c71d9-115">namespace</span></span><br /><br /> <span data-ttu-id="c71d9-116">네임 스페이스에 문서 주석을 추가할 수는 없지만 지원 되는 경우에는이에 대 한 CREF 참조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-116">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="c71d9-117">T</span><span class="sxs-lookup"><span data-stu-id="c71d9-117">T</span></span>|<span data-ttu-id="c71d9-118">형식: `Class` , `Module` , `Interface` , `Structure` , `Enum` , `Delegate`</span><span class="sxs-lookup"><span data-stu-id="c71d9-118">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="c71d9-119">F</span><span class="sxs-lookup"><span data-stu-id="c71d9-119">F</span></span>|<span data-ttu-id="c71d9-120">필드가 `Dim`</span><span class="sxs-lookup"><span data-stu-id="c71d9-120">field: `Dim`</span></span>|  
|<span data-ttu-id="c71d9-121">P</span><span class="sxs-lookup"><span data-stu-id="c71d9-121">P</span></span>|<span data-ttu-id="c71d9-122">속성: `Property` (기본 속성 포함)</span><span class="sxs-lookup"><span data-stu-id="c71d9-122">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="c71d9-123">M</span><span class="sxs-lookup"><span data-stu-id="c71d9-123">M</span></span>|<span data-ttu-id="c71d9-124">메서드: `Sub` , `Function` , `Declare` , `Operator`</span><span class="sxs-lookup"><span data-stu-id="c71d9-124">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="c71d9-125">E</span><span class="sxs-lookup"><span data-stu-id="c71d9-125">E</span></span>|<span data-ttu-id="c71d9-126">이벤트 `Event`</span><span class="sxs-lookup"><span data-stu-id="c71d9-126">event: `Event`</span></span>|  
|<span data-ttu-id="c71d9-127">!</span><span class="sxs-lookup"><span data-stu-id="c71d9-127">!</span></span>|<span data-ttu-id="c71d9-128">오류 문자열</span><span class="sxs-lookup"><span data-stu-id="c71d9-128">error string</span></span><br /><br /> <span data-ttu-id="c71d9-129">문자열의 나머지 부분은 오류에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-129">The rest of the string provides information about the error.</span></span> <span data-ttu-id="c71d9-130">Visual Basic 컴파일러는 확인할 수 없는 링크에 대 한 오류 정보를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-130">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="c71d9-131">의 두 번째 부분은 `String` 네임 스페이스의 루트에서 시작 하는 항목의 정규화 된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-131">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="c71d9-132">항목의 이름, 바깥쪽 형식 및 네임 스페이스는 마침표로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-132">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="c71d9-133">항목 자체의 이름에 마침표가 포함 되어 있으면 숫자 기호 (#)로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-133">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="c71d9-134">이름에 직접 번호 기호가 있는 항목이 없는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-134">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="c71d9-135">예를 들어 생성자의 정규화 된 이름은 `String` `System.String.#ctor` 입니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-135">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="c71d9-136">속성 및 메서드의 경우 메서드에 대한 인수가 있으면 괄호로 묶인 인수 목록이 문자열 뒤에 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-136">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="c71d9-137">인수가 없으면 괄호도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-137">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="c71d9-138">인수는 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-138">The arguments are separated by commas.</span></span> <span data-ttu-id="c71d9-139">각 인수의 인코딩은 .NET Framework 시그니처에서 인코딩 되는 방식을 직접 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-139">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71d9-140">예</span><span class="sxs-lookup"><span data-stu-id="c71d9-140">Example</span></span>  

 <span data-ttu-id="c71d9-141">다음 코드에서는 클래스 및 해당 멤버에 대 한 ID 문자열이 생성 되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c71d9-141">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="c71d9-142">추가 정보</span><span class="sxs-lookup"><span data-stu-id="c71d9-142">See also</span></span>

- [<span data-ttu-id="c71d9-143">-doc</span><span class="sxs-lookup"><span data-stu-id="c71d9-143">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="c71d9-144">방법: XML 설명서 만들기</span><span class="sxs-lookup"><span data-stu-id="c71d9-144">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
