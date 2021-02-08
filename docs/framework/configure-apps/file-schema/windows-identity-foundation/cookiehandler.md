---
description: 다음에 대해 자세히 알아보세요. <cookieHandler>
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 036646ca5c8aaedebba9466ecb8c9232e87a773d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786579"
---
# \<cookieHandler>

<span data-ttu-id="c09ce-102"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM)에서 쿠키를 읽고 쓰는 데 사용 하는를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-102">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="c09ce-103">구문</span><span class="sxs-lookup"><span data-stu-id="c09ce-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c09ce-104">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c09ce-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c09ce-105">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c09ce-106">특성</span><span class="sxs-lookup"><span data-stu-id="c09ce-106">Attributes</span></span>  
  
|<span data-ttu-id="c09ce-107">attribute</span><span class="sxs-lookup"><span data-stu-id="c09ce-107">Attribute</span></span>|<span data-ttu-id="c09ce-108">설명</span><span class="sxs-lookup"><span data-stu-id="c09ce-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c09ce-109">name</span><span class="sxs-lookup"><span data-stu-id="c09ce-109">name</span></span>|<span data-ttu-id="c09ce-110">작성 된 모든 쿠키의 기본 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-110">Specifies the base name for any cookies written.</span></span> <span data-ttu-id="c09ce-111">기본값은 "FedAuth"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-111">The default is "FedAuth".</span></span>|  
|<span data-ttu-id="c09ce-112">path</span><span class="sxs-lookup"><span data-stu-id="c09ce-112">path</span></span>|<span data-ttu-id="c09ce-113">작성 된 모든 쿠키에 대 한 경로 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-113">Specifies the path value for any cookies written.</span></span> <span data-ttu-id="c09ce-114">기본값은 "HttpRuntime. AppDomainAppVirtualPath"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-114">The default is "HttpRuntime.AppDomainAppVirtualPath".</span></span>|  
|<span data-ttu-id="c09ce-115">mode</span><span class="sxs-lookup"><span data-stu-id="c09ce-115">mode</span></span>|<span data-ttu-id="c09ce-116"><xref:System.IdentityModel.Services.CookieHandlerMode>SAM에서 사용 하는 쿠키 처리기의 종류를 지정 하는 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-116">One of the <xref:System.IdentityModel.Services.CookieHandlerMode> values that specifies the kind of cookie handler used by the SAM.</span></span> <span data-ttu-id="c09ce-117">다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-117">The following values may be used:</span></span><br /><br /> <span data-ttu-id="c09ce-118">-"Default"-"청크 분할"과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-118">-   "Default" — The same as "Chunked".</span></span><br /><span data-ttu-id="c09ce-119">-"청크 분할"-클래스의 인스턴스를 사용 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-119">-   "Chunked" — Uses an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="c09ce-120">이 쿠키 처리기는 개별 쿠키가 설정 된 최대 크기를 초과 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-120">This cookie handler ensures that individual cookies do not exceed a set maximum size.</span></span> <span data-ttu-id="c09ce-121">이는 잠재적으로 논리 쿠키 하나를 실시간으로 많은 쿠키에 "청크" 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-121">It accomplishes this by potentially "chunking" one logical cookie into a number of cookies on-the-wire.</span></span><br /><span data-ttu-id="c09ce-122">-"Custom" —에서 파생 된 사용자 지정 클래스의 인스턴스를 사용 <xref:System.IdentityModel.Services.CookieHandler> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-122">-   "Custom" — Uses an instance of a custom class derived from <xref:System.IdentityModel.Services.CookieHandler>.</span></span> <span data-ttu-id="c09ce-123">파생 된 클래스는 자식 요소에서 참조 됩니다 `<customCookieHandler>` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-123">The derived class is referenced by the `<customCookieHandler>` child element.</span></span><br /><br /> <span data-ttu-id="c09ce-124">기본값은 "Default"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-124">The default is "Default".</span></span>|  
|<span data-ttu-id="c09ce-125">persistentSessionLifetime</span><span class="sxs-lookup"><span data-stu-id="c09ce-125">persistentSessionLifetime</span></span>|<span data-ttu-id="c09ce-126">영구적 세션의 수명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-126">Specifies the lifetime of persistent sessions.</span></span> <span data-ttu-id="c09ce-127">0이면 임시 세션이 항상 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-127">If zero, transient sessions are always used.</span></span> <span data-ttu-id="c09ce-128">기본값은 임시 세션을 지정 하는 "0:0:0"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-128">The default value is "0:0:0", which specifies a transient session.</span></span> <span data-ttu-id="c09ce-129">최대값은 365 일의 세션을 지정 하는 "365:0:0"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-129">The maximum value is "365:0:0", which specifies a session of 365 days.</span></span> <span data-ttu-id="c09ce-130">값은 다음 제한 사항에 따라 지정 해야 합니다. `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` 여기서 왼쪽 값은 일을 지정 하 고, 중간 값 (있는 경우)은 시간을 지정 하 고, 가장 오른쪽 값 (있는 경우)은 분을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-130">The value should be specified according to the following restriction: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, where the leftmost value specifies days, the middle value (if present) specifies hours, and the rightmost value (if present) specifies minutes.</span></span>|  
|<span data-ttu-id="c09ce-131">requireSsl</span><span class="sxs-lookup"><span data-stu-id="c09ce-131">requireSsl</span></span>|<span data-ttu-id="c09ce-132">작성 된 모든 쿠키에 대해 "보안" 플래그를 내보낼지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-132">Specifies whether the "Secure" flag is emitted for any cookies written.</span></span> <span data-ttu-id="c09ce-133">이 값을 설정 하면 로그인 세션 쿠키는 HTTPS를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-133">If this value is set, the sign-in session cookies will only be available over HTTPS.</span></span> <span data-ttu-id="c09ce-134">기본값은 "true"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-134">The default is "true".</span></span>|  
|<span data-ttu-id="c09ce-135">hideFromScript</span><span class="sxs-lookup"><span data-stu-id="c09ce-135">hideFromScript</span></span>|<span data-ttu-id="c09ce-136">작성 된 쿠키에 대 한 "HttpOnly" 플래그는 내보내집니다 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-136">Controls whether the "HttpOnly" flag is emitted for any cookies written.</span></span> <span data-ttu-id="c09ce-137">특정 웹 브라우저는 클라이언트 쪽 스크립트가 쿠키 값에 액세스 하지 못하도록 하 여이 플래그를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-137">Certain web browsers honor this flag by keeping client-side script from accessing the cookie value.</span></span> <span data-ttu-id="c09ce-138">기본값은 "true"입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-138">The default is "true".</span></span>|  
|<span data-ttu-id="c09ce-139">도메인</span><span class="sxs-lookup"><span data-stu-id="c09ce-139">domain</span></span>|<span data-ttu-id="c09ce-140">작성 된 모든 쿠키에 대 한 도메인 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-140">The domain value for any cookies written.</span></span> <span data-ttu-id="c09ce-141">기본값은 ""입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-141">The default is "".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c09ce-142">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c09ce-142">Child Elements</span></span>  
  
