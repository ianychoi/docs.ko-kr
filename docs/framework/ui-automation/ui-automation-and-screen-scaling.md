---
title: UI 자동화 및 화면 크기 조정
description: Windows 및 UI 자동화에서 화면 크기 조정을 처리 하는 방법을 읽습니다. DWM은 UI 자동화 클라이언트 앱이 고려해 야 하는 모든 응용 프로그램에 대 한 기본 크기 조정을 수행 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: cf8069f26b85318994aeeb47d42ad28a3a33834a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262530"
---
# <a name="ui-automation-and-screen-scaling"></a><span data-ttu-id="45c32-104">UI 자동화 및 화면 크기 조정</span><span class="sxs-lookup"><span data-stu-id="45c32-104">UI Automation and Screen Scaling</span></span>

> [!NOTE]
> <span data-ttu-id="45c32-105">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="45c32-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45c32-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
<span data-ttu-id="45c32-107">Windows Vista부터 사용자는 dpi (인치당 도트 수) 설정을 변경 하 여 화면에 있는 대부분의 UI (사용자 인터페이스) 요소를 더 크게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-107">Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger.</span></span> <span data-ttu-id="45c32-108">Windows에서는이 기능을 사용할 수 있었지만 이전 버전에서는 응용 프로그램에서 크기 조정을 구현 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-108">Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications.</span></span> <span data-ttu-id="45c32-109">Windows Vista부터 바탕 화면 창 관리자는 자체 크기 조정을 처리 하지 않는 모든 응용 프로그램에 대해 기본 크기 조정을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-109">Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling.</span></span> <span data-ttu-id="45c32-110">UI 자동화 클라이언트 애플리케이션에서는 이 기능을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-110">UI Automation client applications must take this feature into account.</span></span>  
  
<a name="Scaling_in_Windows_Vista"></a>

