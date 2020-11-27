---
title: UI 자동화를 사용하여 컨트롤 호출
description: UI 자동화를 사용 하 여 특정 속성 조건과 일치 하는 컨트롤을 찾고, AutomationElement을 만들고, InvokePattern을 가져오고, 컨트롤에서 Invoke를 사용 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 7c6f5d26d16642f978fd79fd40701c240a53f16a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278000"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="bc631-103">UI 자동화를 사용하여 컨트롤 호출</span><span class="sxs-lookup"><span data-stu-id="bc631-103">Invoke a Control Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="bc631-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bc631-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc631-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bc631-106">이 항목에서는 다음 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="bc631-107">대상 애플리케이션에 대해 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 컨트롤 뷰를 검색하여 특정 속성 조건과 일치하는 컨트롤을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="bc631-108">각 컨트롤에 대해 <xref:System.Windows.Automation.AutomationElement> 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="bc631-109"><xref:System.Windows.Automation.InvokePattern> 컨트롤 패턴을 지원하는 검색된 모든 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 요소에서 <xref:System.Windows.Automation.InvokePattern> 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="bc631-110"><xref:System.Windows.Automation.InvokePattern.Invoke%2A> 를 사용하여 클라이언트 이벤트 처리기에서 컨트롤을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc631-111">예제</span><span class="sxs-lookup"><span data-stu-id="bc631-111">Example</span></span>  

 <span data-ttu-id="bc631-112">이 예제에서는 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> 클래스의 <xref:System.Windows.Automation.AutomationElement> 메서드를 사용하여 <xref:System.Windows.Automation.InvokePattern> 개체를 생성하고 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 메서드를 사용하여 컨트롤을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="bc631-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="bc631-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc631-113">See also</span></span>

- [<span data-ttu-id="bc631-114">InvokePattern, ExpandCollapsePattern 및 TogglePattern 샘플</span><span class="sxs-lookup"><span data-stu-id="bc631-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
