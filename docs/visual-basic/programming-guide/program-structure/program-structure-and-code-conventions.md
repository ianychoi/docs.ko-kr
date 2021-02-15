---
description: '자세한 정보: 프로그램 구조 및 코드 규칙 (Visual Basic)'
title: 프로그램 구조 및 코드 규칙
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: 7d4202ead0550cf54a80eac89c4a4274a22d0315
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468488"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="534bd-103">프로그램 구조 및 코드 규칙(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="534bd-103">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="534bd-104">이 섹션에서는 일반적인 Visual Basic 프로그램 구조를 소개 하 고, 간단한 Visual Basic 프로그램인 "Hello, 세계"를 제공 하 고 Visual Basic 코드 규칙을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-104">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="534bd-105">코드 규칙은 프로그램의 논리에 초점을 맞춘 것이 아니라 물리적 구조와 모양에 초점을 맞춘 제안입니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-105">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="534bd-106">이를 통해 코드를 더 쉽게 읽고 이해 하 고 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-106">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="534bd-107">코드 규칙에는 다른 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-107">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="534bd-108">레이블 및 주석 달기 코드의 표준화 된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-108">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="534bd-109">코드의 간격, 형식 지정 및 들여쓰기에 대 한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-109">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="534bd-110">개체, 변수 및 프로시저에 대 한 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="534bd-110">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="534bd-111">다음 항목에서는 Visual Basic 프로그램에 대 한 프로그래밍 지침 집합과 함께 좋은 사용 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-111">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="534bd-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="534bd-112">In This Section</span></span>  

 [<span data-ttu-id="534bd-113">Visual Basic 프로그램의 구조</span><span class="sxs-lookup"><span data-stu-id="534bd-113">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="534bd-114">Visual Basic 프로그램을 구성 하는 요소에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-114">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="534bd-115">Visual Basic의 Main 프로시저</span><span class="sxs-lookup"><span data-stu-id="534bd-115">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="534bd-116">응용 프로그램에 대 한 시작 지점 및 전반적인 제어 역할을 하는 절차를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-116">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="534bd-117">참조 및 Imports 문</span><span class="sxs-lookup"><span data-stu-id="534bd-117">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="534bd-118">다른 어셈블리의 개체를 참조 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-118">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="534bd-119">Visual Basic의 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="534bd-119">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="534bd-120">네임 스페이스가 어셈블리 내에서 개체를 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-120">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="534bd-121">Visual Basic 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="534bd-121">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="534bd-122">프로시저, 상수, 변수, 인수 및 개체 명명에 대 한 일반 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-122">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="534bd-123">Visual Basic 코딩 규칙</span><span class="sxs-lookup"><span data-stu-id="534bd-123">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="534bd-124">이 설명서의 샘플을 개발 하는 데 사용 되는 지침을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-124">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="534bd-125">조건부 컴파일</span><span class="sxs-lookup"><span data-stu-id="534bd-125">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="534bd-126">특정 코드 블록을 선택적으로 컴파일하는 동시에 다른 사용자를 무시 하도록 컴파일러에 지시 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-126">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="534bd-127">방법: 코드에서 명령문 분리 및 결합</span><span class="sxs-lookup"><span data-stu-id="534bd-127">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="534bd-128">Long 문을 여러 줄로 나누고 짧은 문을 한 줄에 결합 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-128">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="534bd-129">방법: 코드 섹션 축소 및 숨기기</span><span class="sxs-lookup"><span data-stu-id="534bd-129">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="534bd-130">Visual Basic 코드 편집기에서 코드 섹션을 축소 하 고 숨기는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-130">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="534bd-131">방법: Label 문</span><span class="sxs-lookup"><span data-stu-id="534bd-131">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="534bd-132">와 같은 문에서 사용할 수 있도록 코드 줄을 표시 하는 방법을 보여 줍니다 `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="534bd-132">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="534bd-133">코드의 특수 문자</span><span class="sxs-lookup"><span data-stu-id="534bd-133">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="534bd-134">숫자가 아닌 문자 및 영문자가 아닌 문자를 사용 하는 방법과 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-134">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="534bd-135">코드 주석</span><span class="sxs-lookup"><span data-stu-id="534bd-135">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="534bd-136">코드에 설명 주석을 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-136">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="534bd-137">코드에서 요소 이름으로 사용되는 키워드</span><span class="sxs-lookup"><span data-stu-id="534bd-137">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="534bd-138">대괄호 ()를 사용 하 여 `[]` 키워드를 Visual Basic 변수 이름을 구분 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-138">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="534bd-139">Me, My, MyBase 및 MyClass</span><span class="sxs-lookup"><span data-stu-id="534bd-139">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="534bd-140">Visual Basic 프로그램의 요소를 참조 하는 다양 한 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-140">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="534bd-141">Visual Basic 제한 사항</span><span class="sxs-lookup"><span data-stu-id="534bd-141">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="534bd-142">Visual Basic 내에서 알려진 코딩 제한을 제거 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-142">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="534bd-143">관련 단원</span><span class="sxs-lookup"><span data-stu-id="534bd-143">Related Sections</span></span>  

 [<span data-ttu-id="534bd-144">글꼴 표시 및 코드 규칙</span><span class="sxs-lookup"><span data-stu-id="534bd-144">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="534bd-145">Visual Basic에 대 한 표준 코딩 규칙을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-145">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="534bd-146">코드 작성</span><span class="sxs-lookup"><span data-stu-id="534bd-146">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="534bd-147">코드를 더 쉽게 작성 및 관리할 수 있도록 하는 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="534bd-147">Describes features that make it easier for you to write and manage your code.</span></span>
