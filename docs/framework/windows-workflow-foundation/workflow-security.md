---
title: 워크플로 보안
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 6253a0d76d8b1db938e789f19d2cdd5abba9b700
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273895"
---
# <a name="workflow-security"></a><span data-ttu-id="a39f5-102">워크플로 보안</span><span class="sxs-lookup"><span data-stu-id="a39f5-102">Workflow Security</span></span>

<span data-ttu-id="a39f5-103">WF (Windows Workflow Foundation)는 WCF (Microsoft SQL Server 및 Windows Communication Foundation)와 같은 다양 한 기술과 통합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-103">Windows Workflow Foundation (WF) is integrated with several different technologies, such as Microsoft SQL Server and Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a39f5-104">이러한 기술과 잘못 상호 작용하면 워크플로에 보안 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-104">Interacting with these technologies may introduce security issues into your workflow if done improperly.</span></span>

## <a name="persistence-security-concerns"></a><span data-ttu-id="a39f5-105">지속성 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a39f5-105">Persistence Security Concerns</span></span>

1. <span data-ttu-id="a39f5-106"><xref:System.Activities.Statements.Delay> 활동 및 지속성을 사용하는 워크플로는 서비스로 다시 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-106">Workflows that use a <xref:System.Activities.Statements.Delay> activity and persistence need to be reactivated by a service.</span></span> <span data-ttu-id="a39f5-107">Windows AppFabric은 WMS(워크플로 관리 서비스)를 사용하여 만료된 타이머로 워크플로를 다시 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-107">Windows AppFabric uses the Workflow Management Service (WMS) to reactivate workflows with expired timers.</span></span> <span data-ttu-id="a39f5-108">WMS는 <xref:System.ServiceModel.WorkflowServiceHost>를 만들어 다시 활성화된 워크플로를 호스트합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-108">WMS creates a <xref:System.ServiceModel.WorkflowServiceHost> to host the reactivated workflow.</span></span> <span data-ttu-id="a39f5-109">WMS 서비스가 중지된 경우 타이머가 만료되면 지속된 워크플로는 다시 활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-109">If the WMS service is stopped, persisted workflows will not be reactivated when their timers expire.</span></span>

2. <span data-ttu-id="a39f5-110">지속적인 인스턴스에 대한 액세스는 애플리케이션 도메인 외부의 악의적인 엔터티로부터 보호되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-110">Access to durable instancing should be protected against malicious entities external to the application domain.</span></span> <span data-ttu-id="a39f5-111">또한 지속적인 인스턴스 코드와 같은 애플리케이션 도메인에서 개발자는 악의적인 코드를 실행할 수 없는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-111">In addition, developers should ensure that malicious code can't be executed in the same application domain as the durable instancing code.</span></span>

3. <span data-ttu-id="a39f5-112">지속적인 인스턴스는 높은(관리자) 권한으로 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-112">Durable instancing should not be run with elevated (Administrator) permissions.</span></span>

4. <span data-ttu-id="a39f5-113">애플리케이션 도메인 외부에서 처리되는 데이터는 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-113">Data being processed outside the application domain should be protected.</span></span>

5. <span data-ttu-id="a39f5-114">보안 격리가 필요한 애플리케이션은 스키마 추상화의 같은 인스턴스를 공유해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-114">Applications that require security isolation should not share the same instance of the schema abstraction.</span></span> <span data-ttu-id="a39f5-115">이런 애플리케이션은 다른 스토리지 공급자 또는 다른 스토리지 인스턴스를 사용하도록 구성된 스토리지 공급자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-115">Such applications should use different store providers, or store providers configured to use different store instantiations.</span></span>

## <a name="sql-server-security-concerns"></a><span data-ttu-id="a39f5-116">SQL Server 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a39f5-116">SQL Server Security Concerns</span></span>

- <span data-ttu-id="a39f5-117">많은 수의 자식 활동, 위치, 책갈피, 호스트 확장 또는 범위를 사용하거나 매우 큰 페이로드가 있는 책갈피를 사용할 때는 메모리가 부족하거나 유지 중에 과도한 양의 데이터베이스 공간이 할당될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-117">When large numbers of child activities, locations, bookmarks, host extensions, or scopes are used, or when bookmarks with very large payloads are used, memory can be exhausted, or undue amounts of database space can be allocated during persistence.</span></span> <span data-ttu-id="a39f5-118">개체 수준 및 데이터베이스 수준 보안을 사용하여 이 문제를 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-118">This can be mitigated by using object-level and database-level security.</span></span>

- <span data-ttu-id="a39f5-119"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>를 사용할 때는 인스턴스 저장소를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-119">When using <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the instance store must be secured.</span></span>

- <span data-ttu-id="a39f5-120">인스턴스 저장소의 중요 데이터를 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-120">Sensitive data in the instance store should be encrypted.</span></span> <span data-ttu-id="a39f5-121">자세한 내용은 [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f5-121">For more information, see [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption).</span></span>

