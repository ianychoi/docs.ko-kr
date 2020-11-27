---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267861"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="d9d42-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="d9d42-102">MsmqBindingElementBase</span></span>

<span data-ttu-id="d9d42-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="d9d42-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d42-104">구문</span><span class="sxs-lookup"><span data-stu-id="d9d42-104">Syntax</span></span>  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d9d42-105">메서드</span><span class="sxs-lookup"><span data-stu-id="d9d42-105">Methods</span></span>  

 <span data-ttu-id="d9d42-106">MsmqBindingElementBase 클래스는 메서드를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d9d42-107">속성</span><span class="sxs-lookup"><span data-stu-id="d9d42-107">Properties</span></span>  

 <span data-ttu-id="d9d42-108">MsmqBindingElementBase 클래스에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="d9d42-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="d9d42-109">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="d9d42-110">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="d9d42-110">Data type: string</span></span>  
  
 <span data-ttu-id="d9d42-111">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-112">애플리케이션별 배달 못 한 편지 큐의 위치를 포함하는 URI입니다. 이 큐에는 만료되었거나 전송 또는 전달하지 못한 메시지가 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="d9d42-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="d9d42-113">DeadLetterQueue</span></span>  

 <span data-ttu-id="d9d42-114">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="d9d42-114">Data type: string</span></span>  
  
 <span data-ttu-id="d9d42-115">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-116">사용할 배달 못 한 편지 큐의 형식을 나타내는 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="d9d42-117">지속성</span><span class="sxs-lookup"><span data-stu-id="d9d42-117">Durable</span></span>  

 <span data-ttu-id="d9d42-118">데이터 형식: boolean</span><span class="sxs-lookup"><span data-stu-id="d9d42-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d9d42-119">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-120">이 바인딩에서 처리하는 메시지가 지속적인지 또는 일시적인지를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="d9d42-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="d9d42-121">ExactlyOnce</span></span>  

 <span data-ttu-id="d9d42-122">데이터 형식: boolean</span><span class="sxs-lookup"><span data-stu-id="d9d42-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d9d42-123">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-124">이 바인딩에서 처리하는 메시지가 단 한 번 수신되는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="d9d42-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="d9d42-125">MaxRetryCycles</span></span>  

 <span data-ttu-id="d9d42-126">데이터 형식: sint32</span><span class="sxs-lookup"><span data-stu-id="d9d42-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="d9d42-127">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-128">수신 애플리케이션으로 메시지 전달을 시도하는 최대 재시도 주기 수입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="d9d42-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="d9d42-129">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="d9d42-130">데이터 형식: 문자열</span><span class="sxs-lookup"><span data-stu-id="d9d42-130">Data type: string</span></span>  
  
 <span data-ttu-id="d9d42-131">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-132">포이즌 메시지 처리에 대한 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="d9d42-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="d9d42-133">ReceiveRetryCount</span></span>  

 <span data-ttu-id="d9d42-134">데이터 형식: sint32</span><span class="sxs-lookup"><span data-stu-id="d9d42-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="d9d42-135">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-136">애플리케이션 큐에서 읽은 메시지에 대해 즉시 재시도하는 최대 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="d9d42-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="d9d42-137">RetryCycleDelay</span></span>  

 <span data-ttu-id="d9d42-138">데이터 형식: datetime</span><span class="sxs-lookup"><span data-stu-id="d9d42-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="d9d42-139">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-140">전달하지 못한 메시지를 즉시 다시 전달하려고 시도할 때 재시도 주기 사이의 지연 시간을 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="d9d42-141">timeToLive</span><span class="sxs-lookup"><span data-stu-id="d9d42-141">TimeToLive</span></span>  

 <span data-ttu-id="d9d42-142">데이터 형식: datetime</span><span class="sxs-lookup"><span data-stu-id="d9d42-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="d9d42-143">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-144">이 바인딩에서 처리하는 메시지가 만료되기 전까지 큐에 머무를 수 있는 기간을 나타내는 시간 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="d9d42-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="d9d42-145">UseMsmqTracing</span></span>  

 <span data-ttu-id="d9d42-146">데이터 형식: boolean</span><span class="sxs-lookup"><span data-stu-id="d9d42-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="d9d42-147">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-148">이 바인딩에서 처리하는 메시지의 추적 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="d9d42-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="d9d42-149">UseSourceJournal</span></span>  

 <span data-ttu-id="d9d42-150">데이터 형식: boolean</span><span class="sxs-lookup"><span data-stu-id="d9d42-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="d9d42-151">액세스 형식: 읽기 전용</span><span class="sxs-lookup"><span data-stu-id="d9d42-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9d42-152">이 바인딩에서 처리하는 메시지의 복사본을 소스 업무 일지 큐에 저장하는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d42-153">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d9d42-153">Requirements</span></span>  
  
|<span data-ttu-id="d9d42-154">MOF</span><span class="sxs-lookup"><span data-stu-id="d9d42-154">MOF</span></span>|<span data-ttu-id="d9d42-155">Servicemodel.mof에 선언되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d9d42-156">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="d9d42-156">Namespace</span></span>|<span data-ttu-id="d9d42-157">root\ServiceModel에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9d42-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9d42-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9d42-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
