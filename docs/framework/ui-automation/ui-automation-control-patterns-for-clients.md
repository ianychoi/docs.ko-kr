---
title: 클라이언트용 UI 자동화 컨트롤 패턴
description: UI 자동화 클라이언트의 컨트롤 패턴에 대 한 개요를 참조 하세요. 컨트롤 패턴을 사용 하 여 UI (사용자 인터페이스)에 대 한 정보에 액세스 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 3f58e9909b18681b3a0acf9332cc0c7c604e2002
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241969"
---
# <a name="ui-automation-control-patterns-for-clients"></a><span data-ttu-id="0b432-104">클라이언트용 UI 자동화 컨트롤 패턴</span><span class="sxs-lookup"><span data-stu-id="0b432-104">UI Automation Control Patterns for Clients</span></span>

> [!NOTE]
> <span data-ttu-id="0b432-105">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0b432-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b432-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0b432-107">이 개요에서는 UI 자동화 클라이언트에 대한 컨트롤 패턴을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-107">This overview introduces control patterns for UI Automation clients.</span></span> <span data-ttu-id="0b432-108">UI 자동화 클라이언트에서 컨트롤 패턴을 사용하여 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]에 대한 정보에 액세스하는 방법도 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-108">It includes information on how a UI Automation client can use control patterns to access information about the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="0b432-109">컨트롤 패턴은 컨트롤 형식 및 컨트롤의 모양에 관계없이 컨트롤의 기능을 분류하고 노출하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-109">Control patterns provide a way to categorize and expose a control's functionality independent of the control type or the appearance of the control.</span></span> <span data-ttu-id="0b432-110">UI 자동화 클라이언트는 <xref:System.Windows.Automation.AutomationElement> 를 검사하여 지원되는 컨트롤 패턴을 확인하고 컨트롤의 동작을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-110">UI Automation clients can examine an <xref:System.Windows.Automation.AutomationElement> to determine which control patterns are supported and be assured of the behavior of the control.</span></span>  
  
 <span data-ttu-id="0b432-111">컨트롤 패턴의 전체 목록은 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b432-111">For a complete list of control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).</span></span>  
  
<a name="uiautomation_getting_control_patterns"></a>

## <a name="getting-control-patterns"></a><span data-ttu-id="0b432-112">컨트롤 패턴 가져오기</span><span class="sxs-lookup"><span data-stu-id="0b432-112">Getting Control Patterns</span></span>  

 <span data-ttu-id="0b432-113">클라이언트는 <xref:System.Windows.Automation.AutomationElement> 또는 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> 을 호출하여 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>에서 컨트롤 패턴을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-113">Clients retrieve a control pattern from an <xref:System.Windows.Automation.AutomationElement> by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0b432-114">클라이언트는 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 메서드 또는 개별 `IsPatternAvailable` 속성(예: <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>)을 사용하여 패턴이나 패턴 그룹이 <xref:System.Windows.Automation.AutomationElement>에서 지원되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-114">Clients can use the <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> method or an individual `IsPatternAvailable` property (for example, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) to determine if a pattern or group of patterns is supported on the <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="0b432-115">그러나 컨트롤 패턴을 가져오고 `null` 참조를 테스트하면 프로세스 간 호출을 줄일 수 있으므로 지원되는 속성을 확인하고 컨트롤 패턴을 검색하는 것보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-115">However, it is more efficient to attempt to get the control pattern and test for a `null` reference than to check the supported properties and retrieve the control pattern since it results in fewer cross-process calls.</span></span>  
  
 <span data-ttu-id="0b432-116">다음 예제에서는 <xref:System.Windows.Automation.TextPattern> 에서 <xref:System.Windows.Automation.AutomationElement>컨트롤 패턴을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-116">The following example demonstrates how to get a <xref:System.Windows.Automation.TextPattern> control pattern from an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>

