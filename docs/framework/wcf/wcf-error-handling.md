---
description: '자세한 정보: WCF 오류 처리'
title: WCF 오류 처리
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 57f2c5078e0f73ff57eec79041cb7a2b2d42b498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668177"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="87de5-103">WCF 오류 처리</span><span class="sxs-lookup"><span data-stu-id="87de5-103">WCF Error Handling</span></span>

<span data-ttu-id="87de5-104">WCF 애플리케이션에서 발생하는 오류는 다음 세 그룹 중 하나에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-104">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="87de5-105">통신 오류</span><span class="sxs-lookup"><span data-stu-id="87de5-105">Communication Errors</span></span>  
  
2. <span data-ttu-id="87de5-106">프록시/채널 오류</span><span class="sxs-lookup"><span data-stu-id="87de5-106">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="87de5-107">애플리케이션 오류</span><span class="sxs-lookup"><span data-stu-id="87de5-107">Application Errors</span></span>  
  
 <span data-ttu-id="87de5-108">네트워크를 사용할 수 없거나, 클라이언트가 잘못된 주소를 사용하거나, 서비스 호스트가 들어오는 메시지를 수신하고 있지 않은 경우 통신 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-108">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="87de5-109">이러한 유형의 오류는 클라이언트에 <xref:System.ServiceModel.CommunicationException> 또는 <xref:System.ServiceModel.CommunicationException> 파생 클래스로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-109">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="87de5-110">채널/프록시 오류는 채널 또는 프록시 자체 내에서 발생하는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-110">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="87de5-111">이러한 유형의 오류에는 닫힌 프록시 또는 채널 사용 시도, 클라이언트와 서비스 간의 계약 불일치, 클라이언트 자격 증명이 서비스에서 거부됨 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-111">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="87de5-112">이 범주에는 여러 유형의 오류가 포함되며, 너무 많아서 여기에 모두 나열할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-112">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="87de5-113">이러한 유형의 오류는 클라이언트에 현재 상태대로 반환됩니다(예외 개체에서 변형이 수행되지 않음).</span><span class="sxs-lookup"><span data-stu-id="87de5-113">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="87de5-114">애플리케이션 오류는 서비스 작업을 실행하는 동안 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-114">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="87de5-115">이러한 종류의 오류는 클라이언트에 <xref:System.ServiceModel.FaultException> 또는 <xref:System.ServiceModel.FaultException%601>으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-115">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="87de5-116">WCF의 오류 처리는 다음 방법 중 하나 이상을 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-116">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="87de5-117">throw된 예외 직접 처리</span><span class="sxs-lookup"><span data-stu-id="87de5-117">Directly handling the exception thrown.</span></span> <span data-ttu-id="87de5-118">이 방법은 통신 및 프록시/채널 오류에서만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-118">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="87de5-119">오류 계약 사용</span><span class="sxs-lookup"><span data-stu-id="87de5-119">Using fault contracts</span></span>  
  
- <span data-ttu-id="87de5-120"><xref:System.ServiceModel.Dispatcher.IErrorHandler> 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="87de5-120">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="87de5-121"><xref:System.ServiceModel.ServiceHost> 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="87de5-121">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="87de5-122">오류 계약</span><span class="sxs-lookup"><span data-stu-id="87de5-122">Fault Contracts</span></span>  

 <span data-ttu-id="87de5-123">오류 계약을 사용하면 플랫폼에 독립적인 방법으로 서비스 작업 중에 발생할 수 있는 오류를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-123">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="87de5-124">기본적으로 서비스 작업 내에서 throw된 모든 예외는 클라이언트에 <xref:System.ServiceModel.FaultException> 개체로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-124">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="87de5-125"><xref:System.ServiceModel.FaultException> 개체에는 정보가 거의 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-125">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="87de5-126">오류 계약을 정의하고 오류를 <xref:System.ServiceModel.FaultException%601>으로 반환하여 클라이언트에 전송되는 정보를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-126">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="87de5-127">자세한 내용은 [지정 및 계약 및 서비스에서 오류 처리](specifying-and-handling-faults-in-contracts-and-services.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-127">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="87de5-128">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="87de5-128">IErrorHandler</span></span>  

 <span data-ttu-id="87de5-129"><xref:System.ServiceModel.Dispatcher.IErrorHandler> 인터페이스를 사용하면 WCF 애플리케이션이 오류에 응답하는 방법을 보다 강력하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-129">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="87de5-130">클라이언트에 반환되는 오류 메시지를 완전히 제어하고 로깅 등의 사용자 지정 오류 처리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-130">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="87de5-131"><xref:System.ServiceModel.Dispatcher.IErrorHandler> [오류 처리 및 보고](./samples/extending-control-over-error-handling-and-reporting.md) 에 대 한 제어 및 확장에 대 한 자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="87de5-131">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="87de5-132">ServiceHost 이벤트</span><span class="sxs-lookup"><span data-stu-id="87de5-132">ServiceHost Events</span></span>  

 <span data-ttu-id="87de5-133"><xref:System.ServiceModel.ServiceHost> 클래스는 서비스를 호스트하며 오류 처리에 필요할 수 있는 여러 이벤트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="87de5-133">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="87de5-134">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="87de5-134">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="87de5-135">자세한 내용은 <xref:System.ServiceModel.ServiceHost>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87de5-135">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
