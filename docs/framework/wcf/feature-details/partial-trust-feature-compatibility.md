---
title: 부분 신뢰 기능 호환성
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: baf7758bc83419a68f900aa51233006ecb61d8e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247995"
---
# <a name="partial-trust-feature-compatibility"></a><span data-ttu-id="d480e-102">부분 신뢰 기능 호환성</span><span class="sxs-lookup"><span data-stu-id="d480e-102">Partial Trust Feature Compatibility</span></span>

<span data-ttu-id="d480e-103">WCF (Windows Communication Foundation)는 부분적으로 신뢰할 수 있는 환경에서 실행 될 때 제한 된 기능의 하위 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-103">Windows Communication Foundation (WCF) supports a limited subset of functionality when running in a partially-trusted environment.</span></span> <span data-ttu-id="d480e-104">부분 신뢰에서 지원되는 기능은 [Supported Deployment Scenarios](supported-deployment-scenarios.md) 항목에서 설명한 대로 특정 시나리오 집합을 바탕으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-104">The features supported in partial trust are designed around a specific set of scenarios as described in the [Supported Deployment Scenarios](supported-deployment-scenarios.md) topic.</span></span>  
  
## <a name="minimum-permission-requirements"></a><span data-ttu-id="d480e-105">최소 권한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d480e-105">Minimum Permission Requirements</span></span>  

 <span data-ttu-id="d480e-106">WCF는 다음 표준 명명 된 권한 집합 중 하나에서 실행 되는 응용 프로그램의 기능 하위 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-106">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>  
  
- <span data-ttu-id="d480e-107">보통 신뢰 권한</span><span class="sxs-lookup"><span data-stu-id="d480e-107">Medium Trust permissions</span></span>  
  
- <span data-ttu-id="d480e-108">인터넷 영역 권한</span><span class="sxs-lookup"><span data-stu-id="d480e-108">Internet Zone permissions</span></span>  
  
 <span data-ttu-id="d480e-109">더 제한적인 권한이 있는 부분 신뢰 응용 프로그램에서 WCF를 사용 하려고 하면 런타임에 보안 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-109">Attempting to use WCF in partially-trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>  
  
## <a name="contracts"></a><span data-ttu-id="d480e-110">계약</span><span class="sxs-lookup"><span data-stu-id="d480e-110">Contracts</span></span>  

 <span data-ttu-id="d480e-111">부분 신뢰에서 계약을 실행할 때 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-111">Contracts are subject to the following restrictions when running under partial trust:</span></span>  
  
- <span data-ttu-id="d480e-112">`[ServiceContract]` 인터페이스를 구현하는 서비스 클래스가 `public` 이어야 하며 `public` 생성자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-112">The service class that implements the `[ServiceContract]` interface must be `public` and have a `public` constructor.</span></span> <span data-ttu-id="d480e-113">서비스 클래스가 `[OperationContract]` 메서드를 정의하는 경우 이 메서드는 `public`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-113">If it defines `[OperationContract]` methods, these must be `public`.</span></span> <span data-ttu-id="d480e-114">서비스 클래스가 `[ServiceContract]` 인터페이스를 구현하는 경우에는 `private`인터페이스가 `[ServiceContract]` 일 때 이러한 메서드 구현이 명시적 또는 `public`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-114">If it instead implements a `[ServiceContract]` interface, those method implementations can be explicit or `private`, provided that the `[ServiceContract]` interface is `public`.</span></span>  
  
- <span data-ttu-id="d480e-115">`[ServiceKnownType]` 특성을 사용할 때는 지정된 메서드가 `public`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-115">When using the `[ServiceKnownType]` attribute, the method specified must be `public`.</span></span>  
  
