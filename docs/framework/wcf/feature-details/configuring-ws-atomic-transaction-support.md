---
description: '자세한 정보: 트랜잭션 지원 구성 WS-Atomic'
title: WS-Atomic Transaction 지원 구성
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: c9b732bd0d6b6aa8cb1cf04803ae302a00348987
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780546"
---
# <a name="configure-ws-atomic-transaction-support"></a><span data-ttu-id="6069d-103">WS-Atomic 트랜잭션 지원 구성</span><span class="sxs-lookup"><span data-stu-id="6069d-103">Configure WS-Atomic Transaction support</span></span>

<span data-ttu-id="6069d-104">이 항목에서는 WS-AT 구성 유틸리티를 사용하여 WS-AT(WS-AtomicTransaction) 지원을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-104">This topic describes how you can configure WS-AtomicTransaction (WS-AT) support by using the WS-AT Configuration Utility.</span></span>

## <a name="use-the-ws-at-configuration-utility"></a><span data-ttu-id="6069d-105">WS-AT 구성 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="6069d-105">Use the WS-AT configuration utility</span></span>

<span data-ttu-id="6069d-106">WS-AT 구성 유틸리티(wsatConfig.exe)는 WS-AT 설정을 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-106">The WS-AT Configuration Utility (wsatConfig.exe) is used to configure WS-AT settings.</span></span> <span data-ttu-id="6069d-107">WS-AT 프로토콜 서비스를 사용하려면 구성 유틸리티를 사용하여 WS-AT에 대해 HTTPS 포트를 구성하고, X.509 인증서를 HTTPS 포트에 바인딩하고, 인증서 주체 이름이나 지문을 지정하여 허가된 파트너 인증서를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-107">In order to enable the WS-AT protocol service, you must use the configuration utility to configure the HTTPS port for WS-AT, bind an X.509 certificate to the HTTPS port, and configure authorized partner certificates by specifying certificate subject names or thumbprints.</span></span> <span data-ttu-id="6069d-108">구성 유틸리티를 사용하여 추적 모드를 선택하고 기본 보내기 및 최대 받기 트랜잭션 시간 제한을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-108">The configuration utility also allows you to select the tracing mode and set default outgoing and maximum incoming transaction timeouts.</span></span>

<span data-ttu-id="6069d-109">구성 요소 서비스 관리 콘솔의 MMC(Microsoft Management Console) 속성 페이지 스냅인을 사용하거나 명령줄 창에서 이 도구의 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-109">You can access this tool's functionality by using a Microsoft Management Console (MMC) property page snap-in in the Component Services management console, or from a command-line window.</span></span> <span data-ttu-id="6069d-110">명령줄 창을 통해 로컬 컴퓨터에서 WS-AT 지원을 구성합니다. MMC 스냅인을 사용하는 경우 로컬 및 원격 컴퓨터에서 모두 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-110">Configure WS-AT support on the local machine through the command-line window; configure settings on both local and remote machines by using the MMC snap-in.</span></span>

<span data-ttu-id="6069d-111">명령줄 창은 Windows SDK 설치 위치 "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation"에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-111">The command-line window can be accessed in the Windows SDK installation location "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".</span></span>

