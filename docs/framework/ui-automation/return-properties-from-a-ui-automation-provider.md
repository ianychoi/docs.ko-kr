---
title: UI 자동화 공급자에서 속성 반환
description: UI 자동화 공급자가 .NET의 클라이언트 응용 프로그램에 요소의 속성을 반환할 수 있는 방법을 참조 하세요.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 8269d7d04a67c2a89a28160c0a8bc82bd627749f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250478"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="de88c-103">UI 자동화 공급자에서 속성 반환</span><span class="sxs-lookup"><span data-stu-id="de88c-103">Return Properties from a UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="de88c-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="de88c-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="de88c-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de88c-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="de88c-106">이 항목에는 UI 자동화 공급자가 클라이언트 애플리케이션에 요소의 속성을 반환할 수 있는 방법을 보여주는 샘플 코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de88c-106">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="de88c-107">명시적으로 지원되지 않는 모든 속성의 경우 공급자는 `null` 을 반환해야 합니다(Visual Basic의 경우`Nothing` ).</span><span class="sxs-lookup"><span data-stu-id="de88c-107">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="de88c-108">이렇게 하면 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이 호스트 창 공급자와 같은 다른 소스에서 속성을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de88c-108">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de88c-109">예제</span><span class="sxs-lookup"><span data-stu-id="de88c-109">Example</span></span>  

 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="de88c-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de88c-110">See also</span></span>

- [<span data-ttu-id="de88c-111">UI 자동화 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="de88c-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="de88c-112">서버 쪽 UI 자동화 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="de88c-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