|<span data-ttu-id="c09ce-143">요소</span><span class="sxs-lookup"><span data-stu-id="c09ce-143">Element</span></span>|<span data-ttu-id="c09ce-144">설명</span><span class="sxs-lookup"><span data-stu-id="c09ce-144">Description</span></span>|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|<span data-ttu-id="c09ce-145">를 구성 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-145">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="c09ce-146">`mode` `<cookieHandler>` 요소의 특성이 "Default" 또는 "청크 분할" 인 경우에만이 요소가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-146">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>|  
|[\<customCookieHandler>](customcookiehandler.md)|<span data-ttu-id="c09ce-147">사용자 지정 쿠키 처리기 형식을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-147">Sets the custom cookie handler type.</span></span> <span data-ttu-id="c09ce-148">`mode` `<cookieHandler>` 요소의 특성이 "Custom" 이면이 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-148">This element must be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="c09ce-149">특성의 다른 값에 대해서는 사용할 수 없습니다 `mode` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-149">It cannot be present for any other values of the `mode` attribute.</span></span> <span data-ttu-id="c09ce-150">사용자 지정 형식은 클래스에서 파생 되어야 합니다 <xref:System.IdentityModel.Services.CookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="c09ce-150">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c09ce-151">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c09ce-151">Parent Elements</span></span>  
  
