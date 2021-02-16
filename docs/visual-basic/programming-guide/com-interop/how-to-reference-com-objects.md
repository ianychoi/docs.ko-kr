---
description: '자세한 정보: 방법: Visual Basic에서 COM 개체 참조'
title: '방법: Visual Basic에서 COM 개체 참조'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: f0c08e5be9144bdefc3fe0b4609bad2421889d52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477569"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="80e6f-103">방법: Visual Basic에서 COM 개체 참조</span><span class="sxs-lookup"><span data-stu-id="80e6f-103">How to: Reference COM Objects from Visual Basic</span></span>

<span data-ttu-id="80e6f-104">Visual Basic에서 형식 라이브러리가 있는 COM 개체에 대 한 참조를 추가 하려면 COM 라이브러리에 대 한 interop 어셈블리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-104">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="80e6f-105">COM 개체의 멤버에 대 한 참조는 interop 어셈블리로 라우팅되고 실제 COM 개체로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-105">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="80e6f-106">COM 개체의 응답이 interop 어셈블리로 라우팅되고 .NET Framework 응용 프로그램으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-106">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="80e6f-107">COM 개체에 대 한 형식 정보를 .NET 어셈블리에 포함 하 여 interop 어셈블리를 사용 하지 않고 COM 개체를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-107">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="80e6f-108">형식 정보를 포함 하려면 `Embed Interop Types` `True` COM 개체에 대 한 참조에 대 한 속성을로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-108">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="80e6f-109">명령줄 컴파일러를 사용 하 여 컴파일하는 경우 옵션을 사용 하 여 `/link` COM 라이브러리를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-109">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="80e6f-110">자세한 내용은 [링크 (Visual Basic)](../../reference/command-line-compiler/link.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80e6f-110">For more information, see [-link (Visual Basic)](../../reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="80e6f-111">IDE (통합 개발 환경)에서 형식 라이브러리에 대 한 참조를 추가 하면 Visual Basic에서 자동으로 interop 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-111">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="80e6f-112">명령줄에서 작업할 때 Tlbimp 유틸리티를 사용 하 여 interop 어셈블리를 수동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-112">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="80e6f-113">COM 개체에 대 한 참조를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="80e6f-113">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="80e6f-114">**프로젝트** 메뉴에서 **참조 추가** 를 선택한 다음 대화 상자에서 **COM** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-114">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="80e6f-115">COM 개체 목록에서 사용 하려는 구성 요소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-115">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="80e6f-116">Interop 어셈블리에 대 한 액세스를 간소화 하려면 `Imports` COM 개체를 사용 하는 클래스 또는 모듈의 맨 위에 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-116">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="80e6f-117">예를 들어 다음 코드 예제에서는 `INKEDLib` 라이브러리에서 참조 되는 개체에 대 한 네임 스페이스를 가져옵니다 `Microsoft InkEdit Control 1.0` .</span><span class="sxs-lookup"><span data-stu-id="80e6f-117">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="80e6f-118">Tlbimp를 사용 하 여 interop 어셈블리를 만들려면</span><span class="sxs-lookup"><span data-stu-id="80e6f-118">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="80e6f-119">검색 경로에 아직 없는 경우 Tlbimp의 위치를 검색 경로에 추가 하 고 현재 디렉터리가 있는 디렉터리에 있지 않은 경우에는 해당 위치를 검색 경로에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="80e6f-120">명령 프롬프트에서 Tlbimp를 호출 하 여 다음 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="80e6f-121">형식 라이브러리를 포함 하는 DLL의 이름 및 위치</span><span class="sxs-lookup"><span data-stu-id="80e6f-121">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="80e6f-122">정보를 배치할 네임 스페이스의 이름 및 위치</span><span class="sxs-lookup"><span data-stu-id="80e6f-122">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="80e6f-123">대상 interop 어셈블리의 이름 및 위치</span><span class="sxs-lookup"><span data-stu-id="80e6f-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="80e6f-124">다음 코드는 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-124">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="80e6f-125">Tlbimp를 사용 하 여 등록 되지 않은 COM 개체의 경우에도 형식 라이브러리에 대 한 interop 어셈블리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="80e6f-126">그러나 interop 어셈블리에서 참조 하는 COM 개체를 사용 하려는 컴퓨터에 올바르게 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="80e6f-127">Windows 운영 체제에 포함 된 Regsvr32 유틸리티를 사용 하 여 COM 개체를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80e6f-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e6f-128">추가 정보</span><span class="sxs-lookup"><span data-stu-id="80e6f-128">See also</span></span>

- [<span data-ttu-id="80e6f-129">COM Interop</span><span class="sxs-lookup"><span data-stu-id="80e6f-129">COM Interop</span></span>](index.md)
- [<span data-ttu-id="80e6f-130">Tlbimp.exe(형식 라이브러리 가져오기)</span><span class="sxs-lookup"><span data-stu-id="80e6f-130">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="80e6f-131">Tlbexp.exe(형식 라이브러리 내보내기)</span><span class="sxs-lookup"><span data-stu-id="80e6f-131">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="80e6f-132">연습: COM 개체를 사용한 상속 구현</span><span class="sxs-lookup"><span data-stu-id="80e6f-132">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="80e6f-133">상호 운용성 문제 해결</span><span class="sxs-lookup"><span data-stu-id="80e6f-133">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="80e6f-134">Imports 문(.NET 네임스페이스 및 형식)</span><span class="sxs-lookup"><span data-stu-id="80e6f-134">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
