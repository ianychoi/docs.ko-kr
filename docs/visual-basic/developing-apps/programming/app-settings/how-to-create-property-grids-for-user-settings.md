---
description: '자세한 정보: 방법: Visual Basic에서 사용자 설정의 속성 표 만들기'
title: '방법: 사용자 설정의 속성 그리드 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 19523f712207cac225ccf68e02e338a9e76fe358
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797850"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="9b988-103">방법: Visual Basic에서 사용자 설정의 속성 표 만들기</span><span class="sxs-lookup"><span data-stu-id="9b988-103">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="9b988-104"><xref:System.Windows.Forms.PropertyGrid> 컨트롤을 `My.Settings` 개체의 사용자 설정 속성으로 채워 사용자 설정에 대한 속성 표를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-104">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b988-105">이 예제가 작동하려면 애플리케이션에 해당 사용자 설정이 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-105">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="9b988-106">자세한 내용은 [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b988-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="9b988-107">`My.Settings` 개체는 각 설정을 속성으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-107">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="9b988-108">속성 이름은 설정 이름과 같고 속성 형식은 설정 형식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-108">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="9b988-109">설정의 **범위** 는 속성이 읽기 전용인지 여부를 결정합니다. **애플리케이션** 범위 설정의 속성은 읽기 전용이지만 **사용자** 범위 설정의 속성은 읽기-쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-109">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="9b988-110">자세한 내용은 [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b988-110">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b988-111">런타임에 애플리케이션 범위 설정의 값을 변경하거나 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-111">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="9b988-112">**프로젝트 디자이너** 를 통해 또는 애플리케이션의 구성 파일을 편집하여 애플리케이션을 만들 때만 애플리케이션 범위 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-112">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="9b988-113">자세한 내용은 [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b988-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="9b988-114">이 예제에서는 <xref:System.Windows.Forms.PropertyGrid> 컨트롤을 사용하여 `My.Settings` 개체의 사용자 설정 속성에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-114">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="9b988-115">기본적으로 <xref:System.Windows.Forms.PropertyGrid>는 `My.Settings` 개체의 모든 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-115">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="9b988-116">하지만 사용자 설정 속성에는 <xref:System.Configuration.UserScopedSettingAttribute> 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-116">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="9b988-117">이 예제에서는 <xref:System.Windows.Forms.PropertyGrid>의 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 속성을 <xref:System.Configuration.UserScopedSettingAttribute>로 설정하여 사용자 설정 속성만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-117">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="9b988-118">사용자 설정 속성 표를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="9b988-118">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="9b988-119">**도구 상자** 에서 애플리케이션의 디자인 화면(여기서는 `Form1`)으로 **PropertyGrid** 컨트롤을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-119">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="9b988-120">속성 표 컨트롤의 기본 이름은 `PropertyGrid1`입니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-120">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="9b988-121">`Form1`의 디자인 화면을 두 번 클릭하여 양식 로드 이벤트 처리기에 대한 코드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-121">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="9b988-122">`My.Settings` 개체를 속성 표에 대해 선택된 개체로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-122">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="9b988-123">사용자 설정만 표시하도록 속성 표를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-123">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="9b988-124">애플리케이션 범위 설정만 표시하려면 <xref:System.Configuration.UserScopedSettingAttribute> 대신 <xref:System.Configuration.ApplicationScopedSettingAttribute> 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-124">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9b988-125">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="9b988-125">Robust Programming</span></span>  

 <span data-ttu-id="9b988-126">애플리케이션이 종료될 때 사용자 설정이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-126">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="9b988-127">설정을 즉시 저장하려면 `My.Settings.Save` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9b988-127">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="9b988-128">자세한 내용은 [방법: Visual Basic에서 사용자 설정 유지](how-to-persist-user-settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b988-128">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b988-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b988-129">See also</span></span>

- [<span data-ttu-id="9b988-130">My.Settings 개체</span><span class="sxs-lookup"><span data-stu-id="9b988-130">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="9b988-131">방법: Visual Basic에서 애플리케이션 설정 읽기</span><span class="sxs-lookup"><span data-stu-id="9b988-131">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="9b988-132">방법: Visual Basic에서 사용자 설정 변경</span><span class="sxs-lookup"><span data-stu-id="9b988-132">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="9b988-133">방법: Visual Basic에서 사용자 설정 유지</span><span class="sxs-lookup"><span data-stu-id="9b988-133">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="9b988-134">애플리케이션 설정 관리(.NET)</span><span class="sxs-lookup"><span data-stu-id="9b988-134">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
