---
description: '자세한 정보: 보호 수준 이해'
title: 보호 수준 이해
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 8c6e5bc97c02e9cec4841dac0d7cf8c8b59931e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631712"
---
# <a name="understanding-protection-level"></a><span data-ttu-id="d4841-103">보호 수준 이해</span><span class="sxs-lookup"><span data-stu-id="d4841-103">Understanding Protection Level</span></span>

<span data-ttu-id="d4841-104">`ProtectionLevel` 및 <xref:System.ServiceModel.ServiceContractAttribute> 클래스와 같은 여러 클래스에서 볼 수 있는 <xref:System.ServiceModel.OperationContractAttribute> 속성은</span><span class="sxs-lookup"><span data-stu-id="d4841-104">The `ProtectionLevel` property is found on many different classes, such as the <xref:System.ServiceModel.ServiceContractAttribute> and the <xref:System.ServiceModel.OperationContractAttribute> classes.</span></span> <span data-ttu-id="d4841-105">메시지의 전체나 일부를 보호하는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-105">The property controls how a part (or whole) of a message is protected.</span></span> <span data-ttu-id="d4841-106">이 항목에서는 WCF (Windows Communication Foundation) 기능 및 작동 방식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-106">This topic explains the Windows Communication Foundation (WCF) feature and how it works.</span></span>

