---
title: Databricks에 .NET for Apache Spark 애플리케이션 배포
description: Databricks에 .NET for Apache Spark 애플리케이션을 배포하는 방법을 살펴봅니다.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d17fd5002d47dcde804cb43fc27edb2c2c9be595
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688152"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="680a7-103">자습서: Databricks에 .NET for Apache Spark 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="680a7-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="680a7-104">이 자습서에서는 원 클릭 설정, 간소화된 워크플로 및 협업을 가능하게 하는 대화형 작업 영역이 포함된 Apache Spark 기반 분석 플랫폼인 Azure Databricks를 통해 클라우드에 앱을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="680a7-105">이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="680a7-106">Azure Databricks 작업 영역 만들기</span><span class="sxs-lookup"><span data-stu-id="680a7-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="680a7-107">.NET for Apache Spark 앱 게시</span><span class="sxs-lookup"><span data-stu-id="680a7-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="680a7-108">Spark 작업 및 Spark 클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="680a7-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="680a7-109">Spark 클러스터에서 앱 실행</span><span class="sxs-lookup"><span data-stu-id="680a7-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="680a7-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="680a7-110">Prerequisites</span></span>

<span data-ttu-id="680a7-111">시작하기 전에 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="680a7-112">Azure 계정이 없으면 [체험 계정](https://azure.microsoft.com/free/dotnet/)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="680a7-113">[Azure Portal](https://portal.azure.com/)에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="680a7-114">[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)(.NET for Apache Spark - 10분 이내에 시작하기) 자습서를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="680a7-115">Azure Databricks 작업 영역 만들기</span><span class="sxs-lookup"><span data-stu-id="680a7-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="680a7-116">이 자습서는 **Azure 평가판 구독** 을 사용하여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="680a7-117">무료 계정이 있는 경우 프로필로 이동하고 구독을 **종량제** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="680a7-118">자세한 내용은 [Azure 체험 계정](https://azure.microsoft.com/free/dotnet/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="680a7-118">For more information, see [Azure free account](https://azure.microsoft.com/free/dotnet/).</span></span> <span data-ttu-id="680a7-119">그런 다음 [지출 한도를 제거](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)하고 해당 지역의 vCPU에 대한 [할당량 증가를 요청](/azure/azure-supportability/resource-manager-core-quotas-request)합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-119">Then, [remove the spending limit](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="680a7-120">Azure Databricks 작업 영역을 만드는 경우 **평가판(프리미엄-14일 무료 DBU)** 가격 책정 계층을 선택하여 14일간 무료 프리미엄 Azure Databricks DBU를 위한 작업 영역 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="680a7-121">이 섹션에서는 Azure Portal을 사용하여 Azure Databricks 작업 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="680a7-122">Azure Portal에서 **리소스 만들기** > **분석** > **Azure Databricks** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Azure Portal에서 Azure Databricks 리소스 만들기](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="680a7-124">**Azure Databricks 서비스** 아래에서 Databricks 작업 영역을 만들기 위한 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="680a7-125">속성</span><span class="sxs-lookup"><span data-stu-id="680a7-125">Property</span></span>  |<span data-ttu-id="680a7-126">설명</span><span class="sxs-lookup"><span data-stu-id="680a7-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="680a7-127">**작업 영역 이름**</span><span class="sxs-lookup"><span data-stu-id="680a7-127">**Workspace name**</span></span>     | <span data-ttu-id="680a7-128">Databricks 작업 영역에 대한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="680a7-129">**구독**</span><span class="sxs-lookup"><span data-stu-id="680a7-129">**Subscription**</span></span>     | <span data-ttu-id="680a7-130">드롭다운에서 Azure 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="680a7-131">**리소스 그룹**</span><span class="sxs-lookup"><span data-stu-id="680a7-131">**Resource group**</span></span>     | <span data-ttu-id="680a7-132">새 리소스 그룹을 만들지, 아니면 기존 그룹을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="680a7-133">리소스 그룹은 Azure 솔루션에 관련된 리소스를 보유하는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="680a7-134">자세한 내용은 [Azure Resource Manager 개요](/azure/azure-resource-manager/resource-group-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="680a7-134">For more information, see [Azure Resource Group overview](/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="680a7-135">**위치**</span><span class="sxs-lookup"><span data-stu-id="680a7-135">**Location**</span></span>     | <span data-ttu-id="680a7-136">기본 지역을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-136">Select your preferred region.</span></span> <span data-ttu-id="680a7-137">사용 가능한 지역에 대한 자세한 내용은 [지역별 사용 가능한 Azure 서비스](https://azure.microsoft.com/regions/services/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="680a7-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="680a7-138">**가격 책정 계층**</span><span class="sxs-lookup"><span data-stu-id="680a7-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="680a7-139">**표준**, **프리미엄** 또는 **평가판** 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="680a7-140">이러한 계층에 대한 자세한 내용은 [Databricks 가격 페이지](https://azure.microsoft.com/pricing/details/databricks/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="680a7-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="680a7-141">**Virtual Network**</span><span class="sxs-lookup"><span data-stu-id="680a7-141">**Virtual Network**</span></span>     |   <span data-ttu-id="680a7-142">아니요</span><span class="sxs-lookup"><span data-stu-id="680a7-142">No</span></span>       |

3. <span data-ttu-id="680a7-143">**만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-143">Select **Create**.</span></span> <span data-ttu-id="680a7-144">작업 영역 생성에는 몇 분 정도가 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="680a7-145">작업 영역을 만드는 동안 **알림** 에서 배포 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="680a7-146">Azure Databricks 도구 설치</span><span class="sxs-lookup"><span data-stu-id="680a7-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="680a7-147">**Databricks CLI** 를 사용하여 Azure Databricks 클러스터에 연결하고 로컬 머신에서 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="680a7-148">Databricks 클러스터는 DBFS(Databricks 파일 시스템)를 통해 파일에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="680a7-149">Databricks CLI를 사용하려면 Python 3.6 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="680a7-150">Python이 이미 설치되어 있는 경우 이 단계를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="680a7-151">**Windows:**</span><span class="sxs-lookup"><span data-stu-id="680a7-151">**For Windows:**</span></span>

   <span data-ttu-id="680a7-152">[Windows용 Python을 다운로드](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-152">[Download Python for Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)</span></span>

   <span data-ttu-id="680a7-153">**Linux:** 대부분의 Linux 배포에는 Python이 사전 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="680a7-154">다음 명령을 실행하여 설치된 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="680a7-155">pip를 사용하여 Databricks CLI를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="680a7-156">Python 3.4 이상에는 기본적으로 pip가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="680a7-157">Python 3의 pip3을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="680a7-158">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="680a7-159">Databricks CLI를 설치한 후 새 명령 프롬프트를 열고 `databricks` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="680a7-160">**'databricks'가 내부 또는 외부 명령으로 인식되지 않음 오류** 가 표시되면 새 명령 프롬프트를 열었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="680a7-161">Azure Databricks 설정</span><span class="sxs-lookup"><span data-stu-id="680a7-161">Set up Azure Databricks</span></span>

<span data-ttu-id="680a7-162">이제 Databricks CLI가 설치되었으므로 인증 정보를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="680a7-163">Databricks CLI 명령 `databricks configure --token`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="680a7-164">구성 명령을 실행하면 호스트를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="680a7-165">호스트 URL은 `https://<Location>.azuredatabricks.net` 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-165">Your host URL uses the format: `https://<Location>.azuredatabricks.net`.</span></span> <span data-ttu-id="680a7-166">예를 들어 Azure Databricks 서비스를 만드는 동안 **eastus2** 를 선택한 경우 호스트는 `https://eastus2.azuredatabricks.net`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be `https://eastus2.azuredatabricks.net`.</span></span>

3. <span data-ttu-id="680a7-167">호스트를 입력하면 토큰을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="680a7-168">Azure Portal에서 **작업 영역 시작** 을 선택하여 Azure Databricks 작업 영역을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Azure Databricks 작업 영역 시작](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="680a7-170">작업 영역의 홈페이지에서 **사용자 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks 작업 영역의 사용자 설정](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="680a7-172">사용자 설정 페이지에서 새 토큰을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="680a7-173">생성된 토큰을 복사하여 명령 프롬프트에 다시 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Azure Databricks 작업 영역에서 새 액세스 토큰 생성](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="680a7-175">이제 만들어진 Azure Databricks 클러스터에 액세스하고 파일을 DBFS에 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="680a7-176">작업자 종속성 다운로드</span><span class="sxs-lookup"><span data-stu-id="680a7-176">Download worker dependencies</span></span>

> [!Note]
> <span data-ttu-id="680a7-177">Azure 및 AWS Databricks는 Linux 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-177">Azure and AWS Databricks are Linux-based.</span></span> <span data-ttu-id="680a7-178">따라서 Databricks에 앱을 배포하려면 앱이 .NET Standard와 호환되며 .NET Core 컴파일러를 사용하여 앱을 컴파일하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-178">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

1. <span data-ttu-id="680a7-179">Microsoft.Spark.Worker를 통해 Apache Spark는 사용자가 작성했을 수 있는 UDF(사용자 정의 함수) 등의 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-179">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="680a7-180">[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-180">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="680a7-181">*install-worker.sh* 는 .NET for Apache Spark 종속 파일을 클러스터의 노드에 복사하는 데 사용할 수 있는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-181">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="680a7-182">로컬 컴퓨터에 **install-worker.sh** 라는 새 파일을 만들고 GitHub에 있는 [install-worker.sh 콘텐츠](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-182">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="680a7-183">*db-init.sh* 는 Databricks Spark 클러스터에 종속성을 설치하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-183">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="680a7-184">로컬 컴퓨터에 **db-init.sh** 라는 새 파일을 만들고 GitHub에 있는 [db-init.sh 콘텐츠](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-184">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="680a7-185">방금 만든 파일에서 `DOTNET_SPARK_RELEASE` 변수를 `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-185">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz`.</span></span> <span data-ttu-id="680a7-186">*db-init.sh* 파일의 나머지 내용은 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-186">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="680a7-187">Windows를 사용하는 경우 *install-worker.sh* 및 *db-init.sh* 스크립트의 줄 끝이 Unix 스타일(LF)인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-187">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="680a7-188">Notepad++, Atom 등의 텍스트 편집기를 통해 줄 끝을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-188">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="680a7-189">앱 게시</span><span class="sxs-lookup"><span data-stu-id="680a7-189">Publish your app</span></span>

<span data-ttu-id="680a7-190">[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)(.NET for Apache Spark - 10분 이내에 시작하기) 자습서에서 만든 *mySparkApp* 을 게시하여 Spark 클러스터가 앱을 실행하는 데 필요한 모든 파일에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-190">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="680a7-191">다음 명령을 실행하여 *mySparkApp* 을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-191">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="680a7-192">다음 작업을 수행하여 게시된 앱 파일을 압축하면 Databricks Spark 클러스터에 쉽게 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="680a7-193">**Windows:**</span><span class="sxs-lookup"><span data-stu-id="680a7-193">**On Windows:**</span></span>

   <span data-ttu-id="680a7-194">mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-194">Navigate to mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64.</span></span> <span data-ttu-id="680a7-195">**게시** 폴더를 마우스 오른쪽 단추로 클릭하고 **보내기 > 압축(zip) 폴더** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="680a7-196">새 폴더의 이름을 **publish.zip** 으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="680a7-197">**Linux에서는 다음 명령을 실행합니다.**</span><span class="sxs-lookup"><span data-stu-id="680a7-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="680a7-198">파일 업로드</span><span class="sxs-lookup"><span data-stu-id="680a7-198">Upload files</span></span>

<span data-ttu-id="680a7-199">이 섹션에서는 클라우드에서 앱을 실행하는 데 필요한 모든 파일이 클러스터에 포함되도록 여러 개의 파일을 DBFS에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="680a7-200">DBFS에 파일을 업로드할 때는 항상 파일이 있는 컴퓨터의 디렉터리에서 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="680a7-201">다음 명령을 실행하여 *db-init.sh*, *install-worker.sh* 및 *Microsoft.Spark.Worker* 를 DBFS에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz
   ```

2. <span data-ttu-id="680a7-202">다음 명령을 실행하여 클러스터에서 앱을 실행하는 데 필요한 나머지 파일(압축된 게시 폴더, *input.txt* 및 *microsoft-spark-2-4_2.11-1.0.0.jar*)을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2-4_2.11-1.0.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2-4_2.11-1.0.0.jar dbfs:/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="680a7-203">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="680a7-203">Create a job</span></span>

<span data-ttu-id="680a7-204">.NET for Apache Spark 작업을 실행하는 데 사용하는 명령인 **spark-submit** 을 실행하는 작업을 통해 Azure Databricks에서 앱이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="680a7-205">Azure Databricks 작업 영역에서 **작업** 아이콘, **+ 작업 만들기** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Azure Databricks 작업 만들기](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="680a7-207">작업 제목을 선택한 다음, **spark-submit 구성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Databricks 작업에 대해 spark-submit 구성](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="680a7-209">작업 구성에 다음 매개 변수를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="680a7-210">**확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="680a7-211">클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="680a7-211">Create a cluster</span></span>

1. <span data-ttu-id="680a7-212">작업으로 이동한 다음 **편집** 을 선택하여 작업 클러스터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="680a7-213">클러스터를 **Spark 2.4.1** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="680a7-214">**고급 옵션** > **Init 스크립트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="680a7-215">Init 스크립트 경로를 `dbfs:/spark-dotnet/db-init.sh`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Azure Databricks에서 Spark 클러스터 구성](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="680a7-217">**확인** 을 선택하여 클러스터 설정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="680a7-218">앱 실행</span><span class="sxs-lookup"><span data-stu-id="680a7-218">Run your app</span></span>

1. <span data-ttu-id="680a7-219">작업으로 이동한 다음 **지금 실행** 을 선택하여 새로 구성된 Spark 클러스터에서 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="680a7-220">작업 클러스터를 만드는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="680a7-221">클러스터를 만들고 나면 작업이 제출되고 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="680a7-222">왼쪽 메뉴에서 **클러스터** 를 선택한 다음, 작업의 이름과 실행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="680a7-223">**드라이버 로그** 를 선택하여 작업의 출력을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="680a7-224">앱 실행이 완료되면 시작 로컬 실행과 동일한 단어 개수 테이블이 표준 출력 콘솔에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks 작업 출력 테이블](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="680a7-226">축하합니다. Azure Databricks에서 첫 번째 .NET for Apache Spark 애플리케이션을 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-226">Congratulations, you've run your first .NET for Apache Spark application in Azure Databricks!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="680a7-227">리소스 정리</span><span class="sxs-lookup"><span data-stu-id="680a7-227">Clean up resources</span></span>

<span data-ttu-id="680a7-228">Databricks 작업 영역이 더 이상 필요하지 않은 경우 Azure Portal에서 Azure Databricks 리소스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="680a7-229">또한 리소스 그룹 이름을 선택하여 리소스 그룹 페이지를 연 다음, **리소스 그룹 삭제** 를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="680a7-230">다음 단계</span><span class="sxs-lookup"><span data-stu-id="680a7-230">Next steps</span></span>

<span data-ttu-id="680a7-231">이 자습서에서는 Databricks에 .NET for Apache Spark 애플리케이션을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="680a7-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="680a7-232">Databricks에 대해 자세히 알아보려면 Azure Databricks 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="680a7-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="680a7-233">Azure Databricks 설명서</span><span class="sxs-lookup"><span data-stu-id="680a7-233">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
