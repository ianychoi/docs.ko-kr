---
title: 클라이언트 쪽 공급자 어셈블리 등록
description: 클라이언트 쪽 UI 자동화 공급자가 포함 된 DLL을 등록 하는 방법을 보여 주는 예제를 검토 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 1c6f7685b796b544925207a22679e6a4da455844
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250465"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="a1920-103">클라이언트 쪽 공급자 어셈블리 등록</span><span class="sxs-lookup"><span data-stu-id="a1920-103">Register a Client-Side Provider Assembly</span></span>

> [!NOTE]
> <span data-ttu-id="a1920-104">이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1920-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a1920-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1920-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a1920-106">이 항목에서는 클라이언트 쪽 UI 자동화 공급자가 포함된 DLL을 등록하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1920-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1920-107">예제</span><span class="sxs-lookup"><span data-stu-id="a1920-107">Example</span></span>  

 <span data-ttu-id="a1920-108">다음 예제에서는 콘솔 창에 대한 공급자가 포함된 어셈블리를 등록하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1920-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="a1920-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1920-109">See also</span></span>

- [<span data-ttu-id="a1920-110">클라이언트 쪽 UI 자동화 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="a1920-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
