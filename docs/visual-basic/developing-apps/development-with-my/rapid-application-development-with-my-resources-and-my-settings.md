---
description: '자세한 정보: My.Resources 및 My.Settings를 사용한 신속한 애플리케이션 개발(Visual Basic)'
title: My.Resources 및 My.Settings를 사용한 신속한 응용 프로그램 개발
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 38846b3a6ac273306f588ad8b043d7f35f7230a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797928"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="a6d16-103">My.Resources 및 My.Settings를 사용한 신속한 애플리케이션 개발(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6d16-103">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="a6d16-104">`My.Resources` 개체는 애플리케이션의 리소스에 대한 액세스를 제공하고 애플리케이션의 리소스를 동적으로 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-104">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="a6d16-105">리소스 검색</span><span class="sxs-lookup"><span data-stu-id="a6d16-105">Retrieving Resources</span></span>  

 <span data-ttu-id="a6d16-106">`My.Resources` 개체를 통해 오디오 파일, 아이콘, 이미지 및 문자열과 같은 여러 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-106">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="a6d16-107">예를 들어 애플리케이션의 문화권별 리소스 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-107">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="a6d16-108">다음 예제에서는 양식의 아이콘을 애플리케이션의 리소스 파일에 저장된 `Form1Icon`이라는 아이콘으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-108">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="a6d16-109">`My.Resources` 개체는 글로벌 리소스만 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-109">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="a6d16-110">양식과 관련된 리소스 파일에 대한 액세스 권한은 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-110">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="a6d16-111">양식에서 양식 리소스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-111">Access the form resources from the form.</span></span>  
  
 <span data-ttu-id="a6d16-112">마찬가지로 `My.Settings` 개체는 애플리케이션 설정에 대한 액세스를 제공하며 애플리케이션에 대한 속성 설정과 기타 정보를 동적으로 저장하고 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d16-112">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="a6d16-113">자세한 내용은 [My.Resources 개체](../../language-reference/objects/my-resources-object.md) 및 [My.Settings 개체](../../language-reference/objects/my-settings-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6d16-113">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d16-114">참조</span><span class="sxs-lookup"><span data-stu-id="a6d16-114">See also</span></span>

- [<span data-ttu-id="a6d16-115">My.Resources 개체</span><span class="sxs-lookup"><span data-stu-id="a6d16-115">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="a6d16-116">My.Settings 개체</span><span class="sxs-lookup"><span data-stu-id="a6d16-116">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="a6d16-117">애플리케이션 설정 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6d16-117">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