- <span data-ttu-id="d480e-116">`[MessageContract]` 클래스와 해당 멤버는 `public`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-116">`[MessageContract]` classes and their members can be `public`.</span></span> <span data-ttu-id="d480e-117">`[MessageContract]` 클래스는 애플리케이션 어셈블리에 정의되어 있는 경우 `internal` 일 수 있으며 `internal` 멤버를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-117">If the `[MessageContract]` class is defined in the application assembly it can be `internal` and have `internal` members.</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="d480e-118">시스템 제공 바인딩</span><span class="sxs-lookup"><span data-stu-id="d480e-118">System-Provided Bindings</span></span>  

 <span data-ttu-id="d480e-119"><xref:System.ServiceModel.BasicHttpBinding> 및 <xref:System.ServiceModel.WebHttpBinding> 은 부분 신뢰 환경에서 완전히 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-119">The <xref:System.ServiceModel.BasicHttpBinding> and <xref:System.ServiceModel.WebHttpBinding> are fully supported in a partial trust environment.</span></span> <span data-ttu-id="d480e-120"><xref:System.ServiceModel.WSHttpBinding> 은 전송 보안 모드에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-120">The <xref:System.ServiceModel.WSHttpBinding> is supported for Transport security mode only.</span></span>  
  
 <span data-ttu-id="d480e-121"><xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>또는 <xref:System.ServiceModel.NetMsmqBinding>과 같이 HTTP 이외의 전송을 사용하는 바인딩은 부분 신뢰 환경에서 실행하는 경우 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-121">Bindings that use transports other than HTTP, such as the <xref:System.ServiceModel.NetTcpBinding>, the <xref:System.ServiceModel.NetNamedPipeBinding>, or the <xref:System.ServiceModel.NetMsmqBinding>, are not supported when running in a partial trust environment.</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="d480e-122">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="d480e-122">Custom Bindings</span></span>  

 <span data-ttu-id="d480e-123">사용자 지정 바인딩을 부분 신뢰 환경에서 만들어 사용할 수 있지만 이 단원에 지정되어 있는 제한 사항을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-123">Custom bindings can be created and used in a partial trust environment, but must follow the restrictions specified in this section.</span></span>  
  
### <a name="transports"></a><span data-ttu-id="d480e-124">전송</span><span class="sxs-lookup"><span data-stu-id="d480e-124">Transports</span></span>  

 <span data-ttu-id="d480e-125">유일하게 허용된 전송 바인딩 요소는 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 및 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>입니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-125">The only allowed transport binding elements are <xref:System.ServiceModel.Channels.HttpTransportBindingElement> and <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
### <a name="encoders"></a><span data-ttu-id="d480e-126">인코더</span><span class="sxs-lookup"><span data-stu-id="d480e-126">Encoders</span></span>  

 <span data-ttu-id="d480e-127">다음 인코더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-127">The following encoders are allowed:</span></span>  
  