<span data-ttu-id="d4841-107">보호 수준을 설정 하는 방법에 대 한 지침은 [방법: ProtectionLevel 속성 설정](how-to-set-the-protectionlevel-property.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4841-107">For instructions on setting the protection level, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d4841-108">구성이 아닌 코드에서만 보호 수준을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-108">Protection levels can be set only in code, not in configuration.</span></span>

## <a name="basics"></a><span data-ttu-id="d4841-109">기본</span><span class="sxs-lookup"><span data-stu-id="d4841-109">Basics</span></span>

<span data-ttu-id="d4841-110">다음과 같은 기본 문을 적용하여 보호 수준 기능을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-110">To understand the protection level feature, the following basic statements apply:</span></span>

- <span data-ttu-id="d4841-111">메시지에 대해 세 가지 기본 보호 수준이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-111">Three basic levels of protection exist for any part of a message.</span></span> <span data-ttu-id="d4841-112">수준 속성은 <xref:System.Net.Security.ProtectionLevel> 열거형 값 중 하나로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-112">The property (wherever it occurs) is set to one of the <xref:System.Net.Security.ProtectionLevel> enumeration values.</span></span> <span data-ttu-id="d4841-113">다음은 낮은 보호 수준에서 높은 보호 수준의 순서로 나열된 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-113">In ascending order of protection, they include:</span></span>

  - <span data-ttu-id="d4841-114">`None`.</span><span class="sxs-lookup"><span data-stu-id="d4841-114">`None`.</span></span>

  - <span data-ttu-id="d4841-115">`Sign`.</span><span class="sxs-lookup"><span data-stu-id="d4841-115">`Sign`.</span></span> <span data-ttu-id="d4841-116">보호되는 부분이 디지털 방식으로 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-116">The protected part is digitally signed.</span></span> <span data-ttu-id="d4841-117">이를 통해 보호된 메시지 부분에 대한 변조를 탐지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-117">This ensures detection of any tampering with the protected message part.</span></span>

  - <span data-ttu-id="d4841-118">`EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="d4841-118">`EncryptAndSign`.</span></span> <span data-ttu-id="d4841-119">메시지 부분이 서명되기 전에 암호화되어 기밀성을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-119">The message part is encrypted to ensure confidentiality before it is signed.</span></span>

- <span data-ttu-id="d4841-120">이 기능을 사용 하 여 *응용 프로그램 데이터* 에 대 한 보호 요구 사항만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-120">You can set protection requirements only for *application data* with this feature.</span></span> <span data-ttu-id="d4841-121">예를 들어 WS-Addressing 헤더는 인프라 데이터이므로 `ProtectionLevel`의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-121">For example, WS-Addressing headers are infrastructure data and, therefore, are not affected by the `ProtectionLevel`.</span></span>

- <span data-ttu-id="d4841-122">보안 모드가 `Transport`로 설정되면 전체 메시지가 전송 메커니즘의 보호를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-122">When the security mode is set to `Transport`, the entire message is protected by the transport mechanism.</span></span> <span data-ttu-id="d4841-123">따라서 메시지의 각 부분에 별도의 보호 수준을 설정하는 것은 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-123">Therefore, setting a separate protection level for different parts of a message has no effect.</span></span>

- <span data-ttu-id="d4841-124">는 `ProtectionLevel` 개발자가 바인딩이 준수 해야 하는 *최소 수준을* 설정 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-124">The `ProtectionLevel` is a way for the developer to set the *minimum level* that a binding must comply with.</span></span> <span data-ttu-id="d4841-125">서비스가 배포되면 구성에 지정된 실제 바인딩은 최소 수준을 지원하거나 지원하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-125">When a service is deployed, the actual binding specified in configuration may or may not support the minimum level.</span></span> <span data-ttu-id="d4841-126">예를 들어 <xref:System.ServiceModel.BasicHttpBinding> 클래스는 보안을 활성화할 수 있더라도 기본적으로 보안을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-126">For example, by default, the <xref:System.ServiceModel.BasicHttpBinding> class does not supply security (although it can be enabled).</span></span> <span data-ttu-id="d4841-127">따라서 `None` 이외의 값으로 설정된 계약에 이 클래스를 사용하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-127">Therefore, using it with a contract that has any setting other than `None` will cause an exception to be thrown.</span></span>

- <span data-ttu-id="d4841-128">서비스에서 모든 메시지에 대 한 최소를 요구 하는 경우 `ProtectionLevel` `Sign` WCF가 아닌 기술로 만들어진 클라이언트는 모든 메시지를 암호화 하 고 서명할 수 있습니다 (최소 필요).</span><span class="sxs-lookup"><span data-stu-id="d4841-128">If the service requires that the minimum `ProtectionLevel` for all messages is `Sign`, a client (perhaps created by a non-WCF technology) can encrypt and sign all messages (which is more than the minimum required).</span></span> <span data-ttu-id="d4841-129">이 경우에는 클라이언트가 최소값 보다 더 많이 수행 되었으므로 WCF에서 예외를 throw 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-129">In this case, WCF will not throw an exception because the client has done more than the minimum.</span></span> <span data-ttu-id="d4841-130">그러나 WCF 응용 프로그램 (서비스 또는 클라이언트)은 가능 하면 메시지 파트를 과도 하 게 보호 하지 않지만 최소 수준을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-130">Note, however, that WCF applications (services or clients) will not over-secure a message part if possible but will comply with the minimum level.</span></span> <span data-ttu-id="d4841-131">또한 `Transport`를 보안 모드로 사용하면, 전송에서 메시지 스트림을 과보호할 수 있는데, 이는 보다 세부적인 수준으로 보호하는 것이 기본적으로 불가능하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-131">Also note that when using `Transport` as the security mode, the transport may over-secure the message stream because it is inherently unable to secure at a more granular level.</span></span>

- <span data-ttu-id="d4841-132">`ProtectionLevel`을 명시적으로 `Sign` 또는 `EncryptAndSign`으로 설정하면 보안이 활성화된 상태에서 바인딩을 사용해야 합니다. 그렇지 않으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-132">If you set the `ProtectionLevel` explicitly to either `Sign` or `EncryptAndSign`, then you must use a binding with security enabled or an exception will be thrown.</span></span>

- <span data-ttu-id="d4841-133">보안이 활성화된 바인딩을 선택하고 계약의 어떤 위치에서도 `ProtectionLevel` 속성을 설정하지 않으면, 모든 애플리케이션 데이터가 암호화되거나 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-133">If you select a binding that enables security and you do not set the `ProtectionLevel` property anywhere on the contract, all application data will be encrypted and signed.</span></span>

- <span data-ttu-id="d4841-134">보안이 활성화되지 않은 바인딩(예: `BasicHttpBinding` 클래스에서는 기본적으로 보안이 비활성화됨)을 선택하고 `ProtectionLevel`이 명시적으로 설정되지 않은 경우 애플리케이션 데이터가 보호되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-134">If you select a binding that does not have security enabled (for example, the `BasicHttpBinding` class has security disabled by default), and the `ProtectionLevel` is not explicitly set, then none of the application data will be protected.</span></span>

- <span data-ttu-id="d4841-135">전송 수준에서 보안을 적용하는 바인딩을 사용하면 모든 애플리케이션 데이터가 전송 기능에 따라 보안되며,</span><span class="sxs-lookup"><span data-stu-id="d4841-135">If you are using a binding that applies security at the transport level, all application data will be secured according to the capabilities of the transport.</span></span>

- <span data-ttu-id="d4841-136">메시지 수준에서 보안을 적용하는 바인딩을 사용하면 애플리케이션 데이터는 계약에 설정된 보호 수준에 따라 보안됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-136">If you use a binding that applies security at the message level, then application data will be secured according to the protection levels set on the contract.</span></span> <span data-ttu-id="d4841-137">보호 수준을 지정하지 않는다면 메시지의 모든 애플리케이션 데이터는 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-137">If you do not specify a protection level, then all application data in the messages will be encrypted and signed.</span></span>

- <span data-ttu-id="d4841-138">`ProtectionLevel`은 다양한 범위 지정 수준에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-138">The `ProtectionLevel` can be set at different scoping levels.</span></span> <span data-ttu-id="d4841-139">범위 지정과 관련된 계층 구조에 대해서는 다음 단원에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-139">There is a hierarchy associated with scoping, which is explained in the next section.</span></span>

## <a name="scoping"></a><span data-ttu-id="d4841-140">범위 지정</span><span class="sxs-lookup"><span data-stu-id="d4841-140">Scoping</span></span>

<span data-ttu-id="d4841-141">맨 위 API에 `ProtectionLevel`을 설정하면 그 아래의 모든 단계에 해당 수준이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-141">Setting the `ProtectionLevel` on the topmost API sets the level for all levels below it.</span></span> <span data-ttu-id="d4841-142">그러나 보다 하위 단계에서 `ProtectionLevel`을 다른 값으로 설정하면, 계층 구조에서 해당 단계 아래에 있는 모든 API가 새 수준으로 다시 설정됩니다. 하지만 그 단계 위에 있는 API에는 맨 위 단계의 영향을 계속해서 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-142">If the `ProtectionLevel` is set to a different value at a lower level, all APIs below that level in the hierarchy will now be reset to the new level (APIs above it, however, will still be affected by the topmost level).</span></span> <span data-ttu-id="d4841-143">계층 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-143">The hierarchy is as follows.</span></span> <span data-ttu-id="d4841-144">동일한 단계에 있는 특성은 피어라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-144">Attributes at the same level are peers.</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a><span data-ttu-id="d4841-145">ProtectionLevel 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="d4841-145">Programming ProtectionLevel</span></span>

<span data-ttu-id="d4841-146">계층 구조 내 임의의 지점에서 `ProtectionLevel`을 프로그래밍하려면 특성을 적용할 때 속성에 적절한 값을 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-146">To program the `ProtectionLevel` at any point in the hierarchy, simply set the property to an appropriate value when applying the attribute.</span></span> <span data-ttu-id="d4841-147">예제 [는 방법: ProtectionLevel 속성 설정](how-to-set-the-protectionlevel-property.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4841-147">For examples, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d4841-148">기본적인 속성과 메시지 계약을 설정하려면 이러한 기능의 작동 방법에 대해 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-148">Setting the property on faults and message contracts requires understanding how those features work.</span></span> <span data-ttu-id="d4841-149">자세한 내용은 [방법: ProtectionLevel 속성 설정](how-to-set-the-protectionlevel-property.md) 및 [메시지 계약 사용](./feature-details/using-message-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4841-149">For more information, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md) and [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>

## <a name="ws-addressing-dependency"></a><span data-ttu-id="d4841-150">WS-Addressing 종속성</span><span class="sxs-lookup"><span data-stu-id="d4841-150">WS-Addressing Dependency</span></span>

<span data-ttu-id="d4841-151">대부분의 경우에는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 클라이언트를 생성 하면 클라이언트와 서비스 계약이 동일 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-151">In most cases, using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a client ensures that the client and service contracts are identical.</span></span> <span data-ttu-id="d4841-152">그러나 표면상 동일한 계약으로 인해 클라이언트에서 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-152">However, seemingly identical contracts can cause the client to throw an exception.</span></span> <span data-ttu-id="d4841-153">이러한 현상은 바인딩이 WS-Addressing 사양을 지원하지 않고 계약에 여러 수준의 보호가 지정된 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-153">This occurs whenever a binding does not support the WS-Addressing specification and multiple levels of protection are specified on the contract.</span></span> <span data-ttu-id="d4841-154">예를 들어 <xref:System.ServiceModel.BasicHttpBinding> 클래스가 사양을 지원하지 않거나, WS-Addressing을 지원하지 않는 사용자 지정 바인딩을 만드는 경우 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-154">For example, the <xref:System.ServiceModel.BasicHttpBinding> class does not support the specification, or if you create a custom binding that does not support WS-Addressing.</span></span> <span data-ttu-id="d4841-155">`ProtectionLevel` 기능에서는 하나의 계약에 여러 개의 보호 수준을 사용할 수 있도록 WS-Addressing 사양을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-155">The `ProtectionLevel` feature relies on the WS-Addressing specification to enable different protection levels on a single contract.</span></span> <span data-ttu-id="d4841-156">바인딩이 WS-Addressing 사양을 지원하지 않으면 모든 단계가 동일한 보호 수준으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-156">If the binding does not support the WS-Addressing specification, all levels will be set to the same protection level.</span></span> <span data-ttu-id="d4841-157">계약의 모든 범위에 대해 유효한 보호 수준은 계약에 사용되는 가장 강력한 보호 수준으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-157">The effective protection level for all scopes on the contract will be set to the strongest protection level used on the contract.</span></span>

<span data-ttu-id="d4841-158">이로 인해 디버깅 작업이 어려울 것처럼 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-158">This may cause a problem that is hard to debug at first glance.</span></span> <span data-ttu-id="d4841-159">둘 이상의 서비스에 대한 메서드를 포함하는 클라이언트 계약(인터페이스)을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-159">It is possible to create a client contract (an interface) that includes methods for more than one service.</span></span> <span data-ttu-id="d4841-160">즉, 여러 서비스와 통신하는 클라이언트를 만드는 데 동일한 인터페이스를 사용할 수 있습니다. 이 단일 인터페이스에는 여러 서비스에 대한 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-160">That is, the same interface is used to create a client that communicates with many services, and the single interface contains methods for all services.</span></span> <span data-ttu-id="d4841-161">이러한 시나리오는 드물지만, 개발자가 각각의 특정 서비스에 적용 가능한 메서드만 호출하려면 더욱 주의를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-161">The developer must take care in this rare scenario to invoke only those methods that are applicable for each particular service.</span></span> <span data-ttu-id="d4841-162">바인딩이 <xref:System.ServiceModel.BasicHttpBinding> 클래스이면 여러 보호 수준이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-162">If the binding is the <xref:System.ServiceModel.BasicHttpBinding> class, multiple protection levels cannot be supported.</span></span> <span data-ttu-id="d4841-163">하지만 클라이언트에 응답하는 서비스는 요구된 보호 수준보다 낮은 수준으로 클라이언트에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-163">However, a service replying to the client might respond to a client with a lower protection level than required.</span></span> <span data-ttu-id="d4841-164">이 경우 클라이언트에서는 더 높은 보호 수준을 필요로 하기 때문에 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-164">In this case, the client will throw an exception because it expects a higher protection level.</span></span>

<span data-ttu-id="d4841-165">이러한 문제는 코드 예제에서 설명하고,</span><span class="sxs-lookup"><span data-stu-id="d4841-165">An example of the code illustrates this problem.</span></span> <span data-ttu-id="d4841-166">다음은 서비스 및 클라이언트 계약을 보여 주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-166">The following example shows a service and a client contract.</span></span> <span data-ttu-id="d4841-167">바인딩이 요소인 것으로 가정 합니다 [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d4841-167">Assume that the binding is the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element.</span></span> <span data-ttu-id="d4841-168">계약에 대한 모든 작업은 동일한 보호 수준을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-168">Therefore, all operations on a contract have the same protection level.</span></span> <span data-ttu-id="d4841-169">이 일관된 보호 수준은 모든 작업에 대한 최대 보호 수준으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-169">This uniform protection level is determined as the maximum protection level across all operations.</span></span>

<span data-ttu-id="d4841-170">서비스 계약은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-170">The service contract is:</span></span>

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

<span data-ttu-id="d4841-171">다음 코드에서는 클라이언트 계약 인터페이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-171">The following code shows the client contract interface.</span></span> <span data-ttu-id="d4841-172">여기에는 다른 서비스에 사용되는 `Tax` 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-172">Note that it includes a `Tax` method that is intended to be used with a different service:</span></span>

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

<span data-ttu-id="d4841-173">클라이언트가 `Price` 메서드를 호출할 경우 서비스로부터 회신을 받으면 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-173">When the client calls the `Price` method, it throws an exception when it receives a reply from the service.</span></span> <span data-ttu-id="d4841-174">이는 클라이언트가 `ProtectionLevel`에 `ServiceContractAttribute`을 지정하지 않아 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> 메서드를 포함한 모든 메서드에 기본값(`Price`)을 사용하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-174">This occurs because the client does not specify a `ProtectionLevel` on the `ServiceContractAttribute`, and therefore the client uses the default (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) for all methods, including the `Price` method.</span></span> <span data-ttu-id="d4841-175">하지만 서비스 계약에서는 보호 수준이 <xref:System.Net.Security.ProtectionLevel.Sign>으로 설정된 하나의 메서드를 정의하므로, 서비스에서 <xref:System.Net.Security.ProtectionLevel.Sign> 수준을 사용하여 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-175">However, the service returns the value using the <xref:System.Net.Security.ProtectionLevel.Sign> level because the service contract defines a single method that has its protection level set to <xref:System.Net.Security.ProtectionLevel.Sign>.</span></span> <span data-ttu-id="d4841-176">이 경우 클라이언트에서는 서비스 응답에 대한 유효성 검사를 할 때 오류를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="d4841-176">In this case, the client will throw an error when validating the response from the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4841-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4841-177">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [<span data-ttu-id="d4841-178">서비스에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="d4841-178">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="d4841-179">방법: ProtectionLevel 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d4841-179">How to: Set the ProtectionLevel Property</span></span>](how-to-set-the-protectionlevel-property.md)
- [<span data-ttu-id="d4841-180">계약 및 서비스에서 오류 지정 및 처리</span><span class="sxs-lookup"><span data-stu-id="d4841-180">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="d4841-181">메시지 계약 사용</span><span class="sxs-lookup"><span data-stu-id="d4841-181">Using Message Contracts</span></span>](./feature-details/using-message-contracts.md)
