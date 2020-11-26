---
title: WF의 기본 활동
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: 4f2c20c109d67a35ccc9c363c0a3631922161d2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246078"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="249fe-102">WF의 기본 활동</span><span class="sxs-lookup"><span data-stu-id="249fe-102">Primitives Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="249fe-103">에서는 일반적인 작업을 수행하는 데 편리하게 사용할 수 있는 메커니즘이 있는 여러 시스템 제공 활동을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="249fe-104">작업</span><span class="sxs-lookup"><span data-stu-id="249fe-104">Activity</span></span>|<span data-ttu-id="249fe-105">Description</span><span class="sxs-lookup"><span data-stu-id="249fe-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="249fe-106">현재 범위의 변수에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="249fe-107">워크플로가 언로드될 수 있도록 실행 경로 하나를 유휴 상태로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="249fe-108"><xref:System.Activities.ActivityDelegate>에서 파생되어 속성으로 노출되는 대리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="249fe-109">CLR 개체의 public 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="249fe-110">지정한 문자열을 콘솔 또는 지정한 <xref:System.IO.TextWriter> 개체에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="249fe-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
