---
description: '자세한 정보: 애플리케이션 폼 액세스(Visual Basic)'
title: 애플리케이션 폼 액세스
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: dae73700434f9cdbb145ebea605c87c33f7c0c73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797902"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="0204d-103">애플리케이션 폼 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0204d-103">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="0204d-104">`My.Forms` 개체는 애플리케이션 프로젝트에 선언된 각 Windows Form의 인스턴스에 액세스하는 간편한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-104">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="0204d-105">`My.Application` 개체의 속성을 사용하여 애플리케이션의 시작 화면 및 기본 폼에 액세스하고 애플리케이션의 열려 있는 폼 목록을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-105">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="0204d-106">작업</span><span class="sxs-lookup"><span data-stu-id="0204d-106">Tasks</span></span>  

 <span data-ttu-id="0204d-107">다음 표에는 애플리케이션의 양식에 액세스하는 방법을 보여 주는 예제가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-107">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="0204d-108">대상</span><span class="sxs-lookup"><span data-stu-id="0204d-108">To</span></span>|<span data-ttu-id="0204d-109">참조 항목</span><span class="sxs-lookup"><span data-stu-id="0204d-109">See</span></span>|  
|---|---|  
|<span data-ttu-id="0204d-110">애플리케이션의 다른 폼에서 한 폼에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-110">Access one form from another form in an application.</span></span>|[<span data-ttu-id="0204d-111">My.Forms 개체</span><span class="sxs-lookup"><span data-stu-id="0204d-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="0204d-112">애플리케이션의 열려 있는 모든 폼의 제목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-112">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="0204d-113">애플리케이션이 시작될 때 시작 화면을 상태 정보로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0204d-113">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="0204d-114">참조</span><span class="sxs-lookup"><span data-stu-id="0204d-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="0204d-115">My.Forms 개체</span><span class="sxs-lookup"><span data-stu-id="0204d-115">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