|<span data-ttu-id="c09ce-152">요소</span><span class="sxs-lookup"><span data-stu-id="c09ce-152">Element</span></span>|<span data-ttu-id="c09ce-153">설명</span><span class="sxs-lookup"><span data-stu-id="c09ce-153">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="c09ce-154"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) 및 (SAM)을 구성 하는 설정을 포함 합니다 <xref:System.IdentityModel.Services.SessionAuthenticationModule> .</span><span class="sxs-lookup"><span data-stu-id="c09ce-154">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c09ce-155">설명</span><span class="sxs-lookup"><span data-stu-id="c09ce-155">Remarks</span></span>  

 <span data-ttu-id="c09ce-156">는 <xref:System.IdentityModel.Services.CookieHandler> HTTP 프로토콜 수준에서 원시 쿠키를 읽고 쓰는 역할을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-156">The <xref:System.IdentityModel.Services.CookieHandler> is responsible for reading and writing raw cookies at the HTTP protocol level.</span></span> <span data-ttu-id="c09ce-157"><xref:System.IdentityModel.Services.ChunkedCookieHandler>또는 클래스에서 파생 된 사용자 지정 쿠키 처리기를 구성할 수 있습니다 <xref:System.IdentityModel.Services.CookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="c09ce-157">You can configure either a <xref:System.IdentityModel.Services.ChunkedCookieHandler> or a custom cookie handler derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="c09ce-158">청크 분할 된 쿠키 처리기를 구성 하려면 mode 특성을 "청크 분할" 또는 "기본값"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-158">To configure a chunked cookie handler, set the mode attribute to "Chunked" or "Default".</span></span> <span data-ttu-id="c09ce-159">기본 청크 크기는 2000 바이트 이지만 선택적으로 자식 요소를 포함 하 여 다른 청크 크기를 지정할 수 있습니다 `<chunkedCookieHandler>` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-159">The default chunk size is 2000 bytes, but you may optionally specify a different chunk size by including a `<chunkedCookieHandler>` child element.</span></span>  
  
 <span data-ttu-id="c09ce-160">사용자 지정 쿠키 처리기를 구성 하려면 mode 특성을 "Custom"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-160">To configure a custom cookie handler, set the mode attribute to "Custom".</span></span> <span data-ttu-id="c09ce-161">또한 `<customCookieHandler>` 사용자 지정 처리기의 형식을 참조 하는 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-161">You must also specify a `<customCookieHandler>` child element that references the type of your custom handler.</span></span>  
  
 <span data-ttu-id="c09ce-162">합니다 `<cookieHandler>` 에서 요소가 표시 되는 <xref:System.IdentityModel.Services.CookieHandlerElement> 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-162">The `<cookieHandler>` element is represented by the <xref:System.IdentityModel.Services.CookieHandlerElement> class.</span></span> <span data-ttu-id="c09ce-163">구성에 지정 된 쿠키 처리기는 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> 속성에 설정 된 개체의 속성에서 사용할 수 있습니다 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c09ce-163">The cookie handler that was specified in configuration is available from the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> property of the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c09ce-164">예제</span><span class="sxs-lookup"><span data-stu-id="c09ce-164">Example</span></span>  

 <span data-ttu-id="c09ce-165">다음 XML에서는 요소를 보여 줍니다 `<cookieHandler>` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-165">The following XML shows a `<cookieHandler>` element.</span></span> <span data-ttu-id="c09ce-166">이 예제에서는 특성을 지정 하지 않았기 때문에 `mode` SAM에서 기본 쿠키 처리기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-166">In this example, because the `mode` attribute is not specified, the default cookie handler will be used by the SAM.</span></span> <span data-ttu-id="c09ce-167">클래스의 인스턴스입니다 <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="c09ce-167">This is an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="c09ce-168">`<chunkedCookieHandler>`자식 요소가 지정 되지 않았기 때문에 기본 청크 크기가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-168">Because the `<chunkedCookieHandler>` child element is not specified, the default chunk size will be used.</span></span> <span data-ttu-id="c09ce-169">특성이 설정 되었으므로 HTTPS가 필요 하지 않습니다 `requireSsl` `false` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-169">HTTPS will not be required because the `requireSsl` attribute is set `false`.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="c09ce-170">이 예제에서는 세션 쿠키를 작성 하는 데 HTTPS가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-170">In this example, HTTPS is not required to write session cookies.</span></span> <span data-ttu-id="c09ce-171">이는 `requireSsl` 요소의 특성이로 설정 되어 있기 때문입니다 `<cookieHandler>` `false` .</span><span class="sxs-lookup"><span data-stu-id="c09ce-171">This is because the `requireSsl` attribute on the `<cookieHandler>` element is set to `false`.</span></span> <span data-ttu-id="c09ce-172">이 설정은 보안 위험을 초래할 수 있으므로 대부분의 프로덕션 환경에는 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c09ce-172">This setting is not recommended for most production environments as it may present a security risk.</span></span>  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c09ce-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c09ce-173">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
