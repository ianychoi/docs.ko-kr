---
description: 다음에 대해 자세히 알아보세요. <bindings>
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 2cf5b42b8478e34a528cd36435023cac62bf0c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639382"
---
# \<bindings>

<span data-ttu-id="a049d-102">요소를 사용 `bindings` 하 여 WCF (Windows Communication Foundation)에 대 한 표준 및 사용자 지정 바인딩의 컬렉션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a049d-103">각 항목은 고유한 `binding`으로 식별될 수 있는 `name` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="a049d-104">서비스에서는 `name`을 통해 바인딩을 연결하여 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="a049d-105">.NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a049d-106">기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a049d-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="a049d-107">시스템 제공 바인딩</span><span class="sxs-lookup"><span data-stu-id="a049d-107">System-provided bindings</span></span>

<span data-ttu-id="a049d-108">시스템 제공 바인딩은 WCF 메시지 스택의 복잡성을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a049d-109">시스템 제공 바인딩을 사용하는 애플리케이션은 스택을 완전히 제어할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a049d-110">각 시스템 제공 바인딩에는 바인딩이 처리하는 사용 시나리오에 가장 적합한 특성이 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="a049d-111">각 시스템 제공 바인딩의 구성 섹션은 바인딩 구성에 사용되는 일부 구성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a049d-112">각 구성은 고유한 이름으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-112">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="a049d-113">시스템 제공 바인딩에는 요소나 특성을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a049d-114">이렇게 하려면 [사용자 지정](#custom-bindings) 바인딩 섹션에 설명 된 대로 사용자 지정 바인딩을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="a049d-115">시스템에서 제공 하는 바인딩을 완벽 하 게 모방 하는 사용자 지정 바인딩을 정의 하 고 사용자 응용 프로그램에서 제어를 원하는 몇 가지 설정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="a049d-116">시스템 제공 바인딩 목록은 [시스템 제공 바인딩](../../../wcf/system-provided-bindings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a049d-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="a049d-117">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="a049d-117">Custom bindings</span></span>

<span data-ttu-id="a049d-118">사용자 지정 바인딩은 WCF 메시징 스택에 대한 모든 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a049d-119">개별 바인딩에서는 스택에 나타나는 순서대로 스택 요소의 구성 요소를 지정함으로써 메시지 스택을 정의하며,</span><span class="sxs-lookup"><span data-stu-id="a049d-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a049d-120">각 요소는 스택의 한 요소를 정의 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="a049d-121">각 사용자 지정 바인딩에는 `transport` 요소가 하나만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a049d-122">이 요소가 없으면 메시징 스택이 완전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-122">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="a049d-123">스택에서 요소가 나타나는 순서는 작업이 메시지에 적용되는 순서이므로 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a049d-124">다음과 같은 스택 요소 순서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-124">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="a049d-125">Transactions(선택적)</span><span class="sxs-lookup"><span data-stu-id="a049d-125">Transactions (optional)</span></span>  

2. <span data-ttu-id="a049d-126">안정적인 메시징 (옵션)</span><span class="sxs-lookup"><span data-stu-id="a049d-126">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="a049d-127">Security(선택적)</span><span class="sxs-lookup"><span data-stu-id="a049d-127">Security (optional)</span></span>  

4. <span data-ttu-id="a049d-128">인코더</span><span class="sxs-lookup"><span data-stu-id="a049d-128">Encoder</span></span>  

5. <span data-ttu-id="a049d-129">전송</span><span class="sxs-lookup"><span data-stu-id="a049d-129">Transport</span></span>  

 <span data-ttu-id="a049d-130">사용자 지정 바인딩은 `name` 특성으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="a049d-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="a049d-131">사용자 지정 바인딩에 대 한 자세한 내용은 [사용자 지정 바인딩](../../../wcf/extending/custom-bindings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a049d-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a049d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a049d-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="a049d-133">바인딩</span><span class="sxs-lookup"><span data-stu-id="a049d-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a049d-134">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="a049d-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