<span data-ttu-id="6069d-112">명령줄 도구에 대 한 자세한 내용은 [Ws-atomictransaction 구성 유틸리티 (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6069d-112">For more information about the command-line tool, see [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md).</span></span>

<span data-ttu-id="6069d-113">Windows XP 또는 Windows Server 2003를 실행 하는 경우 **제어판/관리 도구/구성 요소 서비스로** 이동 하 여 **내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하 여 MMC 스냅인에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-113">If you are running Windows XP or Windows Server 2003, you can access the MMC snap-in by navigating to **Control Panel/Administrative Tools/Component Services**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="6069d-114">동일한 위치에서 MSDTC(Microsoft Distributed Transaction Coordinator)를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-114">This is the same location where you can configure the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="6069d-115">구성에 사용할 수 있는 옵션은 **ws-at** 탭에서 그룹화 됩니다. Windows Vista 또는 Windows Server 2008를 실행 하는 경우 **시작** 단추를 클릭 하 고 `dcomcnfg.exe` **검색** 상자에를 입력 하 여 MMC 스냅인을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-115">Options available for configuration are grouped under the **WS-AT** tab. If you are running Windows Vista or Windows Server 2008, the MMC snap-in can be found by clicking the **Start** button, and entering `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="6069d-116">MMC를 열면 **My Computer\Distributed Transaction COORDINATOR\LOCAL DTC** 노드로 이동 하 고 마우스 오른쪽 단추를 클릭 한 다음 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-116">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="6069d-117">구성에 사용할 수 있는 옵션은 **ws-at** 탭에서 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-117">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

<span data-ttu-id="6069d-118">스냅인에 대 한 자세한 내용은 [Ws-atomictransaction 구성 MMC 스냅인](../ws-atomictransaction-configuration-mmc-snap-in.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6069d-118">For more information about the snap-in, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md).</span></span>

<span data-ttu-id="6069d-119">도구의 사용자 인터페이스를 사용하려면 먼저 다음 경로에 있는 WsatUI.dll 파일을 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-119">To enable the tool's user interface, you must first register the WsatUI.dll file, located at the following path</span></span>

<span data-ttu-id="6069d-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span><span class="sxs-lookup"><span data-stu-id="6069d-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span></span>

<span data-ttu-id="6069d-121">제품을 등록하려면 명령 프롬프트 창에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-121">To register the product, execute the following command from a Command Prompt window:</span></span>

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a><span data-ttu-id="6069d-122">WS-AT 사용</span><span class="sxs-lookup"><span data-stu-id="6069d-122">Enable WS-AT</span></span>

<span data-ttu-id="6069d-123">포트 443과 로컬 컴퓨터 저장소에 설치된 프라이빗 키가 있는 X.509 인증서를 사용하여 MSDTC 내부에서 WS-AT 프로토콜 서비스를 활성화하려면 다음 명령으로 wsatConfig.exe 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-123">To enable the WS-AT protocol service inside MSDTC using port 443 and an X.509 certificate with a private key that has been installed in the local machine store, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

<span data-ttu-id="6069d-124">각 매개 변수를 환경에 적합한 값으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-124">Substitute the respective parameters with values relevant to your environment.</span></span>

<span data-ttu-id="6069d-125">MSDTC 내부에서 WS-AT 프로토콜 서비스를 비활성화하려면 다음 명령으로 wsatConfig.exe 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-125">To disable the WS-AT protocol service inside MSDTC, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a><span data-ttu-id="6069d-126">두 컴퓨터 간의 신뢰 구성</span><span class="sxs-lookup"><span data-stu-id="6069d-126">Configure trust between two machines</span></span>

<span data-ttu-id="6069d-127">WS-AT 프로토콜 서비스를 사용하려면 관리자가 분산 트랜잭션에 참여할 개별 계정에 명시적으로 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-127">The WS-AT protocol service requires the administrator to explicitly authorize individual accounts to participate in distributed transactions.</span></span> <span data-ttu-id="6069d-128">두 컴퓨터의 관리자인 경우 컴퓨터 간에 올바른 인증서 집합을 교환하고 적합한 인증서 저장소에 설치한 다음 wsatConfig.exe 도구를 사용하여 각 컴퓨터의 인증서를 다른 컴퓨터의 허가된 참가자 인증서 목록에 추가함으로써 상호 트러스트 관계를 설정하도록 두 컴퓨터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-128">If you are an administrator for two machines, you can configure both machines to establish a mutual trust relationship by exchanging the right set of certificates between the machines, installing them into the appropriate certificate stores, and using the wsatConfig.exe tool to add each machine's certificate to the other's list of authorized participant certificates.</span></span> <span data-ttu-id="6069d-129">이 단계는 WS-AT를 사용하여 두 컴퓨터 간에 분산 트랜잭션을 수행하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-129">This step is necessary to perform distributed transactions between two machines using WS-AT.</span></span>

<span data-ttu-id="6069d-130">다음 예제에서는 두 컴퓨터 A와 B 간에 트러스트를 설정하는 단계를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-130">In the following example outlines the steps to establish trust between two machines, A and B.</span></span>

### <a name="create-and-export-certificates"></a><span data-ttu-id="6069d-131">인증서 만들기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="6069d-131">Create and export certificates</span></span>

<span data-ttu-id="6069d-132">이 절차에는 MMC 인증서 스냅인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-132">This procedure requires the MMC Certificates snap-in.</span></span> <span data-ttu-id="6069d-133">이 스냅인은 시작/실행 메뉴를 열고 입력 상자에 "mmc"를 입력한 다음 확인을 눌러 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-133">The snap-in can be accessed by opening the Start/Run menu, typing "mmc" in the input box and pressing OK.</span></span> <span data-ttu-id="6069d-134">그런 다음, **콘솔** 1 창에서 **파일/추가/제거** 스냅인으로 이동 하 고 추가를 클릭 한 다음 **사용 가능한 독립 실행형 스냅인** 목록에서 **인증서** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-134">Then, in the **Console1** window, navigate to **the File/Add-Remove** Snap-in, click Add, and choose **Certificates** from the **Available Standalone Snapins** list.</span></span> <span data-ttu-id="6069d-135">마지막으로 관리할 **컴퓨터 계정** 을 선택 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-135">Finally, select **Computer Account** to manage and click **OK**.</span></span> <span data-ttu-id="6069d-136">**인증서** 노드가 스냅인 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-136">The **Certificates** node appears in the snap-in console.</span></span>

<span data-ttu-id="6069d-137">트러스트를 설정하려면 필요한 인증서가 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-137">You must already possess the required certificates to establish trust.</span></span> <span data-ttu-id="6069d-138">다음 단계를 수행 하기 전에 새 인증서를 만들고 설치 하는 방법을 알아보려면 [방법: 개발 하는 동안 WCF에서 임시 클라이언트 인증서 만들기 및 설치](/previous-versions/msp-n-p/ff650751(v=pandp.10))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6069d-138">To learn how to create and install new certificates prior to the following steps, see [How to: Create and Install Temporary Client Certificates in WCF During Development](/previous-versions/msp-n-p/ff650751(v=pandp.10)).</span></span>

1. <span data-ttu-id="6069d-139">컴퓨터 A에서 MMC 인증서 스냅인을 사용하여 기존 인증서(certA)를 LocalMachine\MY(개인 노드) 및 LocalMachine\ROOT 저장소(신뢰할 수 있는 루트 인증 기관 노드)로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-139">On machine A, using the MMC Certificates snap-in, import the existing certificate (certA) into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span> <span data-ttu-id="6069d-140">특정 노드로 인증서를 가져오려면 노드를 마우스 오른쪽 단추로 클릭 하 고 **모든 작업/가져오기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-140">To import a certificate to a specific node, right-click the node and choose **All Tasks/Import**.</span></span>

2. <span data-ttu-id="6069d-141">컴퓨터 B에서 MMC 인증서 스냅인을 사용하여 프라이빗 키가 있는 certB 인증서를 만들거나 얻어 LocalMachine\MY(개인 노드) 및 LocalMachine\ROOT 저장소(신뢰할 수 있는 루트 인증 기관 노드)로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-141">On machine B, using the MMC Certificates snap-in, create or obtain a certificate certB with a private key and import it into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span>

3. <span data-ttu-id="6069d-142">아직 수행하지 않은 경우 certA의 공개 키를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-142">Export certA's public key to a file if this has not been done already.</span></span>

4. <span data-ttu-id="6069d-143">아직 수행하지 않은 경우 certB의 공개 키를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-143">Export certB's public key to a file if this has not been done already.</span></span>

### <a name="establish-mutual-trust-between-machines"></a><span data-ttu-id="6069d-144">컴퓨터 간 상호 트러스트 설정</span><span class="sxs-lookup"><span data-stu-id="6069d-144">Establish mutual trust between machines</span></span>

1. <span data-ttu-id="6069d-145">컴퓨터 A에서 certB의 파일 표현을 LocalMachine\MY 및 LocalMachine\ROOT 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-145">On machine A, import the file representation of certB into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="6069d-146">이렇게 하면 컴퓨터 A가 통신할 때 certB를 트러스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-146">This declares that machine A trusts certB to communicate with it.</span></span>

2. <span data-ttu-id="6069d-147">컴퓨터 B에서 certA의 파일을 LocalMachine\MY 및 LocalMachine\ROOT 저장소로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-147">On machine B, import certA’s file into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="6069d-148">이렇게 하면 컴퓨터 B가 통신할 때 certA를 트러스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-148">This implies that machine B trusts certA to communicate with it.</span></span>

<span data-ttu-id="6069d-149">이 단계를 완료하면 두 컴퓨터 간에 트러스트가 설정되고 WS-AT를 사용하여 서로 통신하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-149">After completing these steps, trust is established between the two machines, and they can be configured to communicate with each other using WS-AT.</span></span>

### <a name="configure-msdtc-to-use-certificates"></a><span data-ttu-id="6069d-150">인증서를 사용 하도록 MSDTC 구성</span><span class="sxs-lookup"><span data-stu-id="6069d-150">Configure MSDTC to use certificates</span></span>

<span data-ttu-id="6069d-151">WS-AT 프로토콜 서비스는 클라이언트와 서버로 모두 작동하므로 들어오는 연결을 수신 대기하고 보내는 연결을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-151">Since the WS-AT protocol service acts as both a client and a server, it must both listen for incoming connections and initiate outgoing connections.</span></span> <span data-ttu-id="6069d-152">따라서 외부 당사자와 통신할 때 사용할 인증서와 들어오는 통신을 수락할 때 권한을 부여할 인증서를 알 수 있도록 MSDTC를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-152">Therefore, you need to configure MSDTC so that it knows which certificate to use when communicating with external parties, and which certificates to authorize when accepting incoming communication.</span></span>

<span data-ttu-id="6069d-153">MMC WS-AT 스냅인을 사용하여 이 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-153">You can configure this by using the MMC WS-AT snap-in.</span></span> <span data-ttu-id="6069d-154">이 도구에 대 한 자세한 내용은 [Ws-atomictransaction 구성 MMC 스냅인](../ws-atomictransaction-configuration-mmc-snap-in.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6069d-154">For more information about this tool, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="6069d-155">다음 단계에서는 MSDTC를 실행하는 두 컴퓨터 간에 트러스트를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-155">The following steps describe how to establish trust between two computers running MSDTC.</span></span>

1. <span data-ttu-id="6069d-156">컴퓨터 A의 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-156">Configure machine A's settings.</span></span> <span data-ttu-id="6069d-157">"끝점 인증서"에 대해 인증서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-157">For "Endpoint Certificate", select certA.</span></span> <span data-ttu-id="6069d-158">"권한 있는 인증서"의 경우 인증서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-158">For "Authorized Certificates", select the certB.</span></span>

2. <span data-ttu-id="6069d-159">컴퓨터 B의 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-159">Configure machine B's settings.</span></span> <span data-ttu-id="6069d-160">"끝점 인증서"에 대해 인증서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-160">For "Endpoint Certificate", select certB.</span></span> <span data-ttu-id="6069d-161">"권한 있는 인증서"의 경우 인증서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-161">For "Authorized Certificates", select the certA.</span></span>

> [!NOTE]
> <span data-ttu-id="6069d-162">한 컴퓨터에서 다른 컴퓨터로 메시지를 보낼 때 발신자는 수신자 인증서의 주체 이름과 수신자 컴퓨터의 이름이 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-162">When one machine sends a message to the other machine, the sender attempts to verify that the subject name of the recipient’s certificate and the name of the recipient’s machine match.</span></span> <span data-ttu-id="6069d-163">일치하지 않으면 인증서 확인이 실패하고 두 컴퓨터가 통신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-163">If they do not match, certificate verification fails and the two machines cannot communicate.</span></span>
>
> <span data-ttu-id="6069d-164">도메인에 가입된 컴퓨터의 경우 이름이 정규화된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-164">For a machine joined to a domain, the name is the fully qualified domain name.</span></span> <span data-ttu-id="6069d-165">기본적으로 작업 그룹의 컴퓨터 이름은 컴퓨터의 NetBIOS 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-165">By default, the name of a machine on a workgroup is the machine’s NetBIOS name.</span></span> <span data-ttu-id="6069d-166">그러나 두 컴퓨터 간에 사용되는 연결에 DNS(Domain Name System) 접미사가 있는 경우 해당 접미사도 이름에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-166">However, the name can also include a Domain Name System (DNS) suffix if one is present for the connection being used between the two machines.</span></span>
>
> <span data-ttu-id="6069d-167">컴퓨터 이름이 변경되는 경우, 예를 들어 작업 그룹 컴퓨터가 도메인에 가입하는 경우 인증서를 다시 발급하거나 수동으로 DNS 접미사를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-167">If the name of the machine changes, for example, when a workgroup machine joins a domain, you must reissue certificates or manually configure DNS suffixes.</span></span>

## <a name="security"></a><span data-ttu-id="6069d-168">보안</span><span class="sxs-lookup"><span data-stu-id="6069d-168">Security</span></span>

<span data-ttu-id="6069d-169">MSDTC 및 WS-AT와 관련된 설정 중 일부는 레지스트리의 HKLM\Software\Microsoft\MSDTC 및 HKLM\Software\Microsoft\WSAT에 각각 저장되므로 이러한 레지스트리 키의 보안을 유지하여 관리자만 쓸 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-169">Since some of the settings related to MSDTC and WS-AT are stored in the registry at HKLM\Software\Microsoft\MSDTC and at HKLM\Software\Microsoft\WSAT, respectively, ensure that these registry keys are secured so that only administrators can write to them.</span></span> <span data-ttu-id="6069d-170">레지스트리 편집기 도구에서 보안을 설정 하려는 키를 마우스 오른쪽 단추로 클릭 하 고 **사용 권한** 을 선택 하 여 적절 한 액세스 제어를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-170">In the Registry Editor tool, right-click the key you want to secure and select **Permission** to set the appropriate access control.</span></span> <span data-ttu-id="6069d-171">시스템의 보안과 무결성을 유지하려면 권한이 낮은 사용자에 대해 중요한 키를 읽기 전용으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-171">It is crucial to the security and integrity of the system that important keys are read-only for low-privileged users.</span></span>

<span data-ttu-id="6069d-172">MSDTC를 배포하는 경우 관리자는 MSDTC 데이터 교환의 보안을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-172">When deploying MSDTC, the administrator must ensure that any MSDTC data interchange is secure.</span></span> <span data-ttu-id="6069d-173">작업 그룹 배포에서는 트랜잭션 인프라를 악의적인 사용자로부터 격리합니다. 클러스터 배포에서는 클러스터 레지스트리의 보안을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-173">In a workgroup deployment, isolate the transactional infrastructure from malicious users; in a cluster deployment, secure the cluster registry.</span></span>

## <a name="tracing"></a><span data-ttu-id="6069d-174">추적</span><span class="sxs-lookup"><span data-stu-id="6069d-174">Tracing</span></span>

<span data-ttu-id="6069d-175">WS-AT 프로토콜 서비스는 ws-atomictransaction [구성 MMC 스냅인](../ws-atomictransaction-configuration-mmc-snap-in.md) 도구를 사용 하 여 사용 하도록 설정 하 고 관리할 수 있는 통합 된 트랜잭션 관련 추적을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-175">The WS-AT protocol service supports integrated, transaction-specific tracing that can be enabled and managed through the use of the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) tool.</span></span> <span data-ttu-id="6069d-176">추적에는 특정 트랜잭션에 대해 인리스트먼트가 수행된 시간, 트랜잭션이 터미널 상태에 도달한 시간, 각 트랜잭션 인리스트먼트가 받은 결과 등을 나타내는 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-176">Traces can include data indicating the time an enlistment is made for a specific transaction, the time a transaction reaches its terminal state, the outcome each transaction enlistment has received.</span></span> <span data-ttu-id="6069d-177">모든 추적은 [서비스 추적 뷰어 도구 (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) 도구를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-177">All traces can be viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tool.</span></span>

<span data-ttu-id="6069d-178">또한 WS-AT 프로토콜 서비스는 ETW 추적 세션을 통해 통합된 ServiceModel 추적을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-178">The WS-AT protocol service also supports integrated ServiceModel tracing through the ETW trace session.</span></span> <span data-ttu-id="6069d-179">이 추적 기능은 기존의 트랜잭션 추적 외에 보다 자세한 통신 관련 추적을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-179">This provides more detailed, communication-specific traces in addition to the existing transaction traces.</span></span>  <span data-ttu-id="6069d-180">이러한 추가 추적을 사용하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-180">To enable these additional traces, follow these steps</span></span>

1. <span data-ttu-id="6069d-181">**시작/실행** 메뉴를 열고 입력 상자에 "regedit"를 입력 한 다음 **확인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-181">Open the **Start/Run** menu, type "regedit" in the input box and select **OK**.</span></span>

2. <span data-ttu-id="6069d-182">**레지스트리 편집기** 의 왼쪽 창에서 다음 폴더로 이동 하 여 \software\microsoft\wsat\3.0\를 Hkey_Local_Machine 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-182">In the **Registry Editor**, navigate to the following folder on the left pane, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\</span></span>

3. <span data-ttu-id="6069d-183">오른쪽 창에서 값을 마우스 오른쪽 단추로 클릭 `ServiceModelDiagnosticTracing` 하 고 **수정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-183">Right-click the `ServiceModelDiagnosticTracing` value in the right pane and select **Modify**.</span></span>

4. <span data-ttu-id="6069d-184">**값 데이터** 입력 상자에 다음 유효한 값 중 하나를 입력 하 여 사용할 추적 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-184">In the **Value data** input box, enter one of the following valid values to specify the trace level you want to enable.</span></span>

- <span data-ttu-id="6069d-185">0: 해제</span><span class="sxs-lookup"><span data-stu-id="6069d-185">0: off</span></span>

- <span data-ttu-id="6069d-186">1: 위험</span><span class="sxs-lookup"><span data-stu-id="6069d-186">1: critical</span></span>

- <span data-ttu-id="6069d-187">3: 오류.</span><span class="sxs-lookup"><span data-stu-id="6069d-187">3: error.</span></span> <span data-ttu-id="6069d-188">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="6069d-188">This is the default value</span></span>

- <span data-ttu-id="6069d-189">7: 경고</span><span class="sxs-lookup"><span data-stu-id="6069d-189">7: warning</span></span>

- <span data-ttu-id="6069d-190">15: 정보</span><span class="sxs-lookup"><span data-stu-id="6069d-190">15: information</span></span>

- <span data-ttu-id="6069d-191">31: 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="6069d-191">31: verbose</span></span>

## <a name="see-also"></a><span data-ttu-id="6069d-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6069d-192">See also</span></span>

- [<span data-ttu-id="6069d-193">WS-AtomicTransaction 구성 유틸리티(wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="6069d-193">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="6069d-194">WS-AtomicTransaction 구성 MMC 스냅인</span><span class="sxs-lookup"><span data-stu-id="6069d-194">WS-AtomicTransaction Configuration MMC Snap-in</span></span>](../ws-atomictransaction-configuration-mmc-snap-in.md)
