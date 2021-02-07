---
description: '자세한 정보: WS-AtomicTransaction 구성 MMC 스냅인'
title: WS-AtomicTransaction 구성 MMC 스냅인
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 5f1ac32a98b93a3ec3edb9cfa31ae0ebf424aba8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676302"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a><span data-ttu-id="aa793-103">WS-AtomicTransaction 구성 MMC 스냅인</span><span class="sxs-lookup"><span data-stu-id="aa793-103">WS-AtomicTransaction Configuration MMC snap-in</span></span>

<span data-ttu-id="aa793-104">WS-AtomicTransaction 구성 MMC 스냅인은 로컬 및 원격 컴퓨터 모두에서 WS-AtomicTransaction 설정의 일부를 구성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-104">The WS-AtomicTransaction Configuration MMC snap-in is used to configure a portion of the WS-AtomicTransaction settings on both local and remote machines.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa793-105">설명</span><span class="sxs-lookup"><span data-stu-id="aa793-105">Remarks</span></span>

<span data-ttu-id="aa793-106">Windows XP 또는 Windows Server 2003를 실행 하는 경우 **제어판/관리 도구/구성 요소 서비스/** 로 이동 하 여 **내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하 여 MMC 스냅인을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-106">If you are running Windows XP or Windows Server 2003, the MMC snap-in can be found by navigating to **Control Panel/Administrative Tools/Component Services/**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="aa793-107">이 위치는 MSDTC를 구성할 수 있는 위치와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-107">This is the same location where you can configure the MSDTC.</span></span> <span data-ttu-id="aa793-108">구성에 사용할 수 있는 옵션은 **ws-at** 탭에서 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-108">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

 <span data-ttu-id="aa793-109">Windows Vista 또는 Windows Server 2008를 실행 하는 경우 **시작** 단추를 클릭 하 고 `dcomcnfg.exe` **검색** 상자에를 입력 하 여 MMC 스냅인을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-109">If you are running Windows Vista or Windows Server 2008, MMC snap-in can be found by clicking the **Start** button, and typing in `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="aa793-110">MMC를 열면 **My Computer\Distributed Transaction COORDINATOR\LOCAL DTC** 노드로 이동 하 고 마우스 오른쪽 단추를 클릭 한 다음 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-110">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="aa793-111">구성에 사용할 수 있는 옵션은 **ws-at** 탭에서 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-111">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

 <span data-ttu-id="aa793-112">앞의 단계는 로컬 컴퓨터를 구성하기 위한 스냅인을 시작하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-112">The previous steps are used to launch the snap-in for configuring a local machine.</span></span> <span data-ttu-id="aa793-113">원격 컴퓨터를 구성 하려면 **제어판/관리 도구/구성 요소 서비스/** 에서 원격 컴퓨터의 이름을 찾고, windows XP 또는 windows Server 2003를 실행 하는 경우 비슷한 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-113">If you want to configure a remote machine, you should locate the remote machine's name in **Control Panel/Administrative Tools/Component Services/**, and perform similar steps if you are running Windows XP or Windows Server 2003.</span></span> <span data-ttu-id="aa793-114">Windows Vista 또는 Windows Server 2008를 실행 하는 경우 Vista 및 Windows Server 2008의 이전 단계를 수행 하지만 원격 컴퓨터의 노드에서 **Distributed Transaction COORDINATOR\LOCAL DTC** 노드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-114">If you are running Windows Vista or Windows Server 2008, follow the previous steps for Vista and Windows Server 2008, but use the **Distributed Transaction Coordinator\Local DTC** node under the remote computer's node.</span></span>

 <span data-ttu-id="aa793-115">도구의 사용자 인터페이스를 사용하려면 다음 경로에 있는 WsatUI.dll 파일을 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-115">To use the user interface provided by the tool, you have to register the WsatUI.dll file, which is located at the following path,</span></span>

 <span data-ttu-id="aa793-116">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span><span class="sxs-lookup"><span data-stu-id="aa793-116">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span></span>

 <span data-ttu-id="aa793-117">다음 명령을 사용하여 등록을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-117">The registration can be done by the following command.</span></span>

```console
regasm.exe /codebase WsatUI.dll
```

 <span data-ttu-id="aa793-118">이 도구를 사용하여 기본 WS-AtomicTransaction 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-118">You can use this tool to modify the basic WS-AtomicTransaction settings.</span></span> <span data-ttu-id="aa793-119">예를 들어, WS-AtomicTransaction 활성화 및 비활성화하고, WS-AT에 대해 HTTP 포트를 구성하고, SSL 인증서를 HTTP 포트에 바인딩하고, 인증서 주체 이름을 지정하여 인증서를 구성하고, 추적 모드를 선택하고, 기본 및 최대 시간 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-119">For example, you can enable and disable the WS-AtomicTransaction protocol support, configure the HTTP ports for WS-AT, bind an SSL Certificate to the HTTP port, configure certificates by specifying certificate subject names, select the Tracing mode and set default and maximum timeouts.</span></span>

 <span data-ttu-id="aa793-120">로컬 컴퓨터 에서만 WS-AtomicTransaction 지원을 구성 해야 하는 경우이 도구의 명령줄 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-120">If you must configure WS-AtomicTransaction support on the local machine only, you can use the command-line version of this tool.</span></span> <span data-ttu-id="aa793-121">명령줄 도구에 대 한 자세한 내용은 [Ws-atomictransaction 구성 유틸리티 (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa793-121">For more information about the command-line tool, see the [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) topic.</span></span>

 <span data-ttu-id="aa793-122">MMC 스냅인과 명령줄 도구 모두 일부 WS-AT 설정 구성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-122">You should be aware that both the MMC Snap-in and the command-line tool do not support configuring all WS-AT settings.</span></span> <span data-ttu-id="aa793-123">이러한 설정은 레지스트리를 직접 수정해야지만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-123">These settings can be edited only by modifying the registry directly.</span></span> <span data-ttu-id="aa793-124">이러한 레지스트리 설정에 대 한 자세한 내용은 [WS-Atomic 트랜잭션 지원 구성](./feature-details/configuring-ws-atomic-transaction-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa793-124">For more information about these registry settings, see [Configuring WS-Atomic Transaction Support](./feature-details/configuring-ws-atomic-transaction-support.md).</span></span>

### <a name="user-interface-description"></a><span data-ttu-id="aa793-125">사용자 인터페이스 설명</span><span class="sxs-lookup"><span data-stu-id="aa793-125">User Interface Description</span></span>

<span data-ttu-id="aa793-126">**WS-Atomic 트랜잭션 네트워크 지원 사용**:</span><span class="sxs-lookup"><span data-stu-id="aa793-126">**Enable WS-Atomic Transaction Network Support**:</span></span>

 <span data-ttu-id="aa793-127">이 확인란을 선택하거나 선택 취소하여 이 스냅인의 모든 GUI 구성 요소를 사용하거나 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-127">Toggling this checkbox enables or disables all the GUI components of this snap-in.</span></span>

 <span data-ttu-id="aa793-128">이 확인란을 선택하기 전에 인바운드 통신이나 아웃바운드 통신 또는 두 통신 모두에서 네트워크 DTC 액세스를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-128">Before you check this box, you should make sure that Network DTC Access is enabled with inbound or outbound communication, or both.</span></span> <span data-ttu-id="aa793-129">이 값은 MSDTC 스냅인의 **보안** 탭에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-129">This value can be verified in the **Security** Tab of the MSDTC snap-in.</span></span>

#### <a name="network-group-box"></a><span data-ttu-id="aa793-130">네트워크 그룹 상자</span><span class="sxs-lookup"><span data-stu-id="aa793-130">Network Group Box</span></span>

<span data-ttu-id="aa793-131">네트워크 그룹에서 SSL 암호화와 같은 HTTPS 포트 및 추가 보안 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-131">You can specify the HTTPS port and additional security settings such as SSL encryption in the Network group.</span></span> <span data-ttu-id="aa793-132">DTC 네트워크 트랜잭션이 활성화되어 있지 않은 경우 이 그룹은 비활성화되어 회색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-132">This group is disabled (grayed out) if DTC Network Transactions are not enabled.</span></span>

 <span data-ttu-id="aa793-133">**HTTPS 포트**</span><span class="sxs-lookup"><span data-stu-id="aa793-133">**HTTPS Port**</span></span>

 <span data-ttu-id="aa793-134">WS-AT에 사용되는 HTTPS 포트의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-134">This is the value of the HTTPS port used for WS-AT.</span></span> <span data-ttu-id="aa793-135">값은 유효한 포트를 나타내는 1-65535 범위의 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-135">The value must be a number in the range 1-65535 (as to represent a valid port).</span></span> <span data-ttu-id="aa793-136">HTTP 포트를 변경하면 HTTP 서비스 구성이 수정됩니다. 즉, 이전에 사용한 WS-AT 서비스 주소가 해제되고 새 WS-AT 서비스 주소가 새 포트에 따라 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-136">Changing the HTTP Port modifies the HTTP Service Configuration, which means that the previously used WS-AT Service Address is released, and a new WS-AT Service Address is registered based on the new port.</span></span> <span data-ttu-id="aa793-137">또한 새로 선택한 포트는 SSL 암호화를 위해 현재 선택한 인증서를 사용하여 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-137">In addition, the newly selected port is encrypted with the currently selected certificate for SSL Encryption.</span></span>

> [!NOTE]
> <span data-ttu-id="aa793-138">이 도구를 실행하기 전에 방화벽을 이미 활성화한 경우 예외 목록에 포트가 자동으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-138">If you have already enabled the firewall before running this tool, the port is automatically registered in the exception list.</span></span> <span data-ttu-id="aa793-139">이 도구를 실행하기 전에 방화벽을 비활성화한 경우 방화벽에 대해 추가로 구성되는 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-139">If the firewall is disabled before running this tool, nothing additional is configured regarding the firewall.</span></span>

 <span data-ttu-id="aa793-140">WS-AT를 구성한 후에 방화벽을 활성화하는 경우 이 도구를 다시 실행하고 이 매개 변수를 사용하여 포트 번호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-140">If you enable the firewall after configuring WS-AT, you must run this tool again and supply the port number using this parameter.</span></span> <span data-ttu-id="aa793-141">구성한 후에 방화벽을 비활성화하는 경우 WS-AT는 추가 입력 없이 계속 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-141">If you disable the firewall after configuring, WS-AT continues to work without additional input.</span></span>

 <span data-ttu-id="aa793-142">**엔드포인트 인증서**</span><span class="sxs-lookup"><span data-stu-id="aa793-142">**Endpoint Certificate**</span></span>

 <span data-ttu-id="aa793-143">**선택** 단추를 클릭 하면 로컬 컴퓨터에서 현재 사용할 수 있는 인증서가 포함 된 목록이 표시 되어 사용자가 SSL 암호화에 사용할 수 있는 인증서를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-143">Clicking the **Select** button displays a list with the currently available certificates on the Local Machine, allowing the user to select the certificate that can be used for SSL encryption.</span></span> <span data-ttu-id="aa793-144">인증서에는 프라이빗 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-144">The certificates must have a private key.</span></span> <span data-ttu-id="aa793-145">그렇지 않으면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-145">Otherwise, you receive an error message.</span></span>

> [!NOTE]
> <span data-ttu-id="aa793-146">선택한 포트에 대한 SSL 인증서를 설정하는 경우 인증서가 있으면 해당 포트와 연결된 원래 SSL 인증서를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-146">When you set an SSL certificate for a selected port, you overwrite the original SSL certificate associated with that port if one exists.</span></span>

 <span data-ttu-id="aa793-147">**허가된 계정**</span><span class="sxs-lookup"><span data-stu-id="aa793-147">**Authorized Accounts**</span></span>

 <span data-ttu-id="aa793-148">선택 단추를 클릭 하면 Windows Access Control 목록 편집기가 호출 됩니다. 그러면 **참여** 권한 그룹의 **허용** 또는 **거부** 상자를 **선택** 하 여 WS-Atomic 트랜잭션에 참여할 수 있는 사용자 또는 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-148">Clicking the **Select** button invokes the Windows Access Control List editor, where you can specify the user or group that can participate in WS-Atomic transactions by checking the **Allow** or **Deny** box in the **Participate** permission group.</span></span>

 <span data-ttu-id="aa793-149">**허가된 인증서**</span><span class="sxs-lookup"><span data-stu-id="aa793-149">**Authorized Certificates**</span></span>

 <span data-ttu-id="aa793-150">**선택** 단추를 클릭 하면 LocalMachine에서 현재 사용할 수 있는 인증서 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-150">Clicking the **Select** button displays a list of currently available certificates on the LocalMachine.</span></span> <span data-ttu-id="aa793-151">그런 다음 WS-Atomic Transaction에 참여시할 수 있는 인증서 ID를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-151">You can then select which certificate identities are allowed to participate in WS-Atomic transactions.</span></span>

#### <a name="timeout-group-box"></a><span data-ttu-id="aa793-152">시간 제한 그룹 상자</span><span class="sxs-lookup"><span data-stu-id="aa793-152">Timeout Group Box</span></span>

<span data-ttu-id="aa793-153">**시간 제한** 그룹 상자를 사용 하 여 WS-Atomic 트랜잭션에 대 한 기본 및 최대 제한 시간을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-153">The **Timeout** group box allows you to specify the default and maximum timeout for a WS-Atomic transaction.</span></span> <span data-ttu-id="aa793-154">보내기 시간 제한의 유효한 값은 1부터 3600까지입니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-154">A valid value for outgoing timeout is between 1 and 3600.</span></span> <span data-ttu-id="aa793-155">받기 시간 제한의 유효한 값은 0에서 3600까지입니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-155">A valid value for incoming timeout is between 0 and 3600.</span></span>

#### <a name="tracing-and-logging-group-box"></a><span data-ttu-id="aa793-156">추적 및 로깅 그룹 상자</span><span class="sxs-lookup"><span data-stu-id="aa793-156">Tracing and Logging Group Box</span></span>

<span data-ttu-id="aa793-157">**추적 및 로깅** 그룹 상자를 사용 하 여 원하는 추적 및 로깅 수준을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-157">The **Tracing and Logging** group box allows you to configure the desired tracing and logging level.</span></span>

 <span data-ttu-id="aa793-158">**옵션** 단추를 클릭 하면 추가 설정을 지정할 수 있는 페이지가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-158">Clicking the **Options** button invokes a page where you can specify additional settings.</span></span>

 <span data-ttu-id="aa793-159">**추적 수준** 조합 상자를 사용 하 여 열거형의 유효한 값 중에서 선택할 수 있습니다 <xref:System.Diagnostics.TraceLevel> .</span><span class="sxs-lookup"><span data-stu-id="aa793-159">The **Trace Level** combination box allows you to choose from any valid value of the <xref:System.Diagnostics.TraceLevel> enumeration.</span></span> <span data-ttu-id="aa793-160">또한 동작 추적 및 동작 전파를 수행할지 또는 개인적으로 식별할 수 있는 정보를 수집할지를 지정하는 확인란을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-160">You can also use the checkboxes to specify if you want to perform activity tracing, activity propagation or collect personal identifiable information.</span></span>

 <span data-ttu-id="aa793-161">로깅 **세션** 그룹 상자에서 로깅 세션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-161">You can also specify logging sessions in the **Logging Session** group box.</span></span>

> [!NOTE]
> <span data-ttu-id="aa793-162">다른 추적 소비자가 WS-AT 추적 공급자를 사용 중인 경우 추적 이벤트에 새 로깅 세션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-162">When another trace consumer is using the WS-AT trace provider, you cannot create a new logging session for trace events.</span></span> <span data-ttu-id="aa793-163">이 시간 동안 로깅을 구성하려고 시도하면 "공급자를 사용하지 못했습니다. 오류 코드: 1" 오류 메시지가</span><span class="sxs-lookup"><span data-stu-id="aa793-163">Any attempt to configure logging during this time results in the error message "Failed to enable provider.</span></span> <span data-ttu-id="aa793-164">표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa793-164">Error code: 1".</span></span>

 <span data-ttu-id="aa793-165">추적 및 로깅에 대 한 자세한 내용은 [관리 및 진단](./diagnostics/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa793-165">For more information about tracing and logging, see [Administration and Diagnostics](./diagnostics/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa793-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa793-166">See also</span></span>

- [<span data-ttu-id="aa793-167">WS-Atomic Transaction 지원 구성</span><span class="sxs-lookup"><span data-stu-id="aa793-167">Configuring WS-Atomic Transaction Support</span></span>](./feature-details/configuring-ws-atomic-transaction-support.md)
- [<span data-ttu-id="aa793-168">WS-AtomicTransaction 구성 유틸리티(wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="aa793-168">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="aa793-169">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="aa793-169">Administration and Diagnostics</span></span>](./diagnostics/index.md)
