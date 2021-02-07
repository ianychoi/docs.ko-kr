---
description: 자세한 내용은 Windows Communication Foundation 트랜잭션 개요를 확인 하세요.
title: Windows Communication Foundation 트랜잭션 개요
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: c9d251e4f49ee8e2edaa0ce2ff48738383a1b76c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752654"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="d916b-103">Windows Communication Foundation 트랜잭션 개요</span><span class="sxs-lookup"><span data-stu-id="d916b-103">Windows Communication Foundation Transactions Overview</span></span>

<span data-ttu-id="d916b-104">트랜잭션은 동작 또는 작업 집합을 하나의 개별 실행 단위로 그룹화하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-104">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="d916b-105">트랜잭션은 다음 속성을 가진 작업 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-105">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="d916b-106">원자성.</span><span class="sxs-lookup"><span data-stu-id="d916b-106">Atomicity.</span></span> <span data-ttu-id="d916b-107">특정 트랜잭션에서 완료된 모든 업데이트가 커밋되어 영구화되거나 모두 중단되어 이전 상태로 롤백되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-107">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="d916b-108">일관성.</span><span class="sxs-lookup"><span data-stu-id="d916b-108">Consistency.</span></span> <span data-ttu-id="d916b-109">트랜잭션에서 변경된 내용이 하나의 일관된 상태에서 다른 일관된 상태로의 변환을 나타내도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-109">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="d916b-110">예를 들어 당좌 예금 계좌에서 보통 예금 계좌로 돈을 이체하는 트랜잭션은 전체 은행 계좌의 금액을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-110">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="d916b-111">격리.</span><span class="sxs-lookup"><span data-stu-id="d916b-111">Isolation.</span></span> <span data-ttu-id="d916b-112">트랜잭션이 다른 동시 트랜잭션에 속하는 커밋되지 않은 변경 내용을 인식하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-112">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="d916b-113">격리는 한 트랜잭션의 유지가 다른 트랜잭션의 실행에 예기치 않은 영향을 주지 않도록 하는 동시에 추상적인 동시성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-113">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="d916b-114">지속성.</span><span class="sxs-lookup"><span data-stu-id="d916b-114">Durability.</span></span> <span data-ttu-id="d916b-115">커밋되고 나면 데이터베이스 레코드 같은 관리되는 리소스에 대한 업데이트가 실패한 경우에도 지속되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-115">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="d916b-116">WCF (Windows Communication Foundation)는 웹 서비스 응용 프로그램에서 분산 트랜잭션을 만들 수 있는 다양 한 기능 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-116">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="d916b-117">WCF는 WCF 응용 프로그램에서 타사 기술을 사용 하 여 작성 된 상호 운용 가능한 웹 서비스와 같은 상호 운용 가능한 응용 프로그램으로 트랜잭션을 이동할 수 있도록 하는 WS-AtomicTransaction (WS-AT) 프로토콜에 대 한 지원을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-117">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="d916b-118">또한 WCF는 트랜잭션 흐름을 사용 하도록 설정 하는 interop 기능이 필요 하지 않은 시나리오에서 사용할 수 있는 OLE 트랜잭션 프로토콜에 대 한 지원을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-118">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="d916b-119">애플리케이션 구성 파일에서 바인딩을 구성하여 트랜잭션 흐름을 가능하거나 불가능하게 하고 바인딩에 원하는 트랜잭션 프로토콜을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-119">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="d916b-120">또한 구성 파일을 사용하여 서비스 수준에서 트랜잭션 시간 초과를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-120">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="d916b-121">자세한 내용은 [트랜잭션 흐름 사용](enabling-transaction-flow.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d916b-121">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="d916b-122"><xref:System.ServiceModel> 네임스페이스의 트랜잭션 특성을 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-122">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="d916b-123"><xref:System.ServiceModel.ServiceBehaviorAttribute> 특성을 사용하여 트랜잭션 시간 초과와 격리 수준 필터링을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-123">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="d916b-124"><xref:System.ServiceModel.OperationBehaviorAttribute> 특성을 사용하여 트랜잭션 기능을 활성화하고 트랜잭션 완료 동작을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-124">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="d916b-125">계약 메서드의 <xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute> 특성을 사용하여 트랜잭션 흐름을 필요로 하거나 허용 또는 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="d916b-125">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="d916b-126">자세한 내용은 [ServiceModel 트랜잭션 특성](servicemodel-transaction-attributes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d916b-126">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d916b-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d916b-127">See also</span></span>

- [<span data-ttu-id="d916b-128">ServiceModel 트랜잭션 특성</span><span class="sxs-lookup"><span data-stu-id="d916b-128">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="d916b-129">트랜잭션 흐름 사용</span><span class="sxs-lookup"><span data-stu-id="d916b-129">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
