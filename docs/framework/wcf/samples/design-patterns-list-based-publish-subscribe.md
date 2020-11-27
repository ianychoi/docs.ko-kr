---
title: '디자인 패턴: 목록 기반 게시-구독'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 4e679980df8a720eb4aa22741bbdd067940c7723
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292677"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="176eb-102">디자인 패턴: 목록 기반 게시-구독</span><span class="sxs-lookup"><span data-stu-id="176eb-102">Design Patterns: List-Based Publish-Subscribe</span></span>

<span data-ttu-id="176eb-103">이 샘플에서는 WCF (Windows Communication Foundation) 프로그램으로 구현 된 목록 기반 Publish-Subscribe 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="176eb-104">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="176eb-105">목록 기반 Publish-Subscribe 디자인 패턴은 Microsoft 패턴 & 사례 게시, [통합 패턴](/previous-versions/msp-n-p/ff647309(v=pandp.10))에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="176eb-106">게시-구독 패턴에서는 정보 항목을 구독한 받는 사람 컬렉션으로 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="176eb-107">목록 기반 게시-구독에서는 구독자 목록을 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="176eb-108">공유할 정보가 있으면 목록에 있는 각 구독자에게 복사본이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="176eb-109">이 샘플에서는 필요할 때마다 클라이언트에서 구독하거나 구독 취소할 수 있는 동적 목록 기반 게시-구독 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="176eb-110">List-based Publish-Subscribe 샘플은 클라이언트, 서비스 및 데이터 소스 프로그램으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="176eb-111">둘 이상의 클라이언트와 둘 이상의 데이터 소스 프로그램이 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="176eb-112">클라이언트에서는 서비스를 구독하고 알림을 수신하며 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="176eb-113">데이터 소스 프로그램에서는 현재 모든 구독자와 공유할 정보를 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="176eb-114">이 샘플에서 클라이언트와 데이터 소스는 콘솔 프로그램(.exe 파일)이고 서비스는 IIS(인터넷 정보 서비스)에서 호스트되는 라이브러리(.dll)입니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="176eb-115">클라이언트와 데이터 소스 동작은 데스크톱에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="176eb-116">서비스에서는 이중 통신을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-116">The service uses duplex communication.</span></span> <span data-ttu-id="176eb-117">`ISampleContract` 서비스 계약은 `ISampleClientCallback` 콜백 계약과 쌍을 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="176eb-118">서비스는 클라이언트가 구독자 목록에 가입하거나 해제하는 데 사용하는 Subscribe 및 Unsubscribe 서비스 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="176eb-119">또한 서비스는 데이터 소스 프로그램에서 서비스에 새 정보를 제공하기 위해 호출하는 `PublishPriceChange` 서비스 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="176eb-120">클라이언트 프로그램은 서비스에서 모든 구독자에게 가격 변경을 알리기 위해 호출하는 `PriceChange` 서비스 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="176eb-121">서비스는 모든 구독자에게 새 정보에 대해 알리는 메커니즘으로 .NET Framework 이벤트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="176eb-122">클라이언트에서 Subscribe를 호출하여 서비스에 가입하면 이벤트 처리기가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="176eb-123">클라이언트가 해제되면 이벤트에서 이벤트 처리기가 구독 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="176eb-124">데이터 소스에서 서비스를 호출하여 가격 변경을 보고하면 서비스에서 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="176eb-125">그러면 구독한 각 클라이언트에 대해 하나씩 서비스 인스턴스가 각각 호출되고 해당 이벤트 처리기가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="176eb-126">각 이벤트 처리기에서는 콜백 함수를 통해 해당 클라이언트로 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="176eb-127">샘플을 실행하면 여러 클라이언트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="176eb-128">클라이언트는 서비스를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-128">The clients subscribe to the service.</span></span> <span data-ttu-id="176eb-129">그런 다음 서비스로 정보를 보내는 데이터 소스 프로그램이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="176eb-130">서비스는 정보를 모든 구독자에게 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="176eb-131">정보가 수신되었는지를 확인하는 동작을 각 클라이언트 콘솔에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="176eb-132">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="176eb-133">샘플을 설치하고 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="176eb-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="176eb-134">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="176eb-135">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="176eb-136">단일 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="176eb-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="176eb-137">다음 주소를 입력 하 여 브라우저를 사용 하 여 서비스에 액세스할 수 있는지 테스트 `http://localhost/servicemodelsamples/service.svc` 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="176eb-138">확인 페이지가 응답으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="176eb-139">언어별 폴더의 \client\bin에서 Client.exe를 실행 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="176eb-140">클라이언트 콘솔 창에 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="176eb-141">여러 클라이언트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="176eb-142">언어별 폴더의 \datasource\bin에서 Datasource.exe를 실행 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="176eb-143">데이터 소스 동작이 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="176eb-144">데이터 소스에서 서비스로 정보를 보내면 각 클라이언트로 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="176eb-145">클라이언트, 데이터 원본 및 서비스 프로그램이 통신할 수 없는 경우 [WCF 샘플에 대 한 문제 해결 팁](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="176eb-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="176eb-146">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="176eb-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="176eb-147">서비스 컴퓨터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="176eb-148">서비스 컴퓨터에서 ServiceModelSamples라는 가상 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="176eb-149">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md) 에서 Setupvroot.bat 배치 파일을 사용 하 여 디스크 디렉터리와 가상 디렉터리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="176eb-150">%SystemDrive%\Inetpub\wwwroot\servicemodelsamples에서 서비스 컴퓨터의 ServiceModelSamples 가상 디렉터리로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="176eb-151">\bin 디렉터리에 파일을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="176eb-152">클라이언트 컴퓨터에서 브라우저를 사용하여 서비스에 액세스할 수 있는지 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="176eb-153">클라이언트 컴퓨터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="176eb-154">언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="176eb-155">각 클라이언트 구성 파일에서 엔드포인트 정의의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="176eb-156">주소에서 "localhost"에 대한 참조를 정규화된 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="176eb-157">데이터 소스 컴퓨터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="176eb-158">언어별 폴더의 \datasource\bin\ 폴더에서 데이터 소스 프로그램 파일을 데이터 소스 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="176eb-159">데이터 소스 구성 파일에서 엔드포인트 정의의 주소 값을 서비스의 새 주소와 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="176eb-160">주소에서 "localhost"에 대한 참조를 정규화된 도메인 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="176eb-161">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="176eb-162">데이터 소스 컴퓨터의 명령 프롬프트에서 Datasource.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="176eb-163">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="176eb-164">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="176eb-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="176eb-165">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="176eb-166">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="176eb-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