- <span data-ttu-id="d480e-128">텍스트 인코더(<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="d480e-128">The text encoder (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="d480e-129">이진 인코더(<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="d480e-129">The binary encoder (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).</span></span>  
  
- <span data-ttu-id="d480e-130">웹 메시지 인코더(<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>)</span><span class="sxs-lookup"><span data-stu-id="d480e-130">The Web Message encoder (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).</span></span>  
  
 <span data-ttu-id="d480e-131">MTOM(Message Transmission Optimization Mechanism) 인코더는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-131">The Message Transmission Optimization Mechanism (MTOM) encoders are not supported.</span></span>  
  
### <a name="security"></a><span data-ttu-id="d480e-132">보안</span><span class="sxs-lookup"><span data-stu-id="d480e-132">Security</span></span>  

 <span data-ttu-id="d480e-133">부분적으로 신뢰할 수 있는 응용 프로그램은 통신을 보호 하기 위해 WCF의 전송 수준 보안 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-133">Partially-trusted applications can use WCF's transport-level security features for securing their communication.</span></span> <span data-ttu-id="d480e-134">메시지 수준 보안은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-134">Message-level security is not supported.</span></span> <span data-ttu-id="d480e-135">메시지 수준 보안을 사용하도록 바인딩을 구성할 경우 런타임에 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-135">Configuring a binding to use message-level security results in an exception at runtime.</span></span>  
  
### <a name="unsupported-bindings"></a><span data-ttu-id="d480e-136">지원되지 않는 바인딩</span><span class="sxs-lookup"><span data-stu-id="d480e-136">Unsupported Bindings</span></span>  

 <span data-ttu-id="d480e-137">신뢰할 수 있는 메시징, 트랜잭션 또는 메시지 수준 보안을 사용하는 바인딩은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-137">Bindings that use reliable messaging, transactions, or message-level security are not supported.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="d480e-138">Serialization</span><span class="sxs-lookup"><span data-stu-id="d480e-138">Serialization</span></span>  

 <span data-ttu-id="d480e-139"><xref:System.Runtime.Serialization.DataContractSerializer> 및 <xref:System.Xml.Serialization.XmlSerializer> 는 모두 부분 신뢰 환경에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-139">Both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported in a partial trust environment.</span></span> <span data-ttu-id="d480e-140">그러나 <xref:System.Runtime.Serialization.DataContractSerializer> 의 사용은 다음 조건에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-140">However, use of the <xref:System.Runtime.Serialization.DataContractSerializer> is subject to the following conditions:</span></span>  
  
- <span data-ttu-id="d480e-141">serialize할 수 있는 모든 `[DataContract]` 형식은 `public`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-141">All serializable `[DataContract]` types must be `public`.</span></span>  
  
- <span data-ttu-id="d480e-142">`[DataMember]` 형식의 serialize할 수 있는 모든 `[DataContract]` 필드 또는 속성은 public이고 읽기/쓰기가 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-142">All serializable `[DataMember]` fields or properties in a `[DataContract]` type must be public and read/write.</span></span> <span data-ttu-id="d480e-143">부분적으로 신뢰할 수 있는 응용 프로그램에서 WCF를 실행 하는 경우 [읽기 전용](https://go.microsoft.com/fwlink/?LinkID=98854) 필드의 serialization 및 deserialization은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-143">The serialization and deserialization of [readonly](https://go.microsoft.com/fwlink/?LinkID=98854) fields is not supported when running WCF in a partially-trusted application.</span></span>  
  
- <span data-ttu-id="d480e-144">`[Serializable]`/ISerializable 프로그래밍 모델은 부분 신뢰 환경에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-144">The `[Serializable]`/ISerializable programming model is not supported in a partial trust environment.</span></span>  
  
- <span data-ttu-id="d480e-145">코드 또는 시스템 수준 구성(machine.config)에서는 알려진 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-145">Known types must be specified in code or machine-level configuration (machine.config).</span></span> <span data-ttu-id="d480e-146">보안상의 이유로 애플리케이션 수준 구성에서는 알려진 형식을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-146">Known types cannot be specified in application-level configuration for security reasons.</span></span>  
  
- <span data-ttu-id="d480e-147"><xref:System.Runtime.Serialization.IObjectReference> 를 구현하는 형식은 부분 신뢰 환경에서 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-147">Types that implement <xref:System.Runtime.Serialization.IObjectReference> throw an exception in a partially-trusted environment.</span></span>  
  
 <span data-ttu-id="d480e-148">부분적으로 신뢰할 수 있는 애플리케이션에서 [T:System.Runtime.Serialization.DataContractSerializer](partial-trust-best-practices.md) 를 안전하게 사용하는 경우의 보안에 대한 자세한 내용은 <xref:System.Runtime.Serialization.DataContractSerializer> 의 Serialization 단원을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d480e-148">See the Serialization section in [Partial Trust Best Practices](partial-trust-best-practices.md) for more information about security when using <xref:System.Runtime.Serialization.DataContractSerializer> safely in a partially-trusted application.</span></span>  
  
### <a name="collection-types"></a><span data-ttu-id="d480e-149">컬렉션 형식</span><span class="sxs-lookup"><span data-stu-id="d480e-149">Collection Types</span></span>  

 <span data-ttu-id="d480e-150">일부 컬렉션 형식은 <xref:System.Collections.Generic.IEnumerable%601> 및 <xref:System.Collections.IEnumerable>을 모두 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-150">Some collection types implement both <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="d480e-151">예제에는 <xref:System.Collections.Generic.ICollection%601>을 구현하는 형식이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-151">Examples include types that implement <xref:System.Collections.Generic.ICollection%601>.</span></span> <span data-ttu-id="d480e-152">이러한 형식은 `public` 의 `GetEnumerator()`구현 및 `GetEnumerator()`의 명시적 구현을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-152">Such types can implement a `public` implementation of `GetEnumerator()`, and an explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="d480e-153">이 경우 <xref:System.Runtime.Serialization.DataContractSerializer> 는 `public` 의 명시적 구현이 아니라 `GetEnumerator()`의 `GetEnumerator()`구현을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-153">In this case, <xref:System.Runtime.Serialization.DataContractSerializer> invokes the `public` implementation of `GetEnumerator()`, and not the explicit implementation of `GetEnumerator()`.</span></span> <span data-ttu-id="d480e-154">`GetEnumerator()` 구현이 모두 `public` 이 아니고 모든 구현이 명시적 구현인 경우 <xref:System.Runtime.Serialization.DataContractSerializer> 는 `IEnumerable.GetEnumerator()`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-154">If none of the `GetEnumerator()` implementations are `public` and all are explicit implementations, then <xref:System.Runtime.Serialization.DataContractSerializer> invokes `IEnumerable.GetEnumerator()`.</span></span>  
  
 <span data-ttu-id="d480e-155">WCF가 부분 신뢰 환경에서 실행 되는 경우 컬렉션 형식의 경우, 구현 중 어떤 것도 `GetEnumerator()` `public` 없거나 명시적 인터페이스 구현인 항목이 없으면 보안 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-155">For collection types when WCF is running in a partial trust environment, if none of the `GetEnumerator()` implementations are `public`, or none of them are explicit interface implementations, then a security exception is thrown.</span></span>  
  
### <a name="netdatacontractserializer"></a><span data-ttu-id="d480e-156">NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="d480e-156">NetDataContractSerializer</span></span>  

 <span data-ttu-id="d480e-157"><xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> 및 <xref:System.Collections.Hashtable> 와 같은 많은 .NET Framework 컬렉션 형식은 부분 신뢰의 <xref:System.Runtime.Serialization.NetDataContractSerializer> 에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-157">Many .NET Framework collection types such as <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.Hashtable> are not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span> <span data-ttu-id="d480e-158">이러한 형식에는 `[Serializable]` 특성이 설정되어 있으며 앞의 Serialization 단원에서 설명한 것처럼 이 특성은 부분 신뢰에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-158">These types have the `[Serializable]` attribute set, and as stated previously in the Serialization section, this attribute is not supported in partial trust.</span></span> <span data-ttu-id="d480e-159"><xref:System.Runtime.Serialization.DataContractSerializer> 는 컬렉션을 특별한 방법으로 다루기 때문에 이 제한을 해결할 수 있지만 <xref:System.Runtime.Serialization.NetDataContractSerializer> 에 이 제한 사항을 피할 수 있는 이러한 메커니즘이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-159">The <xref:System.Runtime.Serialization.DataContractSerializer> treats collections in a special way and is thus able to get around this restriction, but the <xref:System.Runtime.Serialization.NetDataContractSerializer> has no such mechanism to circumvent this restriction.</span></span>  
  
 <span data-ttu-id="d480e-160"><xref:System.DateTimeOffset> 형식은 부분 신뢰의 <xref:System.Runtime.Serialization.NetDataContractSerializer> 에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-160">The <xref:System.DateTimeOffset> type is not supported by the <xref:System.Runtime.Serialization.NetDataContractSerializer> in partial trust.</span></span>  
  
 <span data-ttu-id="d480e-161">서로게이트는 부분 신뢰에서 실행할 때 <xref:System.Runtime.Serialization.NetDataContractSerializer> 메커니즘을 사용하여 <xref:System.Runtime.Serialization.SurrogateSelector> 와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-161">A surrogate cannot be used with the <xref:System.Runtime.Serialization.NetDataContractSerializer> (using the <xref:System.Runtime.Serialization.SurrogateSelector> mechanism) when running in partial trust.</span></span> <span data-ttu-id="d480e-162">이러한 제한 사항은 서로게이트를 사용하는 경우에만 적용되며 서로게이트를 serialize하는 경우에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-162">Note that this restriction applies to using a surrogate, not to serializing it.</span></span>  
  
## <a name="enabling-common-behaviors-to-run"></a><span data-ttu-id="d480e-163">일반 동작이 실행되도록 설정</span><span class="sxs-lookup"><span data-stu-id="d480e-163">Enabling Common Behaviors to Run</span></span>  

 <span data-ttu-id="d480e-164">구성 파일의 섹션에 추가 된 특성 (APTCA)으로 표시 되지 않은 서비스 또는 끝점 동작은 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 응용 프로그램이 부분 신뢰 환경에서 실행 될 때 실행 되지 않으며,이 경우 예외가 throw 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-164">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment and no exception is thrown when this occurs.</span></span> <span data-ttu-id="d480e-165">일반 동작을 실행하려면 다음 옵션 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-165">To enforce the running of common behaviors, you must do one of the following options:</span></span>  
  
- <span data-ttu-id="d480e-166">부분 신뢰 애플리케이션으로 배포될 때 실행될 수 있도록 일반 동작을 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 특성으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-166">Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a partial trust application.</span></span> <span data-ttu-id="d480e-167">APTCA로 표시된 어셈블리가 실행되지 않도록 컴퓨터에 레지스트리 항목을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-167">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running.</span></span> <span data-ttu-id="d480e-168">.</span><span class="sxs-lookup"><span data-stu-id="d480e-168">.</span></span>  
  
- <span data-ttu-id="d480e-169">부분 신뢰 환경에서 애플리케이션을 실행하기 위해 사용자가 코드 액세스 보안 설정을 수정할 수 없는 완전 신뢰 애플리케이션으로서 애플리케이션이 배포되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-169">Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a partial trust environment.</span></span> <span data-ttu-id="d480e-170">사용자가 보안 설정을 수정할 수 있는 경우 동작이 실행되지 않고 예외가 throw되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-170">If they can do so, the behavior does not run and no exception is thrown.</span></span> <span data-ttu-id="d480e-171">이를 확인 하려면Caspol.exe 사용 하 여 **levelfinal** 옵션 [ (코드 액세스 보안 정책 도구)](../../tools/caspol-exe-code-access-security-policy-tool.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d480e-171">To ensure this, see the **levelfinal** option using [Caspol.exe (Code Access Security Policy Tool)](../../tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
 <span data-ttu-id="d480e-172">일반적인 동작에 대 한 예제는 [방법: 엔터프라이즈에서 끝점 잠그기](../extending/how-to-lock-down-endpoints-in-the-enterprise.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d480e-172">For an example of a common behavior, see [How to: Lock Down Endpoints in the Enterprise](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d480e-173">구성</span><span class="sxs-lookup"><span data-stu-id="d480e-173">Configuration</span></span>  

 <span data-ttu-id="d480e-174">한 가지 예외를 제외 하 고 부분적으로 신뢰할 수 있는 코드는 로컬 파일의 WCF 구성 섹션만 로드할 수 있습니다 `app.config` .</span><span class="sxs-lookup"><span data-stu-id="d480e-174">With one exception, partially-trusted code can only load WCF configuration sections in the local `app.config` file.</span></span> <span data-ttu-id="d480e-175">machine.config 또는 루트 web.config 파일에서 WCF 섹션을 참조 하는 WCF 구성 섹션을 로드 하려면 ConfigurationPermission (제한 없음)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-175">To load WCF configuration sections that reference WCF sections in machine.config or in a root web.config file requires ConfigurationPermission(Unrestricted).</span></span> <span data-ttu-id="d480e-176">이 권한이 없으면 로컬 구성 파일 외부에 있는 WCF 구성 섹션 (동작, 바인딩)을 참조할 때 구성이 로드 될 때 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-176">Without this permission, references to WCF configuration sections (behaviors, bindings) outside of the local configuration file results in an exception when the configuration is loaded.</span></span>  
  
 <span data-ttu-id="d480e-177">한 가지 예외는 이 항목의 Serialization 단원에서 설명한 것처럼 serialization에 대한 알려진 형식 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-177">The one exception is known-type configuration for serialization, as described in the Serialization section of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d480e-178">구성 확장은 완전 신뢰에서 실행되는 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-178">Configuration extensions are only supported when running under Full Trust.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="d480e-179">진단</span><span class="sxs-lookup"><span data-stu-id="d480e-179">Diagnostics</span></span>  
  
### <a name="event-logging"></a><span data-ttu-id="d480e-180">이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="d480e-180">Event Logging</span></span>  

 <span data-ttu-id="d480e-181">제한된 이벤트 로깅은 부분 신뢰에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-181">Limited event logging is supported under partial trust.</span></span> <span data-ttu-id="d480e-182">서비스 활성화 오류 및 추적/메시지 로깅 실패만 이벤트 로그에 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-182">Only service activation faults and tracing/message logging failures are logged to the Event Log.</span></span> <span data-ttu-id="d480e-183">이벤트에 너무 많은 메시지를 기록하지 않도록 프로세스에서 로깅할 수 있는 최대 이벤트 수가 5로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-183">The maximum number of events that can be logged by a process is 5, to avoid writing excessive messages to the Event Log.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="d480e-184">메시지 로깅</span><span class="sxs-lookup"><span data-stu-id="d480e-184">Message Logging</span></span>  

 <span data-ttu-id="d480e-185">WCF가 부분 신뢰 환경에서 실행 되는 경우 메시지 로깅이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-185">Message logging does not work when WCF is run in a partial trust environment.</span></span> <span data-ttu-id="d480e-186">부분 신뢰에서 사용하도록 설정된 경우 서비스 활성화는 실패하지 않지만 메시지가 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-186">If enabled under partial trust, it does not fail service activation, but no message is logged.</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="d480e-187">추적</span><span class="sxs-lookup"><span data-stu-id="d480e-187">Tracing</span></span>  

 <span data-ttu-id="d480e-188">제한된 추적 기능은 부분 신뢰 환경에서 실행하는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-188">Restricted tracing functionality is available when running in a partial trust environment.</span></span> <span data-ttu-id="d480e-189">`listeners`구성 파일의 <> 요소에서 추가할 수 있는 형식은 <xref:System.Diagnostics.TextWriterTraceListener> 및 새로운 뿐 <xref:System.Diagnostics.EventSchemaTraceListener> 입니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-189">In the <`listeners`> element in the configuration file, the only types that you can add are <xref:System.Diagnostics.TextWriterTraceListener> and the new <xref:System.Diagnostics.EventSchemaTraceListener>.</span></span> <span data-ttu-id="d480e-190">표준 <xref:System.Diagnostics.XmlWriterTraceListener> 를 사용하면 로그가 불완전하거나 잘못될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-190">Use of the standard <xref:System.Diagnostics.XmlWriterTraceListener> may result in incomplete or incorrect logs.</span></span>  
  
 <span data-ttu-id="d480e-191">지원되는 추적 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-191">Supported trace sources are:</span></span>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <span data-ttu-id="d480e-192"><xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors> 및 <xref:System.IdentityModel.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="d480e-192"><xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, and <xref:System.IdentityModel.Tokens>.</span></span>  
  
 <span data-ttu-id="d480e-193">다음 추적 소스는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-193">The following trace sources are not supported:</span></span>  
  
- <span data-ttu-id="d480e-194">CardSpace</span><span class="sxs-lookup"><span data-stu-id="d480e-194">CardSpace</span></span>  
  
- <xref:System.IO.Log>  

- <span data-ttu-id="d480e-195">[System.servicemodel. TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span><span class="sxs-lookup"><span data-stu-id="d480e-195">[System.ServiceModel.Internal.TransactionBridge](/previous-versions/aa346556(v=vs.110))]</span></span>
  
 <span data-ttu-id="d480e-196"><xref:System.Diagnostics.TraceOptions> 열거형에 대한 다음 멤버는 지정하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-196">The following members of the <xref:System.Diagnostics.TraceOptions> enumeration should not be specified:</span></span>  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 <span data-ttu-id="d480e-197">부분 신뢰 환경에서 추적을 사용하는 경우 애플리케이션에 추적 수신기의 출력을 저장할 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-197">When using tracing in a partial trust environment, ensure that the application has sufficient permissions to store the output of the trace listener.</span></span> <span data-ttu-id="d480e-198">예를 들어 <xref:System.Diagnostics.TextWriterTraceListener> 를 사용하여 추적 출력을 텍스트 파일에 기록하는 경우 애플리케이션에 추적 파일을 기록하는 데 필요한 FileIOPermission이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-198">For example, when using the <xref:System.Diagnostics.TextWriterTraceListener> to write trace output to a text file, ensure that the application has the necessary FileIOPermission required to successfully write to the trace file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d480e-199">중복 오류가 발생 한 추적 파일의 초과를 방지 하기 위해 WCF는 첫 번째 보안 실패 후 리소스 또는 작업 추적을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-199">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="d480e-200">처음으로 리소스에 액세스하거나 작업을 수행할 때 실패한 각 리소스 액세스에 대해 한 가지 예외 추적이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-200">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="wcf-service-host"></a><span data-ttu-id="d480e-201">WCF 서비스 호스트</span><span class="sxs-lookup"><span data-stu-id="d480e-201">WCF Service Host</span></span>  

 <span data-ttu-id="d480e-202">WCF 서비스 호스트는 부분 신뢰를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-202">WCF service host does not support partial trust.</span></span> <span data-ttu-id="d480e-203">부분 신뢰에서 WCF 서비스를 사용 하려면 서비스를 빌드하기 위해 Visual Studio에서 WCF 서비스 라이브러리 프로젝트 템플릿을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d480e-203">If you want to use a WCF service in partial trust, do not use the WCF Service Library Project template in Visual Studio to build your service.</span></span> <span data-ttu-id="d480e-204">대신 wcf 부분 신뢰가 지원 되는 웹 서버에서 서비스를 호스팅할 수 있는 WCF 서비스 웹 사이트 템플릿을 선택 하 여 Visual Studio에서 새 웹 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-204">Instead, create a new Web site in Visual Studio by choosing the WCF service Web site template, which can host the service in a Web server on which WCF partial trust is supported.</span></span>  
  
## <a name="other-limitations"></a><span data-ttu-id="d480e-205">기타 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d480e-205">Other Limitations</span></span>  

  <span data-ttu-id="d480e-206">WCF는 일반적으로 호스팅 응용 프로그램에서 적용 되는 보안 고려 사항으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-206">WCF is generally limited to the security considerations imposed upon it by the hosting application.</span></span> <span data-ttu-id="d480e-207">예를 들어 WCF가 XBAP (XAML 브라우저 응용 프로그램)에서 호스트 되는 경우 [Windows Presentation Foundation 부분 신뢰 보안](/dotnet/desktop/wpf/wpf-partial-trust-security)에 설명 된 대로 xbap 제한의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-207">For example, if WCF is hosted in a XAML Browser Application (XBAP), it is subject to XBAP limitations, as described in [Windows Presentation Foundation Partial Trust Security](/dotnet/desktop/wpf/wpf-partial-trust-security).</span></span>  
  
 <span data-ttu-id="d480e-208">다음 추가 기능은 indigo2를 부분 신뢰 환경에서 실행하는 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-208">The following additional features are not enabled when running indigo2 in a partial trust environment:</span></span>  
  
- <span data-ttu-id="d480e-209">Windows Management Instrumentation(WMI)</span><span class="sxs-lookup"><span data-stu-id="d480e-209">Windows Management Instrumentation (WMI)</span></span>  
  
- <span data-ttu-id="d480e-210">이벤트 로깅은 부분적으로만 사용할 수 있습니다( **진단** 단원에서의 설명 참조).</span><span class="sxs-lookup"><span data-stu-id="d480e-210">Event logging is only partially enabled (see discussion in **Diagnostics** section).</span></span>  
  
- <span data-ttu-id="d480e-211">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="d480e-211">Performance counters</span></span>  
  
 <span data-ttu-id="d480e-212">부분 신뢰 환경에서 지원 되지 않는 WCF 기능을 사용할 경우 런타임에 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-212">Use of WCF features that are not supported in a partial trust environment may result in exceptions at runtime.</span></span>  
  
## <a name="unlisted-features"></a><span data-ttu-id="d480e-213">목록에 없는 기능</span><span class="sxs-lookup"><span data-stu-id="d480e-213">Unlisted Features</span></span>  

 <span data-ttu-id="d480e-214">부분 신뢰 환경에서 실행할 때 사용할 수 없는 정보 또는 작업 부분을 검색하는 가장 좋은 방법은 리소스에 액세스하거나 `try` 블록 내의 작업을 수행한 다음 오류를 `catch` 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-214">The best way to discover that a piece of information or action is unavailable when running in a partial trust environment is to try to access the resource or do the action inside of a `try` block, and then `catch` the failure.</span></span> <span data-ttu-id="d480e-215">중복 오류가 발생 한 추적 파일의 초과를 방지 하기 위해 WCF는 첫 번째 보안 실패 후 리소스 또는 작업 추적을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-215">To avoid flooding the trace files with duplicate errors, WCF disables tracing of the resource or action after the first security failure.</span></span> <span data-ttu-id="d480e-216">처음으로 리소스에 액세스하거나 작업을 수행할 때 실패한 각 리소스 액세스에 대해 한 가지 예외 추적이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d480e-216">There is one exception trace for each failed resource access, the first time an attempt is made to access the resource or perform the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d480e-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d480e-217">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="d480e-218">지원되는 배포 시나리오</span><span class="sxs-lookup"><span data-stu-id="d480e-218">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)
- [<span data-ttu-id="d480e-219">부분 신뢰를 위한 최선의 방법</span><span class="sxs-lookup"><span data-stu-id="d480e-219">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)
