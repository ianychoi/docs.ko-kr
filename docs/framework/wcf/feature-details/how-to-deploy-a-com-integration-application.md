---
title: '방법: COM+ 통합 애플리케이션 배포'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 5f2e64ed06b98db50259edf8ef307ce430b8be38
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289791"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="105c7-102">방법: COM+ 통합 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="105c7-102">How to: Deploy a COM+ Integration Application</span></span>

<span data-ttu-id="105c7-103">COM+ 통합 애플리케이션을 작성했다면 이를 다른 컴퓨터에 배포해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="105c7-104">이 항목에서는 한 컴퓨터에서 다른 컴퓨터로 COM+ 통합 애플리케이션을 이동하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="105c7-105">COM+ 호스팅 통합 응용 프로그램 이동</span><span class="sxs-lookup"><span data-stu-id="105c7-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="105c7-106">WCF가 두 컴퓨터에 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="105c7-107">컴퓨터 A에서 애플리케이션을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="105c7-108">컴퓨터 B로 애플리케이션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="105c7-109">애플리케이션 루트 디렉터리를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-109">Set the Application Root Directory.</span></span> <span data-ttu-id="105c7-110">규칙에 따라 이는 %PROGRAMFILES%/ComPlus Applications/{AppGUID}입니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="105c7-111">컴퓨터 A에 있는 애플리케이션 루트 디렉터리의 Application.config 및 Application.manifest 파일을 컴퓨터 B의 애플리케이션 루트 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="105c7-112">해당 컴퓨터를 식별하기 위해 컴퓨터 B의 Application.config 파일에서 서비스 엔드포인트 주소를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="105c7-113">예를 들어 `http://machineA/MyService`를 `http://machineB/MyService`로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="105c7-114">웹 호스팅 통합 애플리케이션 이동</span><span class="sxs-lookup"><span data-stu-id="105c7-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="105c7-115">WCF가 두 컴퓨터에 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="105c7-116">컴퓨터 A에서 애플리케이션을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="105c7-117">컴퓨터 B로 애플리케이션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="105c7-118">컴퓨터 B에서 IIS vroot를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="105c7-119">컴퓨터 A의 vroot에 있는 .svc 파일(componentName.svc) 및 Web.config 파일을 컴퓨터 B의 새로 만들어진 vroot로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="105c7-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105c7-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="105c7-120">See also</span></span>

- [<span data-ttu-id="105c7-121">COM + 응용 프로그램과 통합 개요</span><span class="sxs-lookup"><span data-stu-id="105c7-121">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="105c7-122">방법: COM+ 서비스 설정 구성</span><span class="sxs-lookup"><span data-stu-id="105c7-122">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="105c7-123">방법: COM+ 서비스 모델 구성 도구 사용</span><span class="sxs-lookup"><span data-stu-id="105c7-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
