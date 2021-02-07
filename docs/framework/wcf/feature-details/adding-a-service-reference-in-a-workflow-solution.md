---
description: '자세한 정보: 워크플로 솔루션에 서비스 참조 추가'
title: 워크플로 솔루션에 서비스 참조 추가
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: ff54235ce2925bd2596bae68333ce98dc7a2f009
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705319"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="97b01-103">워크플로 솔루션에 서비스 참조 추가</span><span class="sxs-lookup"><span data-stu-id="97b01-103">Add a Service Reference in a Workflow Solution</span></span>

<span data-ttu-id="97b01-104">워크플로 애플리케이션에서 서비스 참조를 추가하는 작업은 일반적인 WCF 애플리케이션과 약간 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-104">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="97b01-105">  >  **서비스 참조** 추가를 선택 하 고 서비스에 대 한 URL을 지정 하면 메타 데이터가 다운로드 되 고 해당 wcf 서비스 또는 wcf 워크플로 서비스를 호출할 수 있는 사용자 지정 작업이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-105">When you select **Add** > **Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call that WCF service or WCF workflow service.</span></span> <span data-ttu-id="97b01-106">서비스 참조를 추가한 후 생성된 활동이 빌드되도록 솔루션을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-106">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="97b01-107">솔루션을 다시 빌드한 후 생성된 활동이 워크플로 디자이너 도구 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-107">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="97b01-108">이는 워크플로 솔루션 내에서 서비스 참조를 추가 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-108">This will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="97b01-109">다음 웹 캐스트는 다른 형식의 프로젝트에서 서비스 참조를 추가 하는 방법을 보여 줍니다. [웹 프로젝트의 워크플로에서 WCF 서비스를 호출](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-109">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).</span></span>

<span data-ttu-id="97b01-110">동일한 작업 이름이 포함된 서비스에 대한 서비스 참조를 둘 이상 추가하면 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-110">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="97b01-111">생성된 활동이 첫 번째 서비스 작업만 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-111">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="97b01-112">이 문제를 해결 하려면 서비스 작업 이름을 다르게 변경 하거나 생성 된 각 작업 내에서 끝점 구성 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97b01-112">To work around this issue, rename the service operations so they are different, or change the endpoint configuration name within each generated activity.</span></span>

## <a name="see-also"></a><span data-ttu-id="97b01-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97b01-113">See also</span></span>

- [<span data-ttu-id="97b01-114">워크플로 서비스</span><span class="sxs-lookup"><span data-stu-id="97b01-114">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="97b01-115">웹 프로젝트의 워크플로에서 WCF 서비스 호출</span><span class="sxs-lookup"><span data-stu-id="97b01-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