## <a name="scaling-in-windows-vista"></a><span data-ttu-id="45c32-111">Windows Vista에서 크기 조정</span><span class="sxs-lookup"><span data-stu-id="45c32-111">Scaling in Windows Vista</span></span>  

 <span data-ttu-id="45c32-112">기본 dpi 설정은 96입니다. 즉, 96 픽셀은 1 내의 추상적인 인치 너비 또는 높이를 차지 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-112">The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch.</span></span> <span data-ttu-id="45c32-113">"인치"의 정확한 측정값은 모니터의 크기와 실제 해상도에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-113">The exact measure of an "inch" depends on the size and physical resolution of the monitor.</span></span> <span data-ttu-id="45c32-114">예를 들어, 12인치 너비의 모니터에서 1280픽셀의 수평 해상도의 경우 96픽셀의 가로줄은 1인치의 약 9/10입니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-114">For example, on a monitor 12 inches wide, at a horizontal resolution of 1280 pixels, a horizontal line of 96 pixels extends about 9/10 of an inch.</span></span>  
  
 <span data-ttu-id="45c32-115">Dpi 설정을 변경 하는 것은 화면 해상도를 변경 하는 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-115">Changing the dpi setting is not the same as changing the screen resolution.</span></span> <span data-ttu-id="45c32-116">Dpi 크기 조정을 사용 하는 경우 화면의 실제 픽셀 수는 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-116">With dpi scaling, the number of physical pixels on the screen remains the same.</span></span> <span data-ttu-id="45c32-117">하지만 크기 조정은 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 요소의 크기와 위치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-117">However, scaling is applied to the size and location of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="45c32-118">크기를 조정하지 말라는 메시지가 명시적으로 표시되지 않는 데스크톱 및 애플리케이션에 대해서는 바탕 화면 창 관리자가 이 크기 조정을 자동으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-118">This scaling can be performed automatically by the Desktop Window Manager (DWM) for the desktop and for applications that do not explicitly ask not to be scaled.</span></span>  
  
 <span data-ttu-id="45c32-119">실제로 사용자가 배율 인수를 120 dpi로 설정 하면 화면의 세로 또는 가로 인치가 25% 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-119">In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent.</span></span> <span data-ttu-id="45c32-120">그에 따라 모든 치수가 적절하게 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-120">All dimensions are scaled accordingly.</span></span> <span data-ttu-id="45c32-121">화면 위쪽에서 왼쪽 가장자리까지 애플리케이션 창의 오프셋이 25% 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-121">The offset of an application window from the top and left edges of the screen increases by 25 percent.</span></span> <span data-ttu-id="45c32-122">응용 프로그램 크기 조정을 사용 하 고 응용 프로그램에서 dpi를 인식 하지 못하는 경우 창의 크기는 포함 된 모든 요소의 오프셋과 크기와 함께 동일한 비율로 늘어납니다 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="45c32-122">If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45c32-123">기본적으로, 사용자가 dpi를 120로 설정 하는 경우에는 비 dpi 인식 응용 프로그램에 대 한 크기 조정을 수행 하지 않지만 dpi가 사용자 지정 값 144 이상으로 설정 된 경우에는이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-123">By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher.</span></span> <span data-ttu-id="45c32-124">그러나 사용자는 기본 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-124">However, the user can override the default behavior.</span></span>  
  
 <span data-ttu-id="45c32-125">화면 크기 조정 어떤 방식으로든 화면 좌표와 관련된 애플리케이션에 대한 새로운 문제를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-125">Screen scaling creates new challenges for applications that are concerned in any way with screen coordinates.</span></span> <span data-ttu-id="45c32-126">이제 화면에는 물리적 좌표와 논리적 좌표 두 개가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-126">The screen now contains two coordinate systems: physical and logical.</span></span> <span data-ttu-id="45c32-127">점의 물리적 좌표는 원점의 왼쪽 상단에서의 픽셀 단위의 실제 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-127">The physical coordinates of a point are the actual offset in pixels from the top left of the origin.</span></span> <span data-ttu-id="45c32-128">논리적 좌표는 픽셀 자체의 크기가 조정된 경우 발생되는 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-128">The logical coordinates are the offsets as they would be if the pixels themselves were scaled.</span></span>  
  
 <span data-ttu-id="45c32-129">좌표 (100, 48)에서 단추가 있는 대화 상자를 설계한다고 가정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="45c32-129">Suppose you design a dialog box with a button at coordinates (100, 48).</span></span> <span data-ttu-id="45c32-130">이 대화 상자가 기본 96 dpi로 표시 되 면 단추는 (100, 48)의 물리적 좌표에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-130">When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48).</span></span> <span data-ttu-id="45c32-131">120 dpi에서는 (125, 60)의 물리적 좌표에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-131">At 120 dpi, it is located at physical coordinates of (125, 60).</span></span> <span data-ttu-id="45c32-132">그러나 논리 좌표는 모든 dpi 설정에서 동일 합니다. (100, 48)</span><span class="sxs-lookup"><span data-stu-id="45c32-132">But the logical coordinates are the same at any dpi setting: (100, 48).</span></span>  
  
 <span data-ttu-id="45c32-133">논리 좌표는 dpi 설정에 관계 없이 운영 체제와 응용 프로그램의 동작을 일관적으로 만들기 때문에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-133">Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting.</span></span> <span data-ttu-id="45c32-134">예를 들어, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 은 일반적으로 논리적 좌표를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-134">For example, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normally returns the logical coordinates.</span></span> <span data-ttu-id="45c32-135">대화 상자의 요소 위로 커서를 이동 하면 dpi 설정에 관계 없이 동일한 좌표가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-135">If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting.</span></span> <span data-ttu-id="45c32-136">(100, 100)에서 컨트롤을 그리면 해당 논리적 좌표로 그려지고 모든 dpi 설정에서 동일한 상대적 위치를 차지 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-136">If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.</span></span>  
  
<a name="Scaling_in_UI_Automation_Clients"></a>

