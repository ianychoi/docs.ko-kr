---
title: AutomationID 속성 사용
description: AutomationID 속성을 사용 하 여 UI 자동화 트리 내에서 요소를 찾는 방법과 시기를 보여주는 시나리오 및 샘플 코드를 검토 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 91254903b3481861f21d5e2f4e51f1e50726c46b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258597"
---
# <a name="use-the-automationid-property"></a><span data-ttu-id="111d2-103">AutomationID 속성 사용</span><span class="sxs-lookup"><span data-stu-id="111d2-103">Use the AutomationID Property</span></span>

> [!NOTE]
> <span data-ttu-id="111d2-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="111d2-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="111d2-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="111d2-106">이 항목에는 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 를 사용하여 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 내에서 요소를 찾는 방법과 시기를 보여주는 시나리오와 샘플 코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-106">This topic contains scenarios and sample code that show how and when the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> can be used to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>  
  
 <span data-ttu-id="111d2-107"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 는 형제 항목에서 UI 자동화 요소를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-107"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> uniquely identifies a UI Automation element from its siblings.</span></span> <span data-ttu-id="111d2-108">컨트롤 식별과 관련된 속성 식별자에 대한 자세한 내용은 [UI Automation Properties Overview](ui-automation-properties-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="111d2-108">For more information on property identifiers related to control identification, see [UI Automation Properties Overview](ui-automation-properties-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="111d2-109"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 는 트리 전체에서 고유한 ID를 보장하지 않습니다. 일반적으로 컨테이너 및 범위 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-109"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> does not guarantee a unique identity throughout the tree; it typically needs container and scope information to be useful.</span></span> <span data-ttu-id="111d2-110">예를 들어, 애플리케이션에는 여러 개의 최상위 메뉴가 있는 메뉴 컨트롤과 여러 개의 자식 메뉴 항목이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-110">For example, an application may contain a menu control with multiple top-level menu items that, in turn, have multiple child menu items.</span></span> <span data-ttu-id="111d2-111">이러한 보조 메뉴 항목은 "Item1", "Item 2" 등과 같이 일반적인 체계로 식별되어 최상위 메뉴 항목에서 자식에 대한 중복 식별자가 허용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-111">These secondary menu items may be identified by a generic scheme such as "Item1", "Item 2", and so on, allowing duplicate identifiers for children across top-level menu items.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="111d2-112">시나리오</span><span class="sxs-lookup"><span data-stu-id="111d2-112">Scenarios</span></span>  

 <span data-ttu-id="111d2-113">주 UI 자동화 클라이언트 애플리케이션의 3가지 시나리오에서, <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 를 사용해야 요소를 검색할 때 정확하고 일관된 결과를 얻을 수 있다고 확인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-113">Three primary UI Automation client application scenarios have been identified that require the use of <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> to achieve accurate and consistent results when searching for elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="111d2-114"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 는 최상위 응용 프로그램 창, ID 또는 x:Uid가 없는 컨트롤에서 파생 된 UI 자동화 요소 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , 컨트롤 id가 없는 Win32 컨트롤에서 파생 된 ui 자동화 요소를 제외 하 고 컨트롤 뷰의 모든 UI 자동화 요소에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-114"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> is supported by all UI Automation elements in the control view except top-level application windows, UI Automation elements derived from [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls that do not have an ID or x:Uid, and UI Automation elements derived from Win32 controls that do not have a control ID.</span></span>  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a><span data-ttu-id="111d2-115">검색 가능하고 고유한 AutomationID를 사용하여 UI 자동화 트리에서 특정 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-115">Use a unique and discoverable AutomationID to locate a specific element in the UI Automation tree</span></span>  
  
- <span data-ttu-id="111d2-116">UI Spy와 같은 도구를 사용 하 여 관심 있는 요소의를 보고 합니다 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="111d2-116">Use a tool such as UI Spy to report the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> of a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element of interest.</span></span> <span data-ttu-id="111d2-117">그런 다음 이 값을 복사하여 클라이언트 애플리케이션에 붙여넣을 수 있습니다(예: 이후의 자동 테스트를 위한 테스트 스크립트).</span><span class="sxs-lookup"><span data-stu-id="111d2-117">This value can then be copied and pasted into a client application such as a test script for subsequent automated testing.</span></span> <span data-ttu-id="111d2-118">이 방법은 런타임 시에 요소를 식별하고 찾는 데 필요한 코드의 수를 줄이고 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-118">This approach reduces and simplifies the code necessary to identify and locate an element at runtime.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="111d2-119">일반적으로 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>의 직계 자식 항목만 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-119">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="111d2-120">하위 항목 검색은 수 많은 요소에서 반복될 수 있기 때문에 스택 오버플로가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-120">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="111d2-121">낮은 수준의 특정 요소를 가져오려고 시도하는 경우, 낮은 수준의 컨테이너 또는 애플리케이션 창에서 검색을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-121">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="111d2-122">영구 경로를 사용하여 이전에 식별된 AutomationElement로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="111d2-122">Use a persistent path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="111d2-123">간단한 테스트 스크립트에서 견고한 레코드 및 재생 유틸리티에 이르기까지, 클라이언트 애플리케이션은 파일 열기 대화 상자 또는 메뉴 항목 등과 같이 현재 인스턴스화되지 않아서 UI 자동화 트리에 존재하지 않는 요소에 액세스해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-123">Client applications, from simple test scripts to robust record and playback utilities, may require access to elements that are not currently instantiated, such as a file open dialog or a menu item and therefore do not exist in the UI Automation tree.</span></span> <span data-ttu-id="111d2-124">이러한 요소는 AutomationID, 컨트롤 패턴 및 이벤트 수신기와 같은 UI 자동화 속성을 사용 하 여 UI 작업의 특정 시퀀스를 재현 하거나 "재생" 해야만 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-124">These elements can only be instantiated by reproducing, or "playing back", a specific sequence of UI actions through the use of UI Automation properties such as AutomationID, control patterns, and event listeners.</span></span>
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="111d2-125">상대 경로를 사용하여 이전에 식별된 AutomationElement로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="111d2-125">Use a relative path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="111d2-126">특정 상황에서는 AutomationID가 형제 항목 간에서만 고유하기 때문에 UI 자동화 트리에서 여러 요소의 AutomationID 속성 값이 동일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-126">In certain circumstances, since AutomationID is only guaranteed to be unique amongst siblings, multiple elements in the UI Automation tree may have identical AutomationID property values.</span></span> <span data-ttu-id="111d2-127">이러한 상황에서는 필요에 따라 최상위 항목을 기준으로 요소를 고유하게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-127">In these situations the elements can be uniquely identified based on a parent and, if necessary, a grandparent.</span></span> <span data-ttu-id="111d2-128">예를 들어, 개발자가 자식 항목이 "Item1", "Item2" 등과 같은 순차적 AutomationID로 식별되는 여러 개의 자식 메뉴 항목과 함께 다수의 메뉴 항목이 있는 메뉴 모음을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-128">For example, a developer may provide a menu bar with multiple menu items each with multiple child menu items where the children are identified with sequential AutomationID's such as "Item1", "Item2", and so on.</span></span> <span data-ttu-id="111d2-129">이 경우, 필요에 따라 상위 항목 및 최상위 항목(필요한 경우)의 AutomationID와 함께 각 메뉴 항목의 AutomationID로 고유하게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="111d2-129">Each menu item could then be uniquely identified by its AutomationID along with the AutomationID of its parent and, if necessary, its grandparent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="111d2-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="111d2-130">See also</span></span>

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [<span data-ttu-id="111d2-131">UI 자동화 트리 개요</span><span class="sxs-lookup"><span data-stu-id="111d2-131">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="111d2-132">속성 조건에 따라 UI 자동화 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="111d2-132">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