## <a name="retrieving-properties-on-control-patterns"></a><span data-ttu-id="0b432-117">컨트롤 패턴에 대한 속성 검색</span><span class="sxs-lookup"><span data-stu-id="0b432-117">Retrieving Properties on Control Patterns</span></span>  

 <span data-ttu-id="0b432-118">클라이언트는 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> 또는 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> 를 호출하고 적절한 형식으로 반환되는 개체를 캐스팅하여 컨트롤 패턴에 대한 속성 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-118">Clients can retrieve the property values on control patterns by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> and casting the object returned to an appropriate type.</span></span> <span data-ttu-id="0b432-119">속성에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [클라이언트에 대 한 UI 자동화 속성](ui-automation-properties-for-clients.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b432-119">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
 <span data-ttu-id="0b432-120">메서드 외에도 `GetPropertyValue` CLR (공용 언어 런타임) 접근자를 통해 속성 값을 검색 하 여 패턴에 대 한 속성에 액세스할 수 있습니다 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b432-120">In addition to the `GetPropertyValue` methods, property values can be retrieved through the common language runtime (CLR) accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.</span></span>  
  
<a name="uiautomation_with_variable_patterns"></a>

## <a name="controls-with-variable-patterns"></a><span data-ttu-id="0b432-121">가변 패턴을 사용하는 컨트롤</span><span class="sxs-lookup"><span data-stu-id="0b432-121">Controls with Variable Patterns</span></span>  

 <span data-ttu-id="0b432-122">일부 컨트롤 형식은 컨트롤의 상태 또는 컨트롤이 사용되는 방식에 따라 다양한 패턴을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-122">Some control types support different patterns depending on their state or the manner in which the control is being used.</span></span> <span data-ttu-id="0b432-123">변수 패턴을 사용할 수 있는 컨트롤의 예로는 목록 보기 (미리 보기, 타일, 아이콘, 목록, 세부 정보), Microsoft Excel 차트 (원형, 꺾은선형, 가로 막대형, 수식이 있는 셀 값), Microsoft Word의 문서 영역 (기본, 웹 레이아웃, 개요, 인쇄 레이아웃, 인쇄 미리 보기) 및 Microsoft Windows Media Player 스킨이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-123">Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), Microsoft Excel Charts (Pie, Line, Bar, Cell Value with a formula), Microsoft Word's document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and Microsoft Windows Media Player skins.</span></span>  
  
 <span data-ttu-id="0b432-124">사용자 지정 컨트롤 형식을 구현하는 컨트롤에는 해당 기능을 나타내는 데 필요한 컨트롤 패턴 집합이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b432-124">Controls implementing custom control types can have any set of control patterns that are needed to represent their functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b432-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b432-125">See also</span></span>

- [<span data-ttu-id="0b432-126">UI 자동화 컨트롤 패턴</span><span class="sxs-lookup"><span data-stu-id="0b432-126">UI Automation Control Patterns</span></span>](ui-automation-control-patterns.md)
- [<span data-ttu-id="0b432-127">UI 자동화 텍스트 패턴</span><span class="sxs-lookup"><span data-stu-id="0b432-127">UI Automation Text Pattern</span></span>](ui-automation-text-pattern.md)
- [<span data-ttu-id="0b432-128">UI 자동화를 사용하여 컨트롤 호출</span><span class="sxs-lookup"><span data-stu-id="0b432-128">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="0b432-129">UI 자동화를 사용하여 확인란의 전환 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="0b432-129">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="0b432-130">UI 자동화 클라이언트에 대한 컨트롤 패턴 매핑</span><span class="sxs-lookup"><span data-stu-id="0b432-130">Control Pattern Mapping for UI Automation Clients</span></span>](control-pattern-mapping-for-ui-automation-clients.md)
- [<span data-ttu-id="0b432-131">TextPattern Insert 텍스트 샘플</span><span class="sxs-lookup"><span data-stu-id="0b432-131">TextPattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="0b432-132">TextPattern 검색 및 선택 샘플</span><span class="sxs-lookup"><span data-stu-id="0b432-132">TextPattern Search and Selection Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [<span data-ttu-id="0b432-133">InvokePattern, ExpandCollapsePattern 및 TogglePattern 샘플</span><span class="sxs-lookup"><span data-stu-id="0b432-133">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