- <span data-ttu-id="a39f5-122">데이터베이스 연결 문자열은 종종 구성 파일에 포함되기 때문에 Windows 수준 보안(ACL)을 사용하여 구성 파일(대개 Web.Config)이 안전한지, 로그인과 암호 정보가 연결 문자열에 포함되어 있지 않은지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-122">Since the database connection string is often included in a configuration file, windows-level security (ACL) should be used to ensure that the configuration file (Web.Config usually) is secure, and that login and password information are not included in the connection string.</span></span> <span data-ttu-id="a39f5-123">대신 데이터베이스와 웹 서버 사이에는 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-123">Windows authentication should be used between the database and the web server instead.</span></span>

## <a name="considerations-for-workflowservicehost"></a><span data-ttu-id="a39f5-124">WorkflowServiceHost에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a39f5-124">Considerations for WorkflowServiceHost</span></span>

- <span data-ttu-id="a39f5-125">워크플로에서 사용 되는 WCF (Windows Communication Foundation) 끝점을 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-125">Windows Communication Foundation (WCF) endpoints used in workflows should be secured.</span></span> <span data-ttu-id="a39f5-126">자세한 내용은 [WCF 보안 개요](../wcf/feature-details/security-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f5-126">For more information, see [WCF Security Overview](../wcf/feature-details/security-overview.md).</span></span>

- <span data-ttu-id="a39f5-127"><xref:System.ServiceModel.ServiceAuthorizationManager>를 사용하여 호스트 수준 권한 부여를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-127">Host-level authorization can be implemented by using <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span> <span data-ttu-id="a39f5-128">자세한 내용은 [방법: 서비스에 대 한 사용자 지정 권한 부여 관리자 만들기](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a39f5-128">See [How To: Create a Custom Authorization Manager for a Service](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) for details.</span></span>

- <span data-ttu-id="a39f5-129">들어오는 메시지에 대한 ServiceSecurityContext는 OperationContext에 액세스하여 워크플로 내에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-129">The ServiceSecurityContext for the incoming message is also available from within workflow by accessing OperationContext.</span></span>

## <a name="wf-security-pack-ctp"></a><span data-ttu-id="a39f5-130">WF Security Pack CTP</span><span class="sxs-lookup"><span data-stu-id="a39f5-130">WF Security Pack CTP</span></span>

 <span data-ttu-id="a39f5-131">Microsoft WF Security Pack community 기술 미리 보기 (CTP) 1은 [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (wf 4) 및 [WIF (Windows Identity Foundation](/previous-versions/dotnet/framework/security/index))의 [Windows Workflow Foundation](index.md) 을 기반으로 하는 일련의 작업 및 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-131">The Microsoft WF Security Pack community technology preview (CTP) 1 is a set of activities and their implementation based on [Windows Workflow Foundation](index.md) in [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) and [Windows Identity Foundation (WIF)](/previous-versions/dotnet/framework/security/index).</span></span> <span data-ttu-id="a39f5-132">Microsoft WF Security Pack CTP 1에는 다음과 같은 워크플로를 사용하여 다양한 보안 관련 시나리오를 손쉽게 사용하는 방법을 보여 주는 활동과 디자이너가 모두 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a39f5-132">The Microsoft WF Security Pack CTP 1 contains both activities and their designers which illustrate how to easily enable various security-related scenarios using workflow, including:</span></span>

1. <span data-ttu-id="a39f5-133">워크플로에서 클라이언트 ID 가장</span><span class="sxs-lookup"><span data-stu-id="a39f5-133">Impersonating a client identity in the workflow</span></span>

2. <span data-ttu-id="a39f5-134">PrincipalPermission 및 클레임의 유효성 검사 같은 워크플로 내 인증</span><span class="sxs-lookup"><span data-stu-id="a39f5-134">In-workflow authorization, such as PrincipalPermission and validation of Claims</span></span>

3. <span data-ttu-id="a39f5-135">사용자 이름/암호 또는 STS(보안 토큰 서비스)에서 검색한 토큰 같은 워크플로에 지정된 ClientCredentials을 사용하여 인증된 메시징</span><span class="sxs-lookup"><span data-stu-id="a39f5-135">Authenticated messaging using ClientCredentials specified in the workflow, such as username/password or a token retrieved from a Security Token Service (STS)</span></span>

4. <span data-ttu-id="a39f5-136">WS-Trust ActAs를 사용하여 클라이언트 보안 토큰이 백엔드 서비스로 이동(클레임 기반 위임)</span><span class="sxs-lookup"><span data-stu-id="a39f5-136">Flowing a client security token to a back-end service (claims-based delegation) using WS-Trust ActAs</span></span>

<span data-ttu-id="a39f5-137">자세한 내용을 보고 WF Security Pack CTP를 다운로드 하려면 다음을 참조 하세요. [Wf Security PACK ctp](https://archive.codeplex.com/?p=wf)</span><span class="sxs-lookup"><span data-stu-id="a39f5-137">For more information and to download the WF Security Pack CTP, see: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)</span></span>
