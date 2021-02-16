---
description: '자세한 정보: 연습: Visual Basic 사용 하 여 COM 개체 만들기'
title: '연습: COM 개체 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 469466189e264253f3588a0a2735afe651bbd36f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427273"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="a7e4b-103">연습: Visual Basic을 사용하여 COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="a7e4b-103">Walkthrough: Creating COM Objects with Visual Basic</span></span>

<span data-ttu-id="a7e4b-104">새 응용 프로그램 또는 구성 요소를 만들 때 .NET Framework 어셈블리를 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-104">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="a7e4b-105">그러나 Visual Basic를 사용 하면 .NET Framework 구성 요소를 COM에 쉽게 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-105">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="a7e4b-106">이를 통해 COM 구성 요소가 필요한 이전 응용 프로그램 제품군에 대해 새로운 구성 요소를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-106">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="a7e4b-107">이 연습에서는 Visual Basic를 사용 하 여 COM 클래스 템플릿을 사용 하거나 사용 하지 않고 .NET Framework 개체를 COM 개체로 노출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-107">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="a7e4b-108">Com 개체를 노출 하는 가장 쉬운 방법은 COM 클래스 템플릿을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-108">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="a7e4b-109">이 템플릿은 새 클래스를 만든 다음 상호 운용성 계층을 사용 하 여 클래스를 COM 개체로 생성 하 고 운영 체제에 등록 하도록 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-109">This template creates a new class, then configures your project to generate the class with an interoperability layer as a COM object, and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7e4b-110">Visual Basic에서 만든 클래스를 비관리 코드에서 사용할 COM 개체로 노출할 수도 있지만,이 클래스는 진정한 COM 개체가 아니므로 Visual Basic 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-110">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="a7e4b-111">자세한 내용은 [.NET Framework 애플리케이션의 COM 상호 운용성](com-interoperability-in-net-framework-applications.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-111">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="a7e4b-112">COM 클래스 템플릿을 사용 하 여 COM 개체를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a7e4b-112">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="a7e4b-113">**파일** 메뉴에서 새 **프로젝트** 를 클릭 하 여 새 Windows 응용 프로그램 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-113">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="a7e4b-114">**새 프로젝트** 대화 상자의 **프로젝트 형식** 필드에서 Windows가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-114">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="a7e4b-115">**템플릿** 목록에서 **클래스 라이브러리** 를 선택 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-115">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="a7e4b-116">새 프로젝트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-116">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="a7e4b-117">**프로젝트** 메뉴에서 **새 항목 추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-117">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="a7e4b-118">**새 항목 추가** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-118">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="a7e4b-119">**템플릿** 목록에서 **COM 클래스** 를 선택한 다음 **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-119">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="a7e4b-120">Visual Basic 새 클래스를 추가 하 고 COM interop에 대 한 새 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-120">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="a7e4b-121">속성, 메서드 및 이벤트와 같은 코드를 COM 클래스에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-121">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="a7e4b-122">**빌드** 메뉴에서 **classlibrary1.chainone 빌드** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-122">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="a7e4b-123">Visual Basic는 어셈블리를 빌드하고 운영 체제에 COM 개체를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-123">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="a7e4b-124">COM 클래스 템플릿을 사용 하지 않고 COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="a7e4b-124">Creating COM Objects without the COM Class Template</span></span>  

 <span data-ttu-id="a7e4b-125">COM 클래스 템플릿을 사용 하는 대신 COM 클래스를 수동으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-125">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="a7e4b-126">이 절차는 명령줄에서 작업 하는 경우 나 COM 개체가 정의 되는 방법을 더 자세히 제어 하려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-126">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="a7e4b-127">COM 개체를 생성 하도록 프로젝트를 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="a7e4b-127">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="a7e4b-128">**Newproject** 를 클릭 하 여 **파일** 메뉴에서 새 Windows 응용 프로그램 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-128">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="a7e4b-129">**새 프로젝트** 대화 상자의 **프로젝트 형식** 필드에서 Windows가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-129">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="a7e4b-130">**템플릿** 목록에서 **클래스 라이브러리** 를 선택 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-130">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="a7e4b-131">새 프로젝트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-131">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="a7e4b-132">**솔루션 탐색기** 에서 프로젝트를 오른쪽 마우스 단추로 클릭하고 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-132">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="a7e4b-133">**프로젝트 디자이너가** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-133">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="a7e4b-134">**컴파일** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-134">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="a7e4b-135">**COM Interop 등록** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-135">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="a7e4b-136">COM 개체를 만들기 위해 클래스에 코드를 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="a7e4b-136">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="a7e4b-137">**솔루션 탐색기** 에서 **Class1 .vb** 를 두 번 클릭 하 여 해당 코드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-137">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="a7e4b-138">클래스의 이름을 `ComClass1`으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-138">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="a7e4b-139">에 다음 상수를 추가 `ComClass1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-139">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="a7e4b-140">COM 개체에 필요한 GUID (Globally Unique Identifier) 상수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-140">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="a7e4b-141">**도구** 메뉴에서 **GUID 만들기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="a7e4b-142">**GUID 만들기** 대화 상자에서 **레지스트리 형식** 과 **복사** 를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="a7e4b-143">**종료** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-143">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="a7e4b-144">에 대 한 빈 문자열을 `ClassId` GUID로 바꾸고 선행 중괄호와 후행 중괄호를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="a7e4b-145">예를 들어, Guidgen.exe에서 제공 하는 GUID가 이면 `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` 코드가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="a7e4b-146">`InterfaceId`다음 예제와 같이 및 상수에 대해 이전 단계를 반복 `EventsId` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-146">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="a7e4b-147">Guid가 새롭고 고유한 지 확인 합니다. 그렇지 않으면 COM 구성 요소가 다른 COM 구성 요소와 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-147">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="a7e4b-148">`ComClass` `ComClass1` 다음 예제와 같이 클래스 Id, 인터페이스 Id 및 이벤트 id에 대 한 guid를 지정 하 여 특성을에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-148">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="a7e4b-149">COM 클래스에는 매개 변수가 없는 생성자가 있어야 합니다 `Public Sub New()` . 그렇지 않으면 클래스가 올바르게 등록 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-149">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="a7e4b-150">클래스에 매개 변수가 없는 생성자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-150">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="a7e4b-151">클래스에 속성, 메서드 및 이벤트를 추가 하 여 `End Class` 문으로 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-151">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="a7e4b-152">**빌드** 메뉴에서 **솔루션 빌드** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-152">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="a7e4b-153">Visual Basic는 어셈블리를 빌드하고 운영 체제에 COM 개체를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-153">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a7e4b-154">Visual Basic를 사용 하 여 생성 하는 COM 개체는 진정한 COM 개체가 아니기 때문에 다른 Visual Basic 응용 프로그램에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-154">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="a7e4b-155">이러한 COM 개체에 대 한 참조를 추가 하려고 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-155">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="a7e4b-156">자세한 내용은 참조 하세요 [.NET Framework 애플리케이션의 COM 상호 운용성](com-interoperability-in-net-framework-applications.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e4b-156">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e4b-157">추가 정보</span><span class="sxs-lookup"><span data-stu-id="a7e4b-157">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="a7e4b-158">COM Interop</span><span class="sxs-lookup"><span data-stu-id="a7e4b-158">COM Interop</span></span>](index.md)
- [<span data-ttu-id="a7e4b-159">연습: COM 개체를 사용한 상속 구현</span><span class="sxs-lookup"><span data-stu-id="a7e4b-159">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="a7e4b-160">#Region 지시문</span><span class="sxs-lookup"><span data-stu-id="a7e4b-160">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="a7e4b-161">.NET Framework 애플리케이션의 COM 상호 운용성</span><span class="sxs-lookup"><span data-stu-id="a7e4b-161">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="a7e4b-162">상호 운용성 문제 해결</span><span class="sxs-lookup"><span data-stu-id="a7e4b-162">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
