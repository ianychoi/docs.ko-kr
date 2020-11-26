---
title: Azure HDInsight에 .NET for Apache Spark 애플리케이션 배포
description: HDInsight에 .NET for Apache Spark 애플리케이션을 배포하는 방법을 살펴봅니다.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f7a3b0c0d972d5cb6dbc6eea818fe794c5060eae
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687912"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="d2dec-103">자습서: Azure HDInsight에 .NET for Apache Spark 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="d2dec-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="d2dec-104">이 자습서에서는 Azure HDInsight 클러스터를 통해 .NET for Apache Spark 앱을 클라우드에 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="d2dec-105">Hdinsight의 Spark 클러스터는 Azure Storage 및 Azure Data Lake Storage와 호환되므로, HDInsight를 사용하면 Azure에서 Spark 클러스터를 보다 쉽게 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="d2dec-106">이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d2dec-107">Azure Storage Explorer를 사용하여 해당 스토리지 계정 액세스</span><span class="sxs-lookup"><span data-stu-id="d2dec-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="d2dec-108">Azure HDInsight 클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="d2dec-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="d2dec-109">.NET for Apache Spark 앱 게시</span><span class="sxs-lookup"><span data-stu-id="d2dec-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="d2dec-110">HDInsight 스크립트 동작 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="d2dec-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="d2dec-111">HDInsight 클러스터에서 .NET for Apache Spark 앱 실행</span><span class="sxs-lookup"><span data-stu-id="d2dec-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2dec-112">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d2dec-112">Prerequisites</span></span>

