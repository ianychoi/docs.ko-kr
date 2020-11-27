---
title: HTTP, TCP 또는 명명된 파이프를 사용하는 동기 시나리오
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 906bceadf56d82570b41cfbb2c96e4b89d595d02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274441"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="edead-102">HTTP, TCP 또는 명명된 파이프를 사용하는 동기 시나리오</span><span class="sxs-lookup"><span data-stu-id="edead-102">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="edead-103">이 항목에서는 HTTP, TCP 또는 명명된 파이프를 사용하는 단일 스레드 클라이언트가 포함된 다양한 동기 요청/회신 시나리오의 작업 및 전송에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-103">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="edead-104">다중 스레드 요청에 대 한 자세한 내용은 [HTTP, TCP 또는 명명 된 파이프를 사용 하는 비동기 시나리오](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="edead-104">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="edead-105">오류가 없는 동기 요청/회신</span><span class="sxs-lookup"><span data-stu-id="edead-105">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="edead-106">이 단원에서는 단일 스레드 클라이언트에서의 유효한 동기 요청/회신 시나리오 작업 및 전송에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-106">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="edead-107">클라이언트</span><span class="sxs-lookup"><span data-stu-id="edead-107">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="edead-108">서비스 엔드포인트와의 통신 설정</span><span class="sxs-lookup"><span data-stu-id="edead-108">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="edead-109">클라이언트가 구성되고 열립니다.</span><span class="sxs-lookup"><span data-stu-id="edead-109">A client is constructed and opened.</span></span> <span data-ttu-id="edead-110">이러한 각 단계에 대해 앰비언트 활동 (A)이 각각 "클라이언트 생성" (B) 및 "Open Client" (C) 활동으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-110">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="edead-111">전송 중인 각 동작에서 앰비언트 동작은 다시 전송될 때까지, 즉 ServiceModel 코드가 실행될 때까지 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-111">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="edead-112">서비스 엔드포인트에 요청하기</span><span class="sxs-lookup"><span data-stu-id="edead-112">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="edead-113">앰비언트 활동은 "ProcessAction" (D) 활동으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-113">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="edead-114">이 동작 내에서 요청 메시지가 전송되고 응답 메시지가 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-114">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="edead-115">이 동작은 컨트롤이 사용자 코드로 반환되면 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-115">The activity ends when control returns to user code.</span></span> <span data-ttu-id="edead-116">이것은 동기 요청이므로 컨트롤이 반환될 때까지 앰비언트 동작이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-116">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="edead-117">서비스 엔드포인트와의 통신 닫기</span><span class="sxs-lookup"><span data-stu-id="edead-117">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="edead-118">클라이언트의 닫기 동작(I)은 앰비언트 동작에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-118">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="edead-119">이 동작은 새로 만들기 및 열기와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-119">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="edead-120">서버</span><span class="sxs-lookup"><span data-stu-id="edead-120">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="edead-121">서비스 호스트 설정</span><span class="sxs-lookup"><span data-stu-id="edead-121">Setting up a Service Host</span></span>  

 <span data-ttu-id="edead-122">ServiceHost의 새로 만들기 및 열기 동작(N 및 O)은 앰비언트 동작(M)에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-122">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="edead-123">수신기 동작(P)은 각 수신기의 ServiceHost를 열면 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-123">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="edead-124">수신기 동작은 데이터를 받고 처리할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="edead-124">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="edead-125">통신 중에 데이터 받기</span><span class="sxs-lookup"><span data-stu-id="edead-125">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="edead-126">데이터가 네트워크에 도착 하면 수신 된 데이터를 처리 하는 데 아직 (Q)가 없는 경우 "ReceiveBytes" 활동이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-126">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="edead-127">이 동작은 연결 또는 큐 내의 여러 메시지에 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edead-127">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="edead-128">ReceiveBytes 동작은 SOAP 동작 메시지를 구성할 데이터가 충분하면 ProcessMessage 동작(R)을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-128">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="edead-129">동작 R에서 메시지 헤더가 처리되고 activityID 헤더가 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-129">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="edead-130">이 헤더가 있는 경우 동작 ID는 ProcessAction 동작으로 설정되고 그렇지 않으면, 새 ID가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-130">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="edead-131">ProcessAction 동작(S)이 만들어지고 호출이 처리되면 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-131">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="edead-132">이 동작은 사용자 코드(T) 실행 및 가능한 경우 응답 메시지 보내기를 비롯하여 들어오는 메시지와 관련된 모든 처리가 완료되면 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-132">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="edead-133">서비스 호스트 닫기</span><span class="sxs-lookup"><span data-stu-id="edead-133">Closing a Service Host</span></span>  

 <span data-ttu-id="edead-134">ServiceHost의 닫기 동작(Z)은 앰비언트 동작에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="edead-134">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![비동기 시나리오 (HTTP, TCP 또는 명명 된 파이프)를 보여 주는 다이어그램](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="edead-136">에서 \<A: name> `A` 는 이전 텍스트 및 표 3의 작업을 설명 하는 바로 가기 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="edead-136">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="edead-137">`Name`은 동작의 약식 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="edead-137">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="edead-138">인 경우 `propagateActivity` = `true` 클라이언트와 서비스에 대 한 프로세스 동작의 동작 ID가 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-138">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="edead-139">오류가 있는 동기 요청/회신</span><span class="sxs-lookup"><span data-stu-id="edead-139">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="edead-140">이전 시나리오와 유일하게 다른 점은 SOAP 오류 메시지가 응답 메시지로 반환된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="edead-140">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="edead-141">인 경우 `propagateActivity` = `true` 요청 메시지의 작업 ID가 SOAP 오류 메시지에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-141">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="edead-142">오류가 없는 동기 단방향</span><span class="sxs-lookup"><span data-stu-id="edead-142">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="edead-143">첫 번째 시나리오와 유일하게 다른 점은 메시지가 서버로 반환되지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="edead-143">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="edead-144">HTTP 기반 프로토콜의 경우 상태(유효 또는 오류)가 클라이언트로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="edead-144">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="edead-145">이는 HTTP가 WCF 프로토콜 스택의 일부인 요청-응답 의미 체계가 있는 유일한 프로토콜 이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="edead-145">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="edead-146">TCP 처리는 WCF에서 숨겨져 있으므로 클라이언트에 승인이 전송 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="edead-146">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="edead-147">오류가 있는 동기 단방향</span><span class="sxs-lookup"><span data-stu-id="edead-147">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="edead-148">메시지(Q 이상)를 처리하는 동안 오류가 발생하는 경우 클라이언트에게 확인 메시지가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="edead-148">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="edead-149">이 시나리오는 "오류가 없는 동기 단방향" 시나리오와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="edead-149">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="edead-150">오류 메시지를 받으려면 단방향 시나리오를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="edead-150">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="edead-151">이중</span><span class="sxs-lookup"><span data-stu-id="edead-151">Duplex</span></span>  

 <span data-ttu-id="edead-152">이전 시나리오와 다른 점은 클라이언트가 서비스 역할을 한다는 것입니다. 여기서는 비동기 시나리오와 비슷한 ReceiveBytes 및 ProcessMessage 동작을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="edead-152">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
