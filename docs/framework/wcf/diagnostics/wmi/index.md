---
title: 진단에 Windows Management Instrumentation 사용
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: cb015096f9e7cb815e5bd4e4e5487c03fea49bc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267938"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="a0072-102">진단에 Windows Management Instrumentation 사용</span><span class="sxs-lookup"><span data-stu-id="a0072-102">Using Windows Management Instrumentation for Diagnostics</span></span>

<span data-ttu-id="a0072-103">WCF (Windows Communication Foundation)는 WCF WMI(Windows Management Instrumentation) (WMI) 공급자를 통해 런타임에 서비스의 검사 데이터를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="a0072-104">WMI 사용</span><span class="sxs-lookup"><span data-stu-id="a0072-104">Enabling WMI</span></span>  

 <span data-ttu-id="a0072-105">WMI는 Microsoft에서 구현한 WBEM(Web-Based Enterprise Management) 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="a0072-106">WMI SDK에 대 한 자세한 내용은 [WMI(Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0072-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="a0072-107">WBEM은 애플리케이션에서 외부 관리 도구에 관리 계측을 노출하는 방법을 지정하는 산업 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="a0072-108">WMI 공급자는 WBEM 호환 인터페이스를 통해 런타임으로 계측을 노출하는 구성 요소이며,</span><span class="sxs-lookup"><span data-stu-id="a0072-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="a0072-109">특성/값 쌍을 가진 WMI 개체 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="a0072-110">쌍은 다양한 단순 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="a0072-111">관리 도구는 런타임에 인터페이스를 통해 서비스에 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="a0072-112">WCF는 주소, 바인딩, 동작 및 수신기와 같은 서비스 특성을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="a0072-113">애플리케이션의 구성 파일에서 기본 제공 WMI 공급자를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="a0072-114">이 작업은 `wmiProviderEnabled` [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) 다음 샘플 구성에 표시 된 것 처럼 섹션의 특성을 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a0072-115">이 구성 항목은 WMI 인터페이스를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="a0072-116">관리 애플리케이션이 이 인터페이스를 통해 연결하여 애플리케이션의 관리 계측에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="a0072-117">WMI 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="a0072-117">Accessing WMI Data</span></span>  

 <span data-ttu-id="a0072-118">다양한 방식으로 WMI 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="a0072-119">Microsoft는 스크립트, Visual Basic 응용 프로그램, c + + 응용 프로그램 및 .NET Framework에 WMI Api를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="a0072-120">자세한 내용은 [WMI 사용](/windows/win32/wmisdk/using-wmi)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0072-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a0072-121">.NET Framework에서 제공한 메서드를 사용하여 WMI 데이터를 프로그래밍 방식으로 액세스하는 경우 그와 같은 메서드는 연결이 설정될 때 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="a0072-122">연결은 <xref:System.Management.ManagementObject> 인스턴스를 구성하는 동안에는 설정되지 않고, 실제 데이터 교환을 포함하는 첫 번째 요청에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="a0072-123">따라서 `try..catch` 블록을 사용하여 가능한 예외를 catch해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="a0072-124">WMI에서 `System.ServiceModel` 추적 소스에 대한 메시지 로깅 옵션과 추적 및 메시지 로깅 수준을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="a0072-125">이러한 작업은 부울 속성인,, 및를 노출 하는 [AppDomainInfo](appdomaininfo.md) 인스턴스에 액세스 하 여 수행할 수 있습니다 `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel` `LogMalformedMessages` `TraceLevel` .</span><span class="sxs-lookup"><span data-stu-id="a0072-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="a0072-126">따라서 메시지 로깅을 위한 추적 수신기를 구성하지만 이러한 옵션을 구성에서 `false`로 설정해도, 이후에 애플리케이션 실행 시 `true`로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="a0072-127">이를 통해 메시지 로깅을 런타임에 효과적으로 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="a0072-128">마찬가지로 구성 파일에 메시지 로깅을 활성화하더라도, WMI를 사용하여 런타임에 메시지 로깅을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="a0072-129">구성 파일에서 메시지 로깅에 대한 메시지 로깅 추적 수신기 또는 추적을 위한 `System.ServiceModel` 추적 수신기를 지정하지 않으면, WMI에서 변경이 승인되더라도 변경 내용이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="a0072-130">각 수신기를 올바르게 설정 하는 방법에 대 한 자세한 내용은 [메시지 로깅 구성](../configuring-message-logging.md) 및 [추적 구성](../tracing/configuring-tracing.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0072-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="a0072-131">구성에 지정된 다른 모든 추적 소스의 추적 수준은 애플리케이션이 시작되면 적용되며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="a0072-132">WCF는 `GetOperationCounterInstanceName` 스크립팅에 대 한 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="a0072-133">이 메서드는 작업 이름과 함께 제공된 경우 성능 카운터 인스턴스 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="a0072-134">사용자 입력을 검증하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-134">However, it does not validate your input.</span></span> <span data-ttu-id="a0072-135">따라서 잘못된 작업 이름을 제공하면 잘못된 카운터 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="a0072-136">`OutgoingChannel` `Service` 대상 서비스에 대 한 WCF 클라이언트를 메서드 내에서 만들지 않은 경우 인스턴스의 속성은 서비스에 의해 열린 채널 수를 계산 하 여 다른 서비스에 연결 합니다 `Service` .</span><span class="sxs-lookup"><span data-stu-id="a0072-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="a0072-137">**주의** WMI는 <xref:System.TimeSpan> 최대 3 개의 소수점 값만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="a0072-138">예를 들어, 서비스에서 속성 중 하나를 <xref:System.TimeSpan.MaxValue>로 설정한 경우 해당 값은 WMI를 통해 볼 때 소수점 이하 셋째 자리 이후부터 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="a0072-139">보안</span><span class="sxs-lookup"><span data-stu-id="a0072-139">Security</span></span>  

 <span data-ttu-id="a0072-140">WCF WMI 공급자는 환경에서 서비스를 검색할 수 있기 때문에 액세스 권한을 부여 하는 데 매우 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="a0072-141">기본 관리자 전용 액세스를 완화하면 충분히 신뢰할 수 없는 대상이 사용자 환경의 중요 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="a0072-142">특히 원격 WMI 액세스에 대한 권한을 완화하면 자원 소모 공격이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="a0072-143">과도한 WMI 요청으로 프로세스 자원이 소모되면 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="a0072-144">또한 MOF 파일에 대한 액세스 권한을 완화하면 충분히 신뢰할 수 없는 대상이 WMI 동작을 조작하고 WMI 스키마에 로드된 개체를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="a0072-145">예를 들어, 필드를 제거하여 중요 데이터를 관리자가 보지 못하도록 숨기거나, 채워지지 않거나 예외가 발생한 필드를 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="a0072-146">기본적으로 WCF WMI 공급자는 관리자에 게 "메서드 실행", "공급자 쓰기", "계정 사용" 권한 및 ASP.NET, 로컬 서비스 및 네트워크 서비스에 대 한 "계정 사용" 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="a0072-147">특히 Windows Vista 이외의 플랫폼에서는 ASP.NET 계정에 WMI ServiceModel 네임 스페이스에 대 한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="a0072-148">특정 사용자 그룹에 이러한 권한을 부여하지 않으려면 WMI 공급자를 비활성화하거나(기본값) 해당 사용자 그룹에 대한 액세스 권한을 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="a0072-149">또한 구성을 통해 WMI를 활성화할 경우 사용자 권한이 부족하여 WMI가 활성화되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="a0072-150">그러나 이 오류를 기록하기 위해 이벤트가 이벤트 로그에 기록되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="a0072-151">사용자 권한 수준을 수정하려면 다음 단계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="a0072-152">시작을 클릭 하 고 실행을 클릭 한 다음 **compmgmt.msc** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="a0072-153">**서비스 및 응용 프로그램/WMI 컨트롤** 을 마우스 오른쪽 단추로 클릭 하 여 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="a0072-154">**보안** 탭을 선택 하 고 **Root/ServiceModel** 네임 스페이스로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="a0072-155">**보안** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="a0072-156">액세스를 제어 하려는 특정 그룹 또는 사용자를 선택 하 고 **허용** 또는 **거부** 확인란을 사용 하 여 사용 권한을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="a0072-157">추가 사용자에게 WCF WMI 등록 권한 부여</span><span class="sxs-lookup"><span data-stu-id="a0072-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  

 <span data-ttu-id="a0072-158">WCF는 “분리된 공급자”라고도 하는 in-process WMI 공급자를 호스트하여</span><span class="sxs-lookup"><span data-stu-id="a0072-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="a0072-159">"분리 된 공급자" 라고도 하는 in-process WMI 공급자를 호스트 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="a0072-160">노출할 관리 데이터에 대해 이 공급자를 등록하는 계정에는 적절한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="a0072-161">Windows에서는 기본적으로 권한이 있는 소수의 계정 집합만이 분리된 공급자를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="a0072-162">그러나 사용자는 대개 기본 집합에 포함되지 않은 계정에서 실행 중인 WCF 서비스의 WMI 데이터를 노출하려고 하므로 이는 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="a0072-163">이 권한을 제공하려면 관리자가 다음 사용 권한을 다음과 같은 순서로 추가 계정에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="a0072-164">WCF WMI 네임스페이스 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="a0072-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="a0072-165">WCF 분리된 WMI 공급자 등록 권한</span><span class="sxs-lookup"><span data-stu-id="a0072-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="a0072-166">WMI 네임스페이스 액세스 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="a0072-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="a0072-167">다음 PowerShell 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="a0072-168">이 PowerShell 스크립트는 SDDL (Security Descriptor Definition Language)을 사용 하 여 Built-In 사용자 그룹에 "root/servicemodel" WMI 네임 스페이스에 대 한 액세스 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="a0072-169">다음 ACL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="a0072-170">BA(Built-In Administrator) – 이미 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="a0072-171">NS(Network Service) – 이미 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="a0072-172">LS(Local System) – 이미 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="a0072-173">Built-In Users – 권한을 부여할 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="a0072-174">공급자 등록 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="a0072-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="a0072-175">다음 PowerShell 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="a0072-176">임의의 사용자 또는 그룹에 권한 부여</span><span class="sxs-lookup"><span data-stu-id="a0072-176">Granting Access to Arbitrary Users or Groups</span></span>  

 <span data-ttu-id="a0072-177">이 단원의 예제에서는 모든 로컬 사용자에게 WMI 공급자 등록 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="a0072-178">기본 제공 되지 않은 사용자 또는 그룹에 대 한 액세스 권한을 부여 하려면 해당 사용자 또는 그룹의 SID (보안 식별자)를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="a0072-179">임의 사용자의 SID를 가져오는 간단한 방법은 없지만,</span><span class="sxs-lookup"><span data-stu-id="a0072-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="a0072-180">원하는 사용자로 로그온한 후에 다음 셸 명령을 실행하는 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="a0072-181">그러면 현재 사용자의 SID가 제공되기는 하지만, 이 방법을 통해 모든 임의 사용자의 SID를 가져올 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="a0072-182">SID를 가져오는 또 다른 방법은 관리 작업을 위해 Windows 2000 Resource Kit 도구에서 [getsid.exe](/windows/win32/wmisdk/using-wmi) 도구를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="a0072-183">이 도구는 두 사용자(로컬 또는 도메인)의 SID를 비교하는데, 두 SID를 명령줄에 인쇄한다는 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="a0072-184">자세한 내용은 [잘 알려진 sid](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a0072-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="a0072-185">원격 WMI 개체 인스턴스 액세스</span><span class="sxs-lookup"><span data-stu-id="a0072-185">Accessing Remote WMI Object Instances</span></span>  

 <span data-ttu-id="a0072-186">원격 컴퓨터의 WCF WMI 인스턴스에 액세스 해야 하는 경우 액세스에 사용 하는 도구에서 패킷 개인 정보를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="a0072-187">다음 단원에서는 WMI CIM Studio, Windows Management Instrumentation Tester 및 .NET SDK 2.0을 사용하여 이러한 작업을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="a0072-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="a0072-188">WMI CIM Studio</span></span>

<span data-ttu-id="a0072-189">Wmi 관리 도구를 설치한 경우 wmi CIM Studio를 사용 하 여 WMI 인스턴스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-189">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="a0072-190">도구는 다음 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-190">The tools are in the following folder:</span></span>
  
<span data-ttu-id="a0072-191">*%windir%\Program Files\wmi tools\ 도구\\*</span><span class="sxs-lookup"><span data-stu-id="a0072-191">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="a0072-192">**네임 스페이스에 연결:** 창에서 **root\ServiceModel** 를 입력 하 고 **확인을 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="a0072-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="a0072-193">**WMI CIM Studio 로그인** 창에서 **옵션 >>** 단추를 클릭 하 여 창을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="a0072-194">**인증 수준** 에 대 한 **패킷 개인 정보** 를 선택 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="a0072-195">Windows Management Instrumentation Tester</span><span class="sxs-lookup"><span data-stu-id="a0072-195">Windows Management Instrumentation Tester</span></span>  

 <span data-ttu-id="a0072-196">이 도구는 Windows에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-196">This tool is installed by Windows.</span></span> <span data-ttu-id="a0072-197">이를 실행 하려면 **시작/실행** 대화 상자에 **cmd.exe** 를 입력 하 고 **확인** 을 클릭 하 여 명령 콘솔을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="a0072-198">그런 다음 명령 창에 **wbemtest.exe** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="a0072-199">Windows Management Instrumentation Tester 도구가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="a0072-200">창의 오른쪽 위 모퉁이에 있는 **연결** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="a0072-201">새 창에서 **네임 스페이스** 필드에 **root\ServiceModel** 을 입력 하 고 **인증 수준** 에 대해 **패킷 개인 정보** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="a0072-202">**연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="a0072-203">관리 코드 사용</span><span class="sxs-lookup"><span data-stu-id="a0072-203">Using Managed Code</span></span>  

 <span data-ttu-id="a0072-204"><xref:System.Management> 네임스페이스에서 제공한 클래스를 사용하여 원격 WMI 인스턴스를 프로그래밍 방식으로 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="a0072-205">다음 코드 샘플에서는 이를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a0072-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
