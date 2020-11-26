---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: e095221e1f17cdf4a63c2fe86d5ba050e354e471
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240695"
---
# <a name="customchannelstester"></a><span data-ttu-id="af2a8-102">CustomChannelsTester</span><span class="sxs-lookup"><span data-stu-id="af2a8-102">CustomChannelsTester</span></span>

<span data-ttu-id="af2a8-103">`CustomChannelsTester`는 미리 정의된 서비스 계약 집합에 대해 사용자 지정 채널 구현을 테스트하는 데 사용할 수 있는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-103">The `CustomChannelsTester` is a tool that you can use to test your custom channel implementations against a set of predefined service contracts.</span></span> <span data-ttu-id="af2a8-104">서비스 계약 집합을 선택한 다음 XML 파일을 사용하여 이 도구에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-104">You can select the set of service contracts and pass it to the tool using an XML file.</span></span> <span data-ttu-id="af2a8-105">그러면 이 도구는 메시지 교환 중에 사용자 지정 채널 구현을 연습하는 서비스와 클라이언트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-105">The tool then generates the service and client that exercises your custom channel implementations during message exchange.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="af2a8-106">도구를 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="af2a8-106">To build the tool</span></span>  
  
1. <span data-ttu-id="af2a8-107">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="af2a8-107">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="af2a8-108">솔루션을 빌드하면 CustomChannelsTester.exe, TestSpec.xml 및 SampleRun.cmd의 세 가지 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-108">Building the solution generates three files: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd.</span></span> <span data-ttu-id="af2a8-109">SampleRun 파일에는이 도구를 사용 하 여 [전송: UDP](transport-udp.md) 샘플을 테스트 하는 방법을 보여 주는 샘플 명령줄이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-109">The file SampleRun.cmd has a sample command line that shows how to use this tool to test the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="af2a8-110">도구를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="af2a8-110">To run the tool</span></span>  
  
- <span data-ttu-id="af2a8-111">명령 프롬프트에 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-111">At the command prompt type the following command:</span></span>  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     <span data-ttu-id="af2a8-112">`/binding` 옵션은 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-112">Using the `/binding` option is required.</span></span>  
  
     <span data-ttu-id="af2a8-113">`/dll` "바인딩"이 Windows Communication Foundation (WCF)에서 제공 하는 시스템 제공 바인딩이 아닌 경우 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-113">`/dll` is required if "binding" is not a system-provided binding provided by Windows Communication Foundation (WCF).</span></span>  
  
     <span data-ttu-id="af2a8-114">`/testspec`는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-114">`/testspec` is optional.</span></span>  
  
     <span data-ttu-id="af2a8-115">이 명령을 실행하면 테스트 사양 및 바인딩에 따라 서버와 클라이언트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-115">This creates server and clients based on the test specifications and the binding.</span></span>  
  
     <span data-ttu-id="af2a8-116">클라이언트와 서버를 실행하고 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-116">Executes the client and server and returns the results.</span></span>  
  
     <span data-ttu-id="af2a8-117">다음은 테스트 사양을 설명하는 샘플 XML(testspec.xml)입니다.</span><span class="sxs-lookup"><span data-stu-id="af2a8-117">The following is the sample XML for the description of the test specifications (testspec.xml):</span></span>  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>
    <!-- Test a sessionful / sessionless contract-->
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
