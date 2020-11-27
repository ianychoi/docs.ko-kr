---
title: Federation 샘플
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 22d405620a77285ebe7a68fc151a8e8611df9b4d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283278"
---
# <a name="federation-sample"></a><span data-ttu-id="56988-102">Federation 샘플</span><span class="sxs-lookup"><span data-stu-id="56988-102">Federation Sample</span></span>

<span data-ttu-id="56988-103">이 샘플에서는 연결된 보안을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56988-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="56988-104">샘플 세부 정보</span><span class="sxs-lookup"><span data-stu-id="56988-104">Sample Details</span></span>  

 <span data-ttu-id="56988-105">WCF (Windows Communication Foundation)는을 통해 페더레이션 보안 아키텍처를 배포 하기 위한 지원을 제공 합니다 `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="56988-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="56988-106">`wsFederationHttpBinding`에서는 요청/회신 통신의 기본 전송 메커니즘으로 HTTP를 사용하고, 인코딩 통신 형식으로 텍스트/XML을 사용하는, 안전하고 안정적이며 상호 운용 가능한 바인딩을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="56988-107">WCF의 페더레이션에 대 한 자세한 내용은 [페더레이션](../feature-details/federation.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56988-107">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="56988-108">이 시나리오는 네 부분으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="56988-109">BookStore 서비스</span><span class="sxs-lookup"><span data-stu-id="56988-109">BookStore service</span></span>  
  
- <span data-ttu-id="56988-110">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="56988-110">BookStore STS</span></span>  
  
- <span data-ttu-id="56988-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="56988-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="56988-112">BookStore 클라이언트</span><span class="sxs-lookup"><span data-stu-id="56988-112">BookStore Client</span></span>  
  
 <span data-ttu-id="56988-113">BookStore 서비스는 `BrowseBooks`와 `BuyBook`의 두 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="56988-114">`BrowseBooks` 작업에 대해서는 익명 액세스를 허용하지만, `BuyBooks` 작업에 액세스하려면 인증 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="56988-115">인증은 BookStore STS에서 발급한 토큰의 형태로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="56988-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="56988-116">BookStore 서비스의 구성 파일은 `wsFederationHttpBinding`을 사용하여 클라이언트를 BookStore STS로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="56988-117">그러면 BookStore STS는 클라이언트에게 HomeRealm STS에서 발급한 토큰을 사용하여 인증하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="56988-118">BookStore STS의 구성 파일도 `wsFederationHttpBinding`을 사용하여 클라이언트를 HomeRealm STS로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="56988-119">`BuyBook` 작업에 액세스할 때의 이벤트 순서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="56988-120">클라이언트는 Windows 자격 증명을 사용하여 HomeRealm STS에 대해 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="56988-121">HomeRealm STS는 BookStore STS에 대한 인증에 사용할 수 있는 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="56988-122">클라이언트는 HomeRealm STS에서 발급한 토큰을 사용하여 BookStore STS에 대해 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="56988-123">BookStore STS가 BookStore 서비스에 대한 인증에 사용할 수 있는 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="56988-124">클라이언트는 BookStore STS에서 발급한 토큰을 사용하여 BookStore 서비스에 대해 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="56988-125">클라이언트가 `BuyBook` 작업에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="56988-126">이 샘플의 설치 및 실행 방법에 대해서는 다음 지침을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="56988-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56988-127">이 샘플을 실행 하려면 **wwwroot** 디렉터리에 대 한 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56988-128">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="56988-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="56988-129">SDK 명령 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="56988-129">Open the SDK command window.</span></span> <span data-ttu-id="56988-130">샘플 경로에서 Setup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="56988-131">그러면 샘플에 필요한 가상 디렉터리가 만들어지고 적절한 권한과 함께 필요한 인증서가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="56988-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="56988-132">Setup.bat 배치 파일은 Windows SDK 명령 프롬프트에서 실행되도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="56988-133">MSSDK 환경 변수는 SDK가 설치되는 디렉터리를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="56988-134">이 환경 변수는 Windows SDK 명령 프롬프트 내에서 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="56988-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="56988-135">Windows Vista에서는 설치에서 IIS 관리자 스크립트를 사용 하므로 IIS 6.0 관리 호환성이 설치 되었는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="56988-136">Windows Vista에서 설치 스크립트를 실행 하려면 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="56988-137">Visual Studio에서 FederationSample을 열고 **빌드** 메뉴에서 **솔루션 빌드** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="56988-138">그러면 일반 프로젝트 파일, Bookstore 서비스, Bookstore STS 및 HomeRealm STS를 빌드하고 IIS에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="56988-139">또한 Bookstore 클라이언트 애플리케이션도 빌드하며, BookStoreClient.exe 실행 파일을 FederationSample\BookStoreClient\bin\Debug 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="56988-140">BookStoreClient.exe를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="56988-141">BookStoreClient 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56988-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="56988-142">**찾아보기 서적** 을 클릭 하면 서 면에서 사용할 수 있는 책을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="56988-143">특정 책을 구입 하려면 목록에서 책을 선택 하 고 **구매 서적** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="56988-144">애플리케이션이 시작되고 Windows 인증과 HomeRealm 보안 토큰 서비스를 사용하여 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="56988-145">이 샘플은 사용자가 가격이 $15 이하인 책을 구입할 수 있도록 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="56988-146">$15보다 비싼 책을 구입하려고 하면 클라이언트는 Book Store 서비스로부터 액세스 거부 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="56988-147">이 샘플은 구입 후 사용자의 신용 한도를 업데이트하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="56988-148">사용자의 (고정)신용 한도 내에서 책을 반복하여 구입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="56988-149">정리하려면</span><span class="sxs-lookup"><span data-stu-id="56988-149">To clean up</span></span>  
  
1. <span data-ttu-id="56988-150">Cleanup.bat를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-150">Run Cleanup.bat.</span></span> <span data-ttu-id="56988-151">그러면 설치 과정에 만들어졌던 가상 디렉터리를 삭제하며 설치되었던 인증서도 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="56988-152">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56988-153">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="56988-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="56988-154">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="56988-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56988-155">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56988-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
