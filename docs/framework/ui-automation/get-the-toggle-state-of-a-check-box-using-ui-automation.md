---
title: UI 자동화를 사용하여 확인란의 전환 상태 가져오기
description: 'Microsoft UI 자동화를 사용 하 여 컨트롤의 설정/해제 상태 (예: 확인란)를 가져오는 방법을 보여 주는 코드 예제를 참조 하세요.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 2ec0cc996461b13d0ddc3453188eeb3287a56be7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276440"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="ce366-103">UI 자동화를 사용하여 확인란의 전환 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="ce366-103">Get the Toggle State of a Check Box Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="ce366-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce366-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ce366-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce366-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ce366-106">이 항목에서는를 사용 하 여 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 컨트롤의 설정/해제 상태를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce366-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce366-107">예제</span><span class="sxs-lookup"><span data-stu-id="ce366-107">Example</span></span>  

 <span data-ttu-id="ce366-108">이 예제에서는 클래스의 메서드를 사용 하 여 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.TogglePattern> 컨트롤에서 개체를 가져오고 해당 속성을 반환 <xref:System.Windows.Automation.ToggleState> 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce366-108">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