## <a name="scaling-in-ui-automation-clients"></a><span data-ttu-id="45c32-137">UI 자동화 클라이언트의 크기 조정</span><span class="sxs-lookup"><span data-stu-id="45c32-137">Scaling in UI Automation Clients</span></span>  

 <span data-ttu-id="45c32-138">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]API는 논리적 좌표를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-138">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates.</span></span> <span data-ttu-id="45c32-139">다음 메서드 및 속성은 물리적 좌표를 반환하거나 매개 변수로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-139">The following methods and properties either return physical coordinates or take them as parameters.</span></span>  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 <span data-ttu-id="45c32-140">기본적으로 96이 아닌 환경에서 실행 되는 UI 자동화 클라이언트 응용 프로그램은 이러한 메서드와 속성에서 올바른 결과를 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-140">By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties.</span></span> <span data-ttu-id="45c32-141">예를 들어, 커서 위치는 논리적 좌표에 있기 때문에 클라이언트가 이러한 좌표를 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> 에 간단히 전달하여 커서 아래에 있는 요소를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-141">For example, because the cursor position is in logical coordinates, the client cannot simply pass these coordinates to <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> to obtain the element that is under the cursor.</span></span> <span data-ttu-id="45c32-142">또한 애플리케이션이 클라이언트 영역 외부에 창을 올바르게 배치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-142">In addition, the application will not be able to correctly place windows outside its client area.</span></span>  
  
 <span data-ttu-id="45c32-143">솔루션은 두 부분으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-143">The solution is in two parts.</span></span>  
  
1. <span data-ttu-id="45c32-144">먼저 클라이언트 응용 프로그램에서 dpi를 인식 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-144">First, make the client application dpi-aware.</span></span> <span data-ttu-id="45c32-145">이렇게 하려면 시작 시 Win32 함수를 호출 `SetProcessDPIAware` 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-145">To do this, call the Win32 function `SetProcessDPIAware` at startup.</span></span> <span data-ttu-id="45c32-146">관리 코드에서, 다음 선언을 통해 이 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-146">In managed code, the following declaration makes this function available.</span></span>  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     <span data-ttu-id="45c32-147">이 함수는 전체 프로세스 dpi를 인식 합니다. 즉, 프로세스에 속하는 모든 창이 실제 크기로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-147">This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled.</span></span> <span data-ttu-id="45c32-148">예를 들어, [형광펜 샘플](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)에서 강조 표시 사각형을 구성 하는 4 개의 창은 논리적 좌표가 아니라 UI 자동화에서 가져온 물리적 좌표에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-148">In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates.</span></span> <span data-ttu-id="45c32-149">샘플이 dpi를 인식 하지 못하는 경우 강조 표시는 데스크톱의 논리적 좌표에 그려지며 96이 아닌 환경에서 잘못 된 배치가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-149">If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.</span></span>  
  
2. <span data-ttu-id="45c32-150">커서 좌표를 가져오려면 Win32 함수를 호출 `GetPhysicalCursorPos` 합니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-150">To get cursor coordinates, call the Win32 function `GetPhysicalCursorPos`.</span></span> <span data-ttu-id="45c32-151">다음 예제에서는 이 함수를 선언하고 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-151">The following example shows how to declare and use this function.</span></span>  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <span data-ttu-id="45c32-152"><xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>는 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="45c32-152">Do not use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="45c32-153">크기가 조정된 환경에서 클라이언트 창 외부에서의 이 속성 동작이 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="45c32-153">The behavior of this property outside client windows in a scaled environment is undefined.</span></span>  
  
 <span data-ttu-id="45c32-154">응용 프로그램에서 dpi를 인식 하지 않는 응용 프로그램과의 직접 크로스 프로세스 통신을 수행 하는 경우, Win32 함수 및를 사용 하 여 논리적 좌표와 물리적 좌표 간을 변환 했을 수 있습니다 `PhysicalToLogicalPoint` `LogicalToPhysicalPoint` .</span><span class="sxs-lookup"><span data-stu-id="45c32-154">If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the Win32 functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c32-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45c32-155">See also</span></span>

- [<span data-ttu-id="45c32-156">Highlighter Sample</span><span class="sxs-lookup"><span data-stu-id="45c32-156">Highlighter Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
