---
description: '자세한 정보: WCF와 함께 여러 인증 스키마 사용'
title: WCF와 함께 여러 인증 스키마 사용
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: fd03a13c5d38bbf26e2b6079d1320bc389c9f20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779714"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="6f25b-103">WCF와 함께 여러 인증 스키마 사용</span><span class="sxs-lookup"><span data-stu-id="6f25b-103">Using Multiple Authentication Schemes with WCF</span></span>

<span data-ttu-id="6f25b-104">이제 WCF를 사용하여 단일 엔드포인트에 여러 인증 체계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-104">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="6f25b-105">또한 웹 호스팅 서비스가 IIS에서 직접 인증 설정을 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-105">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="6f25b-106">자체 호스팅 서비스는 사용할 수 있는 인증 체계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-106">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="6f25b-107">IIS에서 인증 설정을 설정 하는 방법에 대 한 자세한 내용은 [Iis 인증](https://go.microsoft.com/fwlink/?LinkId=232458) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f25b-107">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="6f25b-108">IIS에서 호스트되는 서비스</span><span class="sxs-lookup"><span data-stu-id="6f25b-108">IIS-Hosted Services</span></span>  

 <span data-ttu-id="6f25b-109">IIS에서 호스트되는 서비스의 경우 IIS에서 사용할 인증 체계를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-109">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="6f25b-110">그런 다음 서비스의 web.config 파일에서 바인딩 구성의 다음 XML 코드 조각과 같이 clientCredential type을 "InheritedFromHost"로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-110">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="6f25b-111">ServiceAuthenticationBehavior 또는 요소를 사용 하 여 인증 체계의 하위 집합만 서비스에 사용 하도록 지정할 수 있습니다 \<serviceAuthenticationManager> .</span><span class="sxs-lookup"><span data-stu-id="6f25b-111">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="6f25b-112">이를 코드로 구성할 때는 다음 코드 조각에서와 같이 ServiceAuthenticationBehavior를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-112">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="6f25b-113">구성 파일에서이를 구성 하는 경우 \<serviceAuthenticationManager> 다음 XML 조각과 같이 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-113">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="6f25b-114">그러면 IIS에서 선택된 항목에 따라 여기에 나열된 인증 체계의 하위 집합만 서비스 엔드포인트에 적용되는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-114">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="6f25b-115">즉, 개발자는 serviceAuthenticationManager 목록에서 기본 인증을 생략하여 목록에서 기본 인증을 제외할 수 있으며, IIS에서 사용할 수 있는 인증의 경우에도 서비스 엔드포인트에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-115">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="6f25b-116">자체 호스팅 서비스</span><span class="sxs-lookup"><span data-stu-id="6f25b-116">Self-Hosted Services</span></span>  

 <span data-ttu-id="6f25b-117">자체 호스팅 서비스는 설정을 상속할 IIS가 없으므로 약간 다르게 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-117">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="6f25b-118">여기서는 \<serviceAuthenticationManager> element 또는 ServiceAuthenticationBehavior를 사용 하 여 상속 되는 인증 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-118">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="6f25b-119">코드는 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-119">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="6f25b-120">구성은 다음과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-120">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="6f25b-121">그런 다음, 아래 XML 조각에 나와 있는 것처럼 바인딩 설정에 InheritFromHost를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-121">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="6f25b-122">또는 다음 구성 조각에서와 같이 HTTP 전송 바인딩 요소에 인증 체계를 설정하여 사용자 지정 바인딩에 인증 체계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f25b-122">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f25b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f25b-123">See also</span></span>

- [<span data-ttu-id="6f25b-124">바인딩 및 보안</span><span class="sxs-lookup"><span data-stu-id="6f25b-124">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="6f25b-125">엔드포인트: 주소, 바인딩 및 계약</span><span class="sxs-lookup"><span data-stu-id="6f25b-125">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="6f25b-126">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="6f25b-126">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="6f25b-127">사용자 지정 바인딩을 사용하는 보안 기능</span><span class="sxs-lookup"><span data-stu-id="6f25b-127">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6f25b-128">바인딩</span><span class="sxs-lookup"><span data-stu-id="6f25b-128">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="6f25b-129">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="6f25b-129">Custom Bindings</span></span>](../extending/custom-bindings.md)
