---
description: '자세한 정보: 검색 라우터 서비스'
title: 검색 라우터 서비스
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f5fa4cd19758bef0b867fafc5af4b9cf6df27028
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726717"
---
# <a name="discovery-router-service"></a><span data-ttu-id="43d27-103">검색 라우터 서비스</span><span class="sxs-lookup"><span data-stu-id="43d27-103">Discovery Router Service</span></span>

<span data-ttu-id="43d27-104">이 샘플에서는 검색 메시지를 다른 엔드포인트에 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-104">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="43d27-105">데모</span><span class="sxs-lookup"><span data-stu-id="43d27-105">Demonstrates</span></span>  

 <span data-ttu-id="43d27-106">검색 라우팅</span><span class="sxs-lookup"><span data-stu-id="43d27-106">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="43d27-107">토론(Discussion)</span><span class="sxs-lookup"><span data-stu-id="43d27-107">Discussion</span></span>  

 <span data-ttu-id="43d27-108">클라이언트에서 프록시를 사용하여 서비스를 찾으려고 하며 프록시에서는 이러한 서비스를 인식하지 못하지만 다른 프록시는 인식하는 경우에 검색 라우팅이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-108">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="43d27-109">이 프록시에서는 이 클라이언트의 검색 패킷을 두 번째 프록시에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-109">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="43d27-110">두 번째 프록시에서는 서비스를 찾고 원래 클라이언트에 응답을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-110">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="43d27-111">이 샘플의 클라이언트에서는 검색 라우팅 구성 요소에 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-111">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="43d27-112">이 메시지는 검색 라우터의 특정 엔드포인트에 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-112">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="43d27-113">그런 다음 라우터에서 해당 메시지를 UDP 멀티캐스트 엔드포인트에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-113">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="43d27-114">프로브 메시지는 멀티캐스트 엔드포인트로 이동하며 UDP 멀티캐스트 주소에서 수신 대기하는 서비스는 해당 검색 라우터에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-114">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="43d27-115">검색 라우터에서는 응답을 수집하여 클라이언트로 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-115">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43d27-116">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="43d27-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="43d27-117">샘플을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-117">Build the sample.</span></span>  
  
2. <span data-ttu-id="43d27-118">DiscoveryRouter 실행 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-118">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="43d27-119">빌드 디렉터리에서 서비스 실행 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-119">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="43d27-120">클라이언트 실행 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-120">Run the client executable.</span></span> <span data-ttu-id="43d27-121">그러면 클라이언트에서는 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-121">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43d27-122">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43d27-123">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="43d27-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="43d27-124">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43d27-125">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d27-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
