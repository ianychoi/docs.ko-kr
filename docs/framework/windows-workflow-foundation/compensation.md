---
description: '자세히 알아보기: 보정'
title: 보정
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: d2c57a248939d0485075a5cbf57d91789f58d01a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792793"
---
# <a name="compensation"></a><span data-ttu-id="89f89-103">보정</span><span class="sxs-lookup"><span data-stu-id="89f89-103">Compensation</span></span>

<span data-ttu-id="89f89-104">WF (Windows Workflow Foundation)는 이후 오류가 발생할 때 응용 프로그램에서 정의 된 논리에 따라 이전에 완료 된 작업을 실행 취소 하거나 보정 하는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-104">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="89f89-105">이 단원에서는 워크플로에서 보정을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-105">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="89f89-106">보정과 트랜잭션 비교</span><span class="sxs-lookup"><span data-stu-id="89f89-106">Compensation vs. Transactions</span></span>  

 <span data-ttu-id="89f89-107">트랜잭션을 사용하여 여러 작업을 하나의 작업 단위로 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-107">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="89f89-108">트랜잭션을 사용하면 애플리케이션은 트랜잭션 처리의 어떠한 부분에서도 오류가 발생하지 않은 경우 트랜잭션 내부에서 실행된 모든 변경 내용을 취소(롤백)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-108">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="89f89-109">그러나 작업이 오래 실행되는 경우에는 트랜잭션을 사용하는 방법이 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-109">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="89f89-110">예를 들어 여행 계획 애플리케이션은 워크플로로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-110">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="89f89-111">이 워크플로의 각 단계는 항공권 예약, 관리자 승인 대기, 항공권 결제로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-111">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="89f89-112">이 과정에 며칠이 걸릴 수도 있으므로 항공권 예약 및 결제 단계를 같은 트랜잭션으로 묶는 방법은 적절하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-112">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="89f89-113">이 시나리오에서는 보정을 사용하여 이후 처리 과정에서 오류가 발생하면 워크플로의 예약 단계를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-113">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f89-114">이 항목에서는 워크플로의 보정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-114">This topic covers compensation in workflows.</span></span> <span data-ttu-id="89f89-115">워크플로의 트랜잭션에 대 한 자세한 내용은 [트랜잭션](workflow-transactions.md) 및을 참조 하십시오 <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="89f89-115">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="89f89-116">트랜잭션에 대 한 자세한 내용은 및을 참조 하십시오 <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="89f89-116">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="89f89-117">CompensableActivity 사용</span><span class="sxs-lookup"><span data-stu-id="89f89-117">Using CompensableActivity</span></span>  

 <span data-ttu-id="89f89-118"><xref:System.Activities.Statements.CompensableActivity>는 [!INCLUDE[wf1](../../../includes/wf1-md.md)]의 핵심 보정 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-118"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="89f89-119">보정이 필요할 수 있는 작업을 수행하는 활동은 <xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity>에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-119">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="89f89-120">이 예제에서는 항공권 구매 예약 단계가 <xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity>에 배치되고 예약 취소가 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-120">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="89f89-121">워크플로의 <xref:System.Activities.Statements.CompensableActivity> 바로 다음에 관리자 승인을 대기하고 항공권 구매 단계를 완료하는 두 활동이 옵니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-121">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="89f89-122"><xref:System.Activities.Statements.CompensableActivity>를 완료한 이후에 오류 조건으로 인해 워크플로가 취소될 경우 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 처리기의 활동이 예약되고 항공권이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-122">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="89f89-123">다음 예제는 XAML 형식의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-123">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="89f89-124">워크플로가 호출되면 다음 출력이 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-124">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="89f89-125">**ReserveFlight: 티켓은 예약 되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-125">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="89f89-126">**관리자 승인: 관리자 승인이 수신 되었습니다.** 
 **PurchaseFlight: 티켓을 구매 합니다.** 
 **워크플로가 완료 되었으며 상태: 닫혔습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-126">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="89f89-127">이 항목에서 `ReserveFlight`와 같은 샘플 활동은 이름과 목적을 콘솔에 표시하여 보정이 발생하는 경우 활동의 실행 순서를 보여 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-127">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="89f89-128">기본 워크플로 보정</span><span class="sxs-lookup"><span data-stu-id="89f89-128">Default Workflow Compensation</span></span>  

 <span data-ttu-id="89f89-129">기본적으로 워크플로가 취소되면 성공적으로 완료되었지만 아직 확인되거나 보정되지 않은 보정 가능한 활동에 대한 보정 논리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-129">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f89-130"><xref:System.Activities.Statements.CompensableActivity>이 *확인* 되 면 작업에 대 한 보정을 더 이상 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-130">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="89f89-131">확인 프로세스에 대해서는 이 단원의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-131">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="89f89-132">이 예제에서는 항공권을 예약한 이후에 관리자 승인 단계 이전에 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-132">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="89f89-133">이 예제는 XAML 형식의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-133">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="89f89-134">워크플로가 호출되면 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>에서 호스트 애플리케이션이 시뮬레이션된 오류 조건 예외를 처리하고 워크플로가 취소되고 보정 논리가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-134">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="89f89-135">**ReserveFlight: 티켓은 예약 되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-135">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="89f89-136">**SimulatedErrorCondition: ApplicationException을 throw 합니다.** 
 **워크플로 처리 되지 않은 예외:** 
 System.servicemodel **예외: 워크플로에서 시뮬레이션 된 오류 조건입니다.** 
 **Cancelflight: 티켓이 취소 되었습니다.** 
 **워크플로가 완료 되었습니다 (상태: 취소 됨).**</span><span class="sxs-lookup"><span data-stu-id="89f89-136">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>

### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="89f89-137">취소 및 CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="89f89-137">Cancellation and CompensableActivity</span></span>  

 <span data-ttu-id="89f89-138"><xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity>에 있는 활동이 완료되지 않은 상태에서 활동이 취소되면 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>의 활동이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-138">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f89-139"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>는 <xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity>에 있는 활동이 완료되지 않은 상태에서 활동이 취소되는 경우에만 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-139">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="89f89-140"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>는 <xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity>에 있는 활동이 성공적으로 완료된 다음 활동에 대해 보정이 호출되는 경우에만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-140">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="89f89-141"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>는 워크플로 작성자에게 적절한 취소 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-141">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="89f89-142">다음 예제에서는 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 실행되는 동안 예외가 throw된 다음 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-142">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="89f89-143">이 예제는 XAML 형식의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-143">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="89f89-144">워크플로가 호출되면 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>에서 호스트 애플리케이션이 시뮬레이션된 오류 조건 예외를 처리하고 워크플로가 취소되고 <xref:System.Activities.Statements.CompensableActivity>의 취소 논리가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-144">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="89f89-145">이 예제에서는 보정 논리와 취소 논리가 다른 목표를 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-145">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="89f89-146"><xref:System.Activities.Statements.CompensableActivity.Body%2A>가 성공적으로 완료되면 신용 카드가 청구되고 비행기가 예약되었으므로 보정은 두 단계 모두 실행 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-146">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="89f89-147">이 예에서는 비행을 취소 하면 신용 카드 요금이 자동으로 취소 됩니다. 그러나 <xref:System.Activities.Statements.CompensableActivity> 이 취소 되 면이 완료 되지 않은 것 이므로의 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 논리가 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 취소를 가장 잘 처리 하는 방법을 결정할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-147">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="89f89-148">이 예제에서 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>가 신용 카드 청구를 취소하지만 `ReserveFlight`가 <xref:System.Activities.Statements.CompensableActivity.Body%2A>에서 마지막 활동이었으므로 비행기를 취소하려고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-148">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="89f89-149">`ReserveFlight`가 <xref:System.Activities.Statements.CompensableActivity.Body%2A>에서 마지막 활동이었으므로 성공적으로 완료되었다면 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 완료되었으므로 가능한 취소도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-149">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="89f89-150">**ChargeCreditCard: Charge credit card for flight.**</span><span class="sxs-lookup"><span data-stu-id="89f89-150">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="89f89-151">**SimulatedErrorCondition: ApplicationException을 throw 합니다.** 
 **워크플로 처리 되지 않은 예외:** 
 System.servicemodel **예외: 워크플로에서 시뮬레이션 된 오류 조건입니다.** 
 **Cancelcreditcard: 신용 카드 요금을 취소 합니다.** 
 **워크플로가 완료 되었습니다 (상태: 취소 됨).**</span><span class="sxs-lookup"><span data-stu-id="89f89-151">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="89f89-152">취소에 대 한 자세한 내용은 [취소](modeling-cancellation-behavior-in-workflows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="89f89-152">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="89f89-153">보정 활동을 통한 명시적 보정</span><span class="sxs-lookup"><span data-stu-id="89f89-153">Explicit Compensation Using the Compensate Activity</span></span>  

 <span data-ttu-id="89f89-154">이전 단원에서는 암시적 보정에 대해 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-154">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="89f89-155">암시적 보정은 간단한 시나리오에 적합하지만, 보정 처리 일정에 대한 보다 명시적인 제어가 필요할 경우 <xref:System.Activities.Statements.Compensate> 활동을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-155">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="89f89-156"><xref:System.Activities.Statements.Compensate> 활동을 사용하여 보정 프로세스를 시작하려면 보정을 원하는 <xref:System.Activities.Statements.CompensationToken>의 <xref:System.Activities.Statements.CompensableActivity>이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-156">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="89f89-157"><xref:System.Activities.Statements.Compensate> 활동을 사용하면 완료되었지만 아직 확인되거나 보정되지 않은 <xref:System.Activities.Statements.CompensableActivity>에 대한 보정을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-157">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="89f89-158">예를 들어 <xref:System.Activities.Statements.Compensate> 활동을 <xref:System.Activities.Statements.TryCatch.Catches%2A> 활동의 <xref:System.Activities.Statements.TryCatch> 섹션에서 또는 <xref:System.Activities.Statements.CompensableActivity>가 완료된 이후에 언제든지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-158">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="89f89-159">이 예제에서는 <xref:System.Activities.Statements.Compensate> 활동의 <xref:System.Activities.Statements.TryCatch.Catches%2A> 섹션에서 <xref:System.Activities.Statements.TryCatch> 활동을 사용하여 <xref:System.Activities.Statements.CompensableActivity>의 동작을 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-159">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="89f89-160">이 예제는 XAML 형식의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-160">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="89f89-161">워크플로가 호출되면 다음 출력이 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-161">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="89f89-162">**ReserveFlight: 티켓은 예약 되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-162">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="89f89-163">**SimulatedErrorCondition: ApplicationException을 throw 합니다.** 
 **Cancelflight: 티켓이 취소 되었습니다.** 
 **워크플로가 완료 되었으며 상태: 닫혔습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-163">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>

### <a name="confirming-compensation"></a><span data-ttu-id="89f89-164">보정 확인</span><span class="sxs-lookup"><span data-stu-id="89f89-164">Confirming Compensation</span></span>  

 <span data-ttu-id="89f89-165">기본적으로 보정 가능한 활동은 완료된 이후에 언제든지 보정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-165">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="89f89-166">일부 시나리오에서는 이 방법이 적합하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-166">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="89f89-167">이전 예제에서는 예약을 취소하기 위해 티켓 예약에 대한 보정을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-167">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="89f89-168">하지만 항공권이 완료된 이후에는 이 보정 단계는 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-168">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="89f89-169">보정 가능한 활동을 확인하면 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>가 지정한 활동이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-169">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="89f89-170">예를 들어 보정을 수행하는 데 필요한 리소스를 릴리스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-170">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="89f89-171">보정 가능한 활동이 확인된 이후에는 활동을 보정할 수 없습니다. 이 경우 보정을 시도하면 <xref:System.InvalidOperationException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-171">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="89f89-172">워크플로가 성공적으로 완료되면 완료되었지만 확인되거나 보정되지 않은 모든 보정 가능한 활동이 완료된 역순으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-172">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="89f89-173">이 예제에서는 항공권을 예약하고 구매한 후 완료하면 보정 가능한 활동이 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-173">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="89f89-174"><xref:System.Activities.Statements.CompensableActivity>를 확인하려면 <xref:System.Activities.Statements.Confirm> 활동을 사용하고 확인할 <xref:System.Activities.Statements.CompensationToken>의 <xref:System.Activities.Statements.CompensableActivity>을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-174">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="89f89-175">이 예제는 XAML 형식의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-175">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="89f89-176">워크플로가 호출되면 다음 출력이 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-176">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="89f89-177">**ReserveFlight: 티켓은 예약 되어 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-177">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="89f89-178">**관리자 승인: 관리자 승인이 수신 되었습니다.** 
 **PurchaseFlight: 티켓을 구매 합니다.** 
 **TakeFlight: 비행이 완료 되었습니다.** 
 **가 중 비행: 비행이 발생 했으며 보정을 수행할 수 없습니다.** 
 **워크플로가 완료 되었으며 상태: 닫혔습니다.**</span><span class="sxs-lookup"><span data-stu-id="89f89-178">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="89f89-179">보정 활동 중첩</span><span class="sxs-lookup"><span data-stu-id="89f89-179">Nesting Compensation Activities</span></span>  

<span data-ttu-id="89f89-180"><xref:System.Activities.Statements.CompensableActivity>를 다른 <xref:System.Activities.Statements.CompensableActivity.Body%2A>의 <xref:System.Activities.Statements.CompensableActivity> 섹션에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-180">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="89f89-181"><xref:System.Activities.Statements.CompensableActivity>가 다른 <xref:System.Activities.Statements.CompensableActivity>의 처리기에 배치되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-181">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="89f89-182">이는 부모 <xref:System.Activities.Statements.CompensableActivity>의 책임입니다. 활동을 취소, 확인 또는 보정할 경우 성공적으로 완료되었지만 아직 확인 또는 보정되지 않은 보정 가능한 모든 자식 활동은 부모가 취소, 확인 또는 보정을 완료하기 전에 확인 또는 보정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-182">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="89f89-183">이러한 내용이 명시적으로 모델링되지 않은 경우 부모가 취소 또는 보정 신호를 받으면 부모 <xref:System.Activities.Statements.CompensableActivity>는 보정 가능한 활동을 암시적으로 보정합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-183">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="89f89-184">부모가 확인 신호를 받으면 부모는 보정 가능한 자식 활동을 암시적으로 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-184">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="89f89-185">취소, 확인 또는 보정을 처리하는 논리가 부모 <xref:System.Activities.Statements.CompensableActivity>의 처리기에 명시적으로 모델링되어 있을 경우 명시적으로 처리되지 않은 모든 자식은 암시적으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="89f89-185">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f89-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89f89-186">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
