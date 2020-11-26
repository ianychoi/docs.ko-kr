---
title: UI 자동화 요소 가져오기
description: UI (사용자 인터페이스) 요소에 대해 UI 자동화 요소 (AutomationElement) 개체를 가져오는 다양 한 방법을 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 66a8d9e944a8f8a777ec744a33f2cdb2d33e200c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237354"
---
# <a name="obtaining-ui-automation-elements"></a><span data-ttu-id="52941-103">UI 자동화 요소 가져오기</span><span class="sxs-lookup"><span data-stu-id="52941-103">Obtaining UI Automation Elements</span></span>

> [!NOTE]
> <span data-ttu-id="52941-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="52941-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52941-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="52941-106">이 항목에서는 <xref:System.Windows.Automation.AutomationElement> 요소에 대한 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 개체를 가져오는 다양한 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-106">This topic describes the various ways of obtaining <xref:System.Windows.Automation.AutomationElement> objects for [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="52941-107">클라이언트 애플리케이션이 자체 사용자 인터페이스에서 요소를 찾으려고 시도하는 경우 별도 스레드에서 모든 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-107">If your client application might attempt to find elements in its own user interface, you must make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="52941-108">자세한 내용은 [UI Automation Threading Issues](ui-automation-threading-issues.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52941-108">For more information, see [UI Automation Threading Issues](ui-automation-threading-issues.md).</span></span>  
  
<a name="The_Root_Element"></a>

## <a name="root-element"></a><span data-ttu-id="52941-109">루트 요소</span><span class="sxs-lookup"><span data-stu-id="52941-109">Root Element</span></span>  

 <span data-ttu-id="52941-110"><xref:System.Windows.Automation.AutomationElement> 개체에 대한 모든 검색은 시작 지점이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-110">All searches for <xref:System.Windows.Automation.AutomationElement> objects must have a starting-place.</span></span> <span data-ttu-id="52941-111">데스크톱, 애플리케이션 창 또는 컨트롤을 포함한 모든 요소가 대상이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-111">This can be any element, including the desktop, an application window, or a control.</span></span>  
  
 <span data-ttu-id="52941-112">모든 요소가 하위 항목인 데스크톱의 루트 요소는 정적 <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> 속성에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52941-112">The root element for the desktop, from which all elements are descended, is obtained from the static <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> property.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="52941-113">일반적으로 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>의 직계 자식 항목만 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-113">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="52941-114">하위 항목 검색은 수 많은 요소에서 반복될 수 있기 때문에 스택 오버플로가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-114">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="52941-115">낮은 수준의 특정 요소를 가져오려고 시도하는 경우, 낮은 수준의 컨테이너 또는 애플리케이션 창에서 검색을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-115">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
<a name="Using_Conditions"></a>

## <a name="conditions"></a><span data-ttu-id="52941-116">조건</span><span class="sxs-lookup"><span data-stu-id="52941-116">Conditions</span></span>  

 <span data-ttu-id="52941-117">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 요소를 검색할 때 사용할 수 있는 대부분의 기술에 대해, 검색할 요소가 무엇인지 정의하는 기준 집합인 <xref:System.Windows.Automation.Condition>을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-117">For most techniques you can use to retrieve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements, you must specify a <xref:System.Windows.Automation.Condition>, which is a set of criteria defining what elements you want to retrieve.</span></span>  
  
 <span data-ttu-id="52941-118">가장 간단한 조건은 <xref:System.Windows.Automation.Condition.TrueCondition>으로서, 검색 범위 내의 모든 요소가 반환되도록 하는 미리 정의된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-118">The simplest condition is <xref:System.Windows.Automation.Condition.TrueCondition>, a predefined object specifying that all elements within the search scope are to be returned.</span></span> <span data-ttu-id="52941-119"><xref:System.Windows.Automation.Condition.FalseCondition>과는 반대로 <xref:System.Windows.Automation.Condition.TrueCondition>은 요소가 검색되지 않도록 하기 때문에 그다지 유용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-119"><xref:System.Windows.Automation.Condition.FalseCondition>, the converse of <xref:System.Windows.Automation.Condition.TrueCondition>, is less useful, as it would prevent any elements from being found.</span></span>  
  
 <span data-ttu-id="52941-120">단독으로 또는 다른 조건과 함께 사용할 수 있는 기타 미리 정의된 3개의 조건으로 <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>및 <xref:System.Windows.Automation.Automation.RawViewCondition>이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-120">Three other predefined conditions can be used alone or in combination with other conditions: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, and <xref:System.Windows.Automation.Automation.RawViewCondition>.</span></span> <span data-ttu-id="52941-121">단독으로 사용되는은 또는  속성별로 요소를 필터링하지 않기 때문에  에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-121"><xref:System.Windows.Automation.Automation.RawViewCondition>, used by itself, is equivalent to <xref:System.Windows.Automation.Condition.TrueCondition>, because it does not filter elements by their <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> or <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> properties.</span></span>  
  
 <span data-ttu-id="52941-122">하나 이상의 <xref:System.Windows.Automation.PropertyCondition> 개체에서 기타 조건이 생성되고, 각 조건은 속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-122">Other conditions are built up from one or more <xref:System.Windows.Automation.PropertyCondition> objects, each of which specifies a property value.</span></span> <span data-ttu-id="52941-123">예를 들어, <xref:System.Windows.Automation.PropertyCondition> 은 요소가 활성화되도록 지정하거나 특정 컨트롤 패턴을 지원하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-123">For example, a <xref:System.Windows.Automation.PropertyCondition> might specify that the element is enabled, or that it supports a certain control pattern.</span></span>  
  
 <span data-ttu-id="52941-124">개체 형식 <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>및 <xref:System.Windows.Automation.NotCondition>을 생성하고 부울 논리를 사용하여 조건을 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-124">Conditions can be combined using Boolean logic by constructing objects of types <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, and <xref:System.Windows.Automation.NotCondition>.</span></span>  
  
<a name="Search_Scope"></a>

## <a name="search-scope"></a><span data-ttu-id="52941-125">검색 범위</span><span class="sxs-lookup"><span data-stu-id="52941-125">Search Scope</span></span>  

 <span data-ttu-id="52941-126"><xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 또는 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 을 사용하여 수행되는 검색에는 시작 지점뿐만 아니라 범위가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-126">Searches done by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A> must have a scope as well as a starting-place.</span></span>  
  
 <span data-ttu-id="52941-127">범위는 검색되는 시작 지점 주변의 공간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-127">The scope defines the space around the starting-place that is to be searched.</span></span> <span data-ttu-id="52941-128">여기에는 요소 자체, 형제 항목, 부모 항목, 상위 항목, 직계 자식 항목, 하위 항목이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-128">This might include the element itself, its siblings, its parent, its ancestors, its immediate children, and its descendants.</span></span>  
  
 <span data-ttu-id="52941-129">검색 범위는 <xref:System.Windows.Automation.TreeScope> 열거형의 값을 비트 조합하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="52941-129">The scope of a search is defined by a bitwise combination of values from the <xref:System.Windows.Automation.TreeScope> enumeration.</span></span>  
  
<a name="Finding_a_Known_Element"></a>

## <a name="finding-a-known-element"></a><span data-ttu-id="52941-130">알려진 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="52941-130">Finding a Known Element</span></span>  

 <span data-ttu-id="52941-131"><xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>또는 기타 속성이나 속성의 조합으로 식별된 알려진 요소를 찾으려면 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 메서드를 사용하는 것이 가장 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-131">To find a known element, identified by its <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, or some other property or combination of properties, it is easiest to use the <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> method.</span></span> <span data-ttu-id="52941-132">검색된 요소가 애플리케이션 창일 경우 검색의 시작 지점은 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-132">If the element sought is an application window, the starting-point of the search can be the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span>  
  
 <span data-ttu-id="52941-133">이렇게 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 요소를 찾는 것은 자동화된 테스트 시나리오에서 가장 유용한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-133">This way of finding [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements is most useful in automated testing scenarios.</span></span>  
  
<a name="Finding_Elements_in_a_Subtree"></a>

## <a name="finding-elements-in-a-subtree"></a><span data-ttu-id="52941-134">하위 트리에서 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="52941-134">Finding Elements in a Subtree</span></span>  

 <span data-ttu-id="52941-135">알려진 요소와 관련된 특정 기준을 충족하는 모든 요소를 찾으려면 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-135">To find all elements meeting specific criteria that are related to a known element, you can use <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span> <span data-ttu-id="52941-136">예를 들어, 목록 또는 메뉴에서 목록 항목이나 메뉴 항목을 검색하거나 대화 상자의 모든 컨트롤을 식별할 때 이 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-136">For example, you could use this method to retrieve list items or menu items from a list or menu, or to identify all controls in a dialog box.</span></span>  
  
<a name="Walking_a_Subtree"></a>

## <a name="walking-a-subtree"></a><span data-ttu-id="52941-137">하위 트리 탐색</span><span class="sxs-lookup"><span data-stu-id="52941-137">Walking a Subtree</span></span>  

 <span data-ttu-id="52941-138">클라이언트가 사용되는 애플리케이션에 대한 사전 지식이 없는 경우 <xref:System.Windows.Automation.TreeWalker> 클래스를 사용하여 필요한 모든 요소의 하위 트리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-138">If you have no prior knowledge of the applications that your client may be used with, you can construct a subtree of all elements of interest by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span> <span data-ttu-id="52941-139">애플리케이션이 포커스 변경 이벤트에 대한 응답으로 이 작업을 수행할 수 있습니다. 즉, 애플리케이션 또는 컨트롤이 입력 포커스를 받으면 UI 자동화 클라이언트는 포커스가 있는 요소의 자식 항목 및 모든 하위 항목을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-139">Your application might do this in response to a focus-changed event; that is, when an application or control receives input focus, the UI Automation client examines children and perhaps all descendants of the focused element.</span></span>  
  
 <span data-ttu-id="52941-140"><xref:System.Windows.Automation.TreeWalker> 를 사용하여 요소의 상위 항목을 식별할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-140">Another way in which <xref:System.Windows.Automation.TreeWalker> can be used is to identify the ancestors of an element.</span></span> <span data-ttu-id="52941-141">예를 들어, 트리를 탐색하여 컨트롤의 부모 창을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-141">For example, by walking up the tree you can identify the parent window of a control.</span></span>  
  
 <span data-ttu-id="52941-142">필요한 클래스의 개체를 만들거나( <xref:System.Windows.Automation.TreeWalker> 을 전달하여 필요한 요소 정의) <xref:System.Windows.Automation.Condition>의 필드로 정의된 미리 정의된 다음 개체 중 하나를 사용하여 <xref:System.Windows.Automation.TreeWalker>를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-142">You can use <xref:System.Windows.Automation.TreeWalker> either by creating an object of the class (defining the elements of interest by passing a <xref:System.Windows.Automation.Condition>), or by using one of the following predefined objects that are defined as fields of <xref:System.Windows.Automation.TreeWalker>.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|<span data-ttu-id="52941-143"><xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> 속성이 `true`인 요소만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-143">Finds only elements whose <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> property is `true`.</span></span>|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|<span data-ttu-id="52941-144"><xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> 속성이 `true`인 요소만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-144">Finds only elements whose <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> property is `true`.</span></span>|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|<span data-ttu-id="52941-145">모든 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-145">Finds all elements.</span></span>|  
  
 <span data-ttu-id="52941-146"><xref:System.Windows.Automation.TreeWalker>를 가져온 후에는 간단하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-146">After you have obtained a <xref:System.Windows.Automation.TreeWalker>, using it is straightforward.</span></span> <span data-ttu-id="52941-147">`Get` 메서드를 호출하여 하위 트리의 요소를 탐색하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52941-147">Simply call the `Get` methods to navigate among elements of the subtree.</span></span>  
  
 <span data-ttu-id="52941-148"><xref:System.Windows.Automation.TreeWalker.Normalize%2A> 메서드를 사용하여 뷰에 속하지 않은 다른 요소의 하위 트리에서 요소를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-148">The <xref:System.Windows.Automation.TreeWalker.Normalize%2A> method can be used for navigating to an element in the subtree from another element that is not part of the view.</span></span> <span data-ttu-id="52941-149">예를 들어, <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>를 사용하여 하위 트리 뷰를 만들었다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-149">For example, suppose you have created a view of a subtree by using <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>.</span></span> <span data-ttu-id="52941-150">그러면 스크롤 막대가 입력 포커스를 받았다는 알림이 애플리케이션에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="52941-150">Your application then receives notification that a scroll bar has received the input focus.</span></span> <span data-ttu-id="52941-151">스크롤 막대는 콘텐츠 요소가 아니기 때문에 하위 트리의 뷰에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-151">Because a scroll bar is not a content element, it is not present in your view of the subtree.</span></span> <span data-ttu-id="52941-152">하지만 스크롤 막대를 나타내는 <xref:System.Windows.Automation.AutomationElement> 를 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> 에 전달하고 콘텐츠 뷰에 있는 가장 가까운 상위 항목을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-152">However, you can pass the <xref:System.Windows.Automation.AutomationElement> representing the scroll bar to <xref:System.Windows.Automation.TreeWalker.Normalize%2A> and retrieve the nearest ancestor that is in the content view.</span></span>  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>

## <a name="other-ways-to-retrieve-an-element"></a><span data-ttu-id="52941-153">요소를 검색하는 기타 방법</span><span class="sxs-lookup"><span data-stu-id="52941-153">Other Ways to Retrieve an Element</span></span>  

 <span data-ttu-id="52941-154">검색 및 탐색 외에도 다음과 같은 방법으로 <xref:System.Windows.Automation.AutomationElement> 를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-154">In addition to searches and navigation, you can retrieve an <xref:System.Windows.Automation.AutomationElement> in the following ways.</span></span>  
  
### <a name="from-an-event"></a><span data-ttu-id="52941-155">이벤트에서</span><span class="sxs-lookup"><span data-stu-id="52941-155">From an Event</span></span>  

 <span data-ttu-id="52941-156">애플리케이션이 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트를 수신하면, 이벤트 처리기에 전달된 소스 개체는 <xref:System.Windows.Automation.AutomationElement>입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-156">When your application receives a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event, the source object passed to your event handler is an <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="52941-157">예를 들어, 포커스 변경 이벤트를 구독한 경우 <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> 에 전달된 소스는 포커스를 받은 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52941-157">For example, if you have subscribed to focus-changed events, the source passed to your <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> is the element that received the focus.</span></span>  
  
 <span data-ttu-id="52941-158">자세한 내용은 [Subscribe to UI Automation Events](subscribe-to-ui-automation-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52941-158">For more information, see [Subscribe to UI Automation Events](subscribe-to-ui-automation-events.md).</span></span>  
  
### <a name="from-a-point"></a><span data-ttu-id="52941-159">지점에서</span><span class="sxs-lookup"><span data-stu-id="52941-159">From a Point</span></span>  

 <span data-ttu-id="52941-160">화면 좌표가 있는 경우(예: 커서 위치) 정적 <xref:System.Windows.Automation.AutomationElement> 메서드를 사용하여 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> 를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-160">If you have screen coordinates (for example, a cursor position), you can retrieve an <xref:System.Windows.Automation.AutomationElement> by using the static <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> method.</span></span>  
  
### <a name="from-a-window-handle"></a><span data-ttu-id="52941-161">창 핸들에서</span><span class="sxs-lookup"><span data-stu-id="52941-161">From a Window Handle</span></span>  

 <span data-ttu-id="52941-162">HWND에서 <xref:System.Windows.Automation.AutomationElement> 를 검색하려면 정적 <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52941-162">To retrieve an <xref:System.Windows.Automation.AutomationElement> from an HWND, use the static <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> method.</span></span>  
  
### <a name="from-the-focused-control"></a><span data-ttu-id="52941-163">포커스가 있는 컨트롤에서</span><span class="sxs-lookup"><span data-stu-id="52941-163">From the Focused Control</span></span>  

 <span data-ttu-id="52941-164">정적 <xref:System.Windows.Automation.AutomationElement> 속성에서 포커스가 있는 컨트롤을 나타내는 <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> 를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52941-164">You can retrieve an <xref:System.Windows.Automation.AutomationElement> that represents the focused control from the static <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52941-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52941-165">See also</span></span>

- [<span data-ttu-id="52941-166">속성 조건에 따라 UI 자동화 요소 찾기</span><span class="sxs-lookup"><span data-stu-id="52941-166">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="52941-167">TreeWalker를 사용하여 UI 자동화 요소 간 탐색</span><span class="sxs-lookup"><span data-stu-id="52941-167">Navigate Among UI Automation Elements with TreeWalker</span></span>](navigate-among-ui-automation-elements-with-treewalker.md)
- [<span data-ttu-id="52941-168">UI 자동화 트리 개요</span><span class="sxs-lookup"><span data-stu-id="52941-168">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
