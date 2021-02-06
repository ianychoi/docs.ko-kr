---
description: '에 대 한 자세한 <certificate> 정보: <identity>'
title: <identity>의 경우 <certificate>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: b1ccda7e8e84825cc0b2b2be123fe30be449189a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639109"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="28645-103">\<identity>의 경우 \<certificate></span><span class="sxs-lookup"><span data-stu-id="28645-103">\<certificate> for \<identity></span></span>

<span data-ttu-id="28645-104">클라이언트에 서버의 유효성을 검사하는 데 사용되는 X.509 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28645-104">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="28645-105">요소 값을 설정 하는 방법에 대 한 자세한 내용은 [서비스 id 및 인증](../../../wcf/feature-details/service-identity-and-authentication.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28645-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="28645-106">구문</span><span class="sxs-lookup"><span data-stu-id="28645-106">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28645-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="28645-107">Attributes and Elements</span></span>  

 <span data-ttu-id="28645-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="28645-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28645-109">특성</span><span class="sxs-lookup"><span data-stu-id="28645-109">Attributes</span></span>  
  
|<span data-ttu-id="28645-110">attribute</span><span class="sxs-lookup"><span data-stu-id="28645-110">Attribute</span></span>|<span data-ttu-id="28645-111">설명</span><span class="sxs-lookup"><span data-stu-id="28645-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28645-112">encodedValue</span><span class="sxs-lookup"><span data-stu-id="28645-112">encodedValue</span></span>|<span data-ttu-id="28645-113">인증서의 Base64 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="28645-113">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28645-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="28645-114">Child Elements</span></span>  

 <span data-ttu-id="28645-115">없음</span><span class="sxs-lookup"><span data-stu-id="28645-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28645-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="28645-116">Parent Elements</span></span>  
  
|<span data-ttu-id="28645-117">요소</span><span class="sxs-lookup"><span data-stu-id="28645-117">Element</span></span>|<span data-ttu-id="28645-118">설명</span><span class="sxs-lookup"><span data-stu-id="28645-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="28645-119">클라이언트에서 인증할 서비스의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28645-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28645-120">예제</span><span class="sxs-lookup"><span data-stu-id="28645-120">Example</span></span>  

 <span data-ttu-id="28645-121">다음 코드에서는 클라이언트에 서버의 유효성을 검사하는 데 사용되는 인코딩된 인증서 표현을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28645-121">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="28645-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28645-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="28645-123">서비스 ID 및 인증</span><span class="sxs-lookup"><span data-stu-id="28645-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