<span data-ttu-id="d2dec-113">시작하기 전에 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="d2dec-114">Azure 구독이 아직 없는 경우 [체험 계정](https://azure.microsoft.com/free/dotnet/)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="d2dec-115">[Azure Portal](https://portal.azure.com/)에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="d2dec-116">[Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409) 또는 [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) 컴퓨터에 Azure Storage Explorer를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="d2dec-117">[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)(.NET for Apache Spark - 10분 이내에 시작하기) 자습서를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="d2dec-118">해당 스토리지 계정 액세스</span><span class="sxs-lookup"><span data-stu-id="d2dec-118">Access your storage accounts</span></span>

1. <span data-ttu-id="d2dec-119">Azure Storage Explorer를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="d2dec-120">왼쪽 메뉴에서 **계정 추가** 를 선택하고 Azure 계정에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Storage Explorer에서 Azure 계정에 로그인합니다.](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="d2dec-122">로그인하면 보유한 모든 스토리지 계정과 해당 스토리지 계정에 업로드한 모든 리소스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="d2dec-123">HDInsight 클러스터 만들기</span><span class="sxs-lookup"><span data-stu-id="d2dec-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2dec-124">HDInsight 클러스터에 대한 청구는 사용하지 않는 경우에도 분 단위로 비례 배분됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="d2dec-125">사용한 후에 클러스터를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="d2dec-126">자세한 내용은 이 자습서의 [리소스 정리](#clean-up-resources) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2dec-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="d2dec-127">[Azure Portal](https://portal.azure.com)을 방문합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="d2dec-128">**+ 리소스 만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="d2dec-129">**Analytics** 범주에서 **HDInsight** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Azure Portal에서 HDInsight 리소스 만들기](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="d2dec-131">**기본** 에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="d2dec-132">속성</span><span class="sxs-lookup"><span data-stu-id="d2dec-132">Property</span></span>  |<span data-ttu-id="d2dec-133">설명</span><span class="sxs-lookup"><span data-stu-id="d2dec-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="d2dec-134">구독</span><span class="sxs-lookup"><span data-stu-id="d2dec-134">Subscription</span></span>  | <span data-ttu-id="d2dec-135">드롭다운에서 활성 Azure 구독 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="d2dec-136">리소스 그룹</span><span class="sxs-lookup"><span data-stu-id="d2dec-136">Resource group</span></span> | <span data-ttu-id="d2dec-137">새 리소스 그룹을 만들지, 아니면 기존 그룹을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="d2dec-138">리소스 그룹은 Azure 솔루션에 관련된 리소스를 보유하는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="d2dec-139">클러스터 이름</span><span class="sxs-lookup"><span data-stu-id="d2dec-139">Cluster name</span></span> | <span data-ttu-id="d2dec-140">HDInsight Spark 클러스터에 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="d2dec-141">위치</span><span class="sxs-lookup"><span data-stu-id="d2dec-141">Location</span></span>   | <span data-ttu-id="d2dec-142">리소스 그룹의 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-142">Select a location for the resource group.</span></span> <span data-ttu-id="d2dec-143">템플릿에서는 기본 클러스터 스토리지뿐만 아니라 클러스터를 만드는 데 이 위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="d2dec-144">클러스터 유형</span><span class="sxs-lookup"><span data-stu-id="d2dec-144">Cluster type</span></span>| <span data-ttu-id="d2dec-145">클러스터 유형으로 **Spark** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="d2dec-146">클러스터 버전</span><span class="sxs-lookup"><span data-stu-id="d2dec-146">Cluster version</span></span>|<span data-ttu-id="d2dec-147">클러스터 유형을 선택하면 이 필드가 기본 버전으로 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="d2dec-148">Spark 2.3 또는 2.4 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="d2dec-149">클러스터 로그인 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="d2dec-149">Cluster login username</span></span>| <span data-ttu-id="d2dec-150">클러스터 로그인 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-150">Enter the cluster login username.</span></span>  <span data-ttu-id="d2dec-151">기본 이름은 *admin* 입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="d2dec-152">클러스터 로그인 암호</span><span class="sxs-lookup"><span data-stu-id="d2dec-152">Cluster login password</span></span>| <span data-ttu-id="d2dec-153">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-153">Enter any login password.</span></span> |
    |<span data-ttu-id="d2dec-154">SSH(보안 셸) 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="d2dec-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="d2dec-155">SSH 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-155">Enter the SSH username.</span></span> <span data-ttu-id="d2dec-156">기본적으로 이 계정에는 *클러스터 로그인 사용자 이름* 계정과 동일한 암호를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="d2dec-157">완료되면 **다음: Storage >>** 를 선택하여 **Storage** 페이지를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="d2dec-158">**스토리지** 에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="d2dec-159">속성</span><span class="sxs-lookup"><span data-stu-id="d2dec-159">Property</span></span>  |<span data-ttu-id="d2dec-160">설명</span><span class="sxs-lookup"><span data-stu-id="d2dec-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="d2dec-161">기본 스토리지 유형</span><span class="sxs-lookup"><span data-stu-id="d2dec-161">Primary storage type</span></span>|<span data-ttu-id="d2dec-162">기본값 **Azure Storage** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="d2dec-163">선택 방법</span><span class="sxs-lookup"><span data-stu-id="d2dec-163">Selection method</span></span>|<span data-ttu-id="d2dec-164">기본값 **목록에서 선택** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="d2dec-165">기본 스토리지 계정</span><span class="sxs-lookup"><span data-stu-id="d2dec-165">Primary storage account</span></span>|<span data-ttu-id="d2dec-166">구독과 해당 구독 내의 활성 스토리지 계정 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="d2dec-167">컨테이너</span><span class="sxs-lookup"><span data-stu-id="d2dec-167">Container</span></span>|<span data-ttu-id="d2dec-168">이 컨테이너는 클러스터가 클라우드에서 앱을 실행하기 위해 파일을 찾는 해당 스토리지 계정의 특정 Blob 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="d2dec-169">사용 가능한 이름을 임의로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="d2dec-170">**검토 + 만들기** 에서 **만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="d2dec-171">클러스터를 만드는 데 약 20분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="d2dec-172">클러스터를 만들어야 다음 단계를 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="d2dec-173">앱 게시</span><span class="sxs-lookup"><span data-stu-id="d2dec-173">Publish your app</span></span>

<span data-ttu-id="d2dec-174">[.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)(.NET for Apache Spark - 10분 이내에 시작하기) 자습서에서 만든 *mySparkApp* 을 게시하여 Spark 클러스터가 앱을 실행하는 데 필요한 모든 파일에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="d2dec-175">다음 명령을 실행하여 *mySparkApp* 을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="d2dec-176">**Windows:**</span><span class="sxs-lookup"><span data-stu-id="d2dec-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r win-x64
   ```

   <span data-ttu-id="d2dec-177">**Linux:**</span><span class="sxs-lookup"><span data-stu-id="d2dec-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="d2dec-178">다음 작업을 수행하여 게시된 앱 파일을 압축하면 HDInsight 클러스터에 쉽게 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span> <span data-ttu-id="d2dec-179">예를 들어 1단계의 결과로 생성된 게시 폴더의 콘텐츠를 *publish.zip* 으로 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-179">Zip the contents of the publish folder, *publish.zip* for example, that was created as a result of Step 1.</span></span> <span data-ttu-id="d2dec-180">모든 어셈블리는 ZIP 파일의 첫 번째 계층에 있어야 하며 중간 폴더 계층은 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-180">All the assemblies should be in the first layer of the ZIP file and there should be no intermediate folder layer.</span></span> <span data-ttu-id="d2dec-181">즉, *publish.zip* 의 압축을 풀면 모든 어셈블리가 현재 작업 디렉터리로 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-181">This means when you unzip *publish.zip*, all assemblies are extracted into your current working directory.</span></span>

   <span data-ttu-id="d2dec-182">**Windows:**</span><span class="sxs-lookup"><span data-stu-id="d2dec-182">**On Windows:**</span></span>

   <span data-ttu-id="d2dec-183">7-Zip 또는 WinZip과 같은 추출 프로그램을 사용하여 게시된 모든 이진 파일로 bin 디렉터리에 파일을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-183">Use an extraction program, like 7-Zip or WinZip, to extract the file into the bin directory with all the published binaries.</span></span>

   <span data-ttu-id="d2dec-184">**Linux에서는 다음 명령을 실행합니다.**</span><span class="sxs-lookup"><span data-stu-id="d2dec-184">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="d2dec-185">Azure에 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="d2dec-185">Upload files to Azure</span></span>

<span data-ttu-id="d2dec-186">Azure Storage Explorer를 사용하여 클러스터 스토리지로 선택한 Blob 컨테이너에 다음 5개 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-186">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="d2dec-187">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="d2dec-187">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="d2dec-188">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="d2dec-188">install-worker.sh</span></span>
* <span data-ttu-id="d2dec-189">publish.zip</span><span class="sxs-lookup"><span data-stu-id="d2dec-189">publish.zip</span></span>
* <span data-ttu-id="d2dec-190">microsoft-spark-2-4_2.11-1.0.0.jar</span><span class="sxs-lookup"><span data-stu-id="d2dec-190">microsoft-spark-2-4_2.11-1.0.0.jar</span></span>
* <span data-ttu-id="d2dec-191">input.txt</span><span class="sxs-lookup"><span data-stu-id="d2dec-191">input.txt</span></span>

1. <span data-ttu-id="d2dec-192">Azure Storage Explorer를 열고 왼쪽 메뉴에서 해당 스토리지 계정으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-192">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="d2dec-193">해당 스토리지 계정의 **Blob 컨테이너** 에서 클러스터의 Blob 컨테이너로 드릴다운합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-193">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="d2dec-194">*Microsoft.Spark.Worker* 를 통해 Apache Spark는 사용자가 작성했을 수 있는 UDF(사용자 정의 함수) 등의 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-194">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="d2dec-195">[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-195">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span> <span data-ttu-id="d2dec-196">Azure Storage Explorer에서 **업로드** 를 선택하여 작업자를 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-196">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Azure Storage Explorer에 파일 업로드](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="d2dec-198">*install-worker.sh* 는 .NET for Apache Spark 종속 파일을 클러스터의 노드에 복사하는 데 사용할 수 있는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-198">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="d2dec-199">로컬 컴퓨터에 **install-worker.sh** 라는 새 파일을 만들고 GitHub에 있는 [install-worker.sh 콘텐츠](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-199">Create a new file named **install-worker.sh** in your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="d2dec-200">Blob 컨테이너에 *install-worker.sh* 를 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-200">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="d2dec-201">클러스터에는 앱의 게시된 파일이 포함된 *publish.zip* 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-201">Your cluster needs the *publish.zip* file that contains your app's published files.</span></span> <span data-ttu-id="d2dec-202">게시된 폴더 **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** 로 이동하여 **publish.zip** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-202">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="d2dec-203">Blob 컨테이너에 *publish.zip* 을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-203">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="d2dec-204">클러스터에는 jar로 패키지된 애플리케이션 코드가 필요합니다. 이 코드는 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget의 일부로 포함되고 앱의 빌드 출력 디렉터리에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-204">Your cluster needs the application code that is packaged as a jar, included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget and colocated in your app's build output directory.</span></span> <span data-ttu-id="d2dec-205">게시된 폴더 **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64** 로 이동하여 **microsoft-spark-2-4_2.11-1.0.0.jar** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-205">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **microsoft-spark-2-4_2.11-1.0.0.jar**.</span></span> <span data-ttu-id="d2dec-206">Blob 컨테이너에 jar 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-206">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="d2dec-207">Spark 2.3.x, 2.4.x, 3.0.x 버전에 따라 여러 개의 .jar 파일이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-207">There may be multiple .jar files (for versions 2.3.x, 2.4.x and 3.0.x of Spark).</span></span> <span data-ttu-id="d2dec-208">클러스터를 만드는 동안 선택한 Spark 버전과 일치하는 .jar 파일을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-208">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="d2dec-209">예를 들어 클러스터를 만드는 동안 Spark 2.4를 선택한 경우 *microsoft-spark-2-4_2.11-1.0.0.jar* 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-209">For example, choose *microsoft-spark-2-4_2.11-1.0.0.jar* if you chose Spark 2.4 during cluster creation.</span></span>

6. <span data-ttu-id="d2dec-210">클러스터에 앱에 대한 입력이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-210">Your cluster needs the input to your app.</span></span> <span data-ttu-id="d2dec-211">**mySparkApp** 디렉터리로 이동하여 **input.txt** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-211">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="d2dec-212">Blob 컨테이너의 **user/sshuser** 디렉터리에 입력 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-212">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="d2dec-213">ssh를 통해 클러스터에 연결하며, 클러스터는 이 폴더에서 해당 입력을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-213">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="d2dec-214">*input.txt* 파일은 특정 디렉터리로 업로드되는 유일한 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-214">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="d2dec-215">HDInsight 스크립트 동작 실행</span><span class="sxs-lookup"><span data-stu-id="d2dec-215">Run the HDInsight script action</span></span>

<span data-ttu-id="d2dec-216">클러스터가 실행 중이고 Azure에 파일을 업로드했으면, 클러스터에서 **install-worker.sh** 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-216">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="d2dec-217">Azure Portal에서 해당 HDInsight Spark 클러스터로 이동한 다음, **스크립트 동작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-217">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="d2dec-218">**+ 새로운 항목 제출** 을 선택하고 다음 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-218">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="d2dec-219">속성</span><span class="sxs-lookup"><span data-stu-id="d2dec-219">Property</span></span>  |<span data-ttu-id="d2dec-220">설명</span><span class="sxs-lookup"><span data-stu-id="d2dec-220">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="d2dec-221">스크립트 유형</span><span class="sxs-lookup"><span data-stu-id="d2dec-221">Script type</span></span> |<span data-ttu-id="d2dec-222">사용자 지정</span><span class="sxs-lookup"><span data-stu-id="d2dec-222">Custom</span></span>|
   | <span data-ttu-id="d2dec-223">이름</span><span class="sxs-lookup"><span data-stu-id="d2dec-223">Name</span></span> | <span data-ttu-id="d2dec-224">작업자 설치</span><span class="sxs-lookup"><span data-stu-id="d2dec-224">Install Worker</span></span>|
   | <span data-ttu-id="d2dec-225">Bash 스크립트 URI</span><span class="sxs-lookup"><span data-stu-id="d2dec-225">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="d2dec-226">이 URI를 확인하려면 Azure Storage Explorer에서 install-worker.sh를 마우스 오른쪽 단추로 클릭하고 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-226">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="d2dec-227">노드 유형</span><span class="sxs-lookup"><span data-stu-id="d2dec-227">Node type(s)</span></span>| <span data-ttu-id="d2dec-228">작업자</span><span class="sxs-lookup"><span data-stu-id="d2dec-228">Worker</span></span>|
   | <span data-ttu-id="d2dec-229">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d2dec-229">Parameters</span></span> | <span data-ttu-id="d2dec-230">azure</span><span class="sxs-lookup"><span data-stu-id="d2dec-230">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz </br> <span data-ttu-id="d2dec-231">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="d2dec-231">/usr/local/bin</span></span>

3. <span data-ttu-id="d2dec-232">**만들기** 를 선택하여 스크립트를 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-232">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="d2dec-233">앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-233">Run your app</span></span>

1. <span data-ttu-id="d2dec-234">Azure Portal에서 해당 HDInsight Spark 클러스터로 이동한 다음, **SSH + 클러스터 로그인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-234">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="d2dec-235">ssh 로그인 정보를 복사하고 터미널에 로그인을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-235">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="d2dec-236">클러스터를 만드는 동안 설정한 암호를 사용하여 클러스터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-236">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="d2dec-237">Ubuntu 및 Spark에 오신 것을 환영하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-237">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="d2dec-238">**spark-submit** 명령을 사용하여 HDInsight 클러스터에서 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-238">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="d2dec-239">예제 스크립트의 **mycontainer** 및 **mystorageaccount** 를 Blob 컨테이너 및 스토리지 계정의 실제 이름으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-239">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2-4_2.11-1.0.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="d2dec-240">앱이 실행되면 시작 로컬 실행과 동일한 단어 개수 테이블이 콘솔에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-240">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="d2dec-241">축하합니다. 클라우드에서 첫 번째 .NET for Apache Spark 애플리케이션을 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-241">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="d2dec-242">리소스 정리</span><span class="sxs-lookup"><span data-stu-id="d2dec-242">Clean up resources</span></span>

<span data-ttu-id="d2dec-243">HDInsight는 Azure Storage에 데이터를 저장하므로, 사용하지 않을 때는 클러스터를 삭제해도 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-243">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="d2dec-244">HDInsight 클러스터를 사용하지 않는 기간에도 요금이 청구됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-244">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="d2dec-245">클러스터에 대한 요금이 스토리지에 대한 요금보다 몇 배 더 많기 때문에, 클러스터를 사용하지 않을 때는 삭제하는 것이 경제적인 면에서 더 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-245">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="d2dec-246">또한 리소스 그룹 이름을 선택하여 리소스 그룹 페이지를 연 다음, **리소스 그룹 삭제** 를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-246">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="d2dec-247">리소스 그룹을 삭제하여 HDInsight Spark 클러스터와 기본 스토리지 계정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-247">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d2dec-248">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d2dec-248">Next steps</span></span>

<span data-ttu-id="d2dec-249">이 자습서에서는 Azure HDInsight에 .NET for Apache Spark 애플리케이션을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="d2dec-249">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="d2dec-250">HDInsight에 대해 자세히 알아보려면 Azure HDInsight 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d2dec-250">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="d2dec-251">[Azure HDInsight에서 원격으로 작업 제출](../how-to-guides/hdinsight-deploy-methods.md)
> [Azure HDInsight 설명서](/azure/hdinsight/)</span><span class="sxs-lookup"><span data-stu-id="d2dec-251">[Submit jobs remotely on Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md)
[Azure HDInsight Documentation](/azure/hdinsight/)</span></span>
