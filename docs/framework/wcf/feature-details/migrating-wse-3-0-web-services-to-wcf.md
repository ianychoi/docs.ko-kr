---
description: '자세한 정보: WSE 3.0 웹 서비스를 WCF로 마이그레이션'
title: WSE 3.0 웹 서비스를 WCF로 마이그레이션
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 92ba60410747399e7a58944c08a082d56fc524d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733738"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 웹 서비스를 WCF로 마이그레이션

WSE 3.0 웹 서비스를 Windows Communication Foundation (WCF)로 마이그레이션하는 경우의 이점에는 향상 된 성능 및 추가 전송, 추가 보안 시나리오 및 WS-* 사양이 지원 됩니다. WSE 3.0에서 WCF로 마이그레이션된 웹 서비스는 최대 200%에서 400% 성능 개선을 경험할 수 있습니다. WCF에서 지 원하는 전송에 대 한 자세한 내용은 [전송 선택](choosing-a-transport.md)을 참조 하세요. WCF에서 지원 되는 시나리오 목록은 [일반적인 보안 시나리오](common-security-scenarios.md)를 참조 하세요. WCF에서 지 원하는 사양의 목록은 [웹 서비스 프로토콜 상호 운용성 가이드](web-services-protocols-interoperability-guide.md)를 참조 하세요.  
  
 다음 섹션에서는 WSE 3.0 웹 서비스의 특정 기능을 WCF로 마이그레이션하는 방법에 대 한 지침을 제공 합니다.  
  
## <a name="general"></a>일반  

 WSE 3.0 및 WCF 응용 프로그램에는 유선 수준의 상호 운용성과 공통 된 용어 집합이 포함 되어 있습니다. WSE 3.0 및 WCF 응용 프로그램은 둘 다 지 원하는 WS-* 사양 집합을 기반으로 하 여 유선 수준의 상호 운용할 수 있습니다. WSE 3.0 또는 WCF 응용 프로그램을 개발할 때 WSE의 턴키 보안 어설션 이름과 인증 모드와 같은 일반적인 용어 집합이 있습니다.  
  
 WCF와 ASP.NET 또는 WSE 3.0 프로그래밍 모델 간에는 비슷한 많은 측면이 있지만 서로 다릅니다. WCF 프로그래밍 모델에 대 한 자세한 내용은 [기본 프로그래밍 수명 주기](../basic-programming-lifecycle.md)를 참조 하세요.  
  
> [!NOTE]
> WSE 웹 서비스를 WCF로 마이그레이션하려면 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 도구를 사용 하 여 클라이언트를 생성할 수 있습니다. 그러나 이 클라이언트에는 WCF 서비스의 시작 지점으로 사용할 수 있는 인터페이스와 클래스도 포함되어 있습니다. 생성되는 인터페이스에는 <xref:System.ServiceModel.OperationContractAttribute> 속성이 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>로 설정되어 계약의 멤버에 적용되는 `*` 특성이 있습니다. WSE 클라이언트에서이 설정을 사용 하 여 웹 서비스를 호출 하는 경우 다음과 같은 예외가 throw 됩니다. **Services3: ResponseProcessingException: WSE910: 응답 메시지를 처리 하는 동안 오류가 발생 하 고 내부 예외에서 오류를 찾을 수** 있습니다. 이를 완화하려면 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 특성의 <xref:System.ServiceModel.OperationContractAttribute> 속성을 `null`처럼 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`이 아닌 값으로 설정합니다.  
  
## <a name="security"></a>보안  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>정책 파일을 사용하여 WSE 3.0 웹 서비스 보안  

 WCF 서비스는 구성 파일을 사용 하 여 서비스를 보호할 수 있으며 해당 메커니즘은 WSE 3.0 정책 파일과 유사 합니다. WSE 3.0에서 정책 파일을 사용하여 웹 서비스를 보호할 때 턴키 보안 어설션 또는 사용자 지정 정책 어설션을 사용합니다. 턴키 보안 어설션은 WCF 보안 바인딩 요소의 인증 모드에 밀접 하 게 매핑됩니다. 동일 하거나 유사한 이름의 WCF 인증 모드와 WSE 3.0 턴키 보안 어설션을 사용할 수 있을 뿐 아니라 동일한 자격 증명 형식을 사용 하 여 메시지를 보호 합니다. 예를 들어 `usernameForCertificate` WSE 3.0의 턴키 보안 어설션은 `UsernameForCertificate` WCF의 인증 모드로 매핑됩니다. 다음 코드 예제에서는 `usernameForCertificate` WSE 3.0의 턴키 보안 어설션을 사용 하는 최소 정책이 `UsernameForCertificate` 사용자 지정 바인딩에서 WCF의 인증 모드로 매핑되는 방법을 보여 줍니다.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 정책 파일에 지정 된 WSE 3.0 웹 서비스의 보안 설정을 WCF로 마이그레이션하려면 구성 파일에 사용자 지정 바인딩을 만들어야 하 고 턴키 보안 어설션이 동등한 인증 모드로 설정 되어야 합니다. 또한 WSE 3.0 클라이언트가 서비스와 통신할 때 August 2004 WS-Addressing 사양을 사용하도록 사용자 지정 바인딩을 구성해야 합니다. 마이그레이션된 WCF 서비스가 WSE 3.0 클라이언트와 통신 하지 않아도 되 고 보안 패리티를 유지 해야 하는 경우 사용자 지정 바인딩을 만드는 대신 적절 한 보안 설정을 사용 하 여 WCF 시스템 정의 바인딩을 사용 하는 것이 좋습니다.  
  
 다음 표에서는 WSE 3.0 정책 파일과 WCF의 해당 사용자 지정 바인딩 간의 매핑을 보여 줍니다.  
  
|WSE 3.0 턴키 보안 어설션|WCF 사용자 지정 바인딩 구성|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF에서 사용자 지정 바인딩을 만드는 방법에 대 한 자세한 내용은 [사용자 지정 바인딩](../extending/custom-bindings.md)을 참조 하세요.  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>애플리케이션 코드를 사용하여 보안된 WSE 3.0 웹 서비스  

 WSE 3.0 또는 WCF를 사용 하는지 여부에 관계 없이 응용 프로그램 코드에서 구성 대신 보안 요구 사항을 지정할 수 있습니다. WSE 3.0에서 보안 요구 사항을 지정하려면 `Policy` 클래스에서 파생되는 클래스를 만든 다음 `Add` 메서드를 호출하여 요구 사항을 추가합니다. 코드에서 보안 요구 사항을 지정 하는 방법에 대 한 자세한 내용은 [방법: 정책 파일을 사용 하지 않고 웹 서비스 보안](/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10))을 참조 하세요. WCF에서 코드에 보안 요구 사항을 지정 하려면 클래스의 인스턴스를 만들고 <xref:System.ServiceModel.Channels.BindingElementCollection> 의 인스턴스를에 추가 <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.BindingElementCollection> 합니다. 보안 어설션 요구 사항은 <xref:System.ServiceModel.Channels.SecurityBindingElement> 클래스의 정적 인증 모드 도우미 메서드를 사용하여 설정됩니다. WCF를 사용 하는 코드에서 보안 요구 사항을 지정 하는 방법에 대 한 자세한 내용은 [방법: SecurityBindingElement를 사용 하 여 사용자 지정 바인딩 만들기](how-to-create-a-custom-binding-using-the-securitybindingelement.md) 및 [방법: 지정 된 인증 모드에 대 한 SecurityBindingElement 만들기](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)를 참조 하세요.  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 사용자 지정 정책 어설션  

 WSE 3.0에는 SOAP 메시지를 보안하는 사용자 지정 정책 어설션과 SPAO 메시지를 보안하지 않는 사용자 지정 정책 어설션이 있습니다. SOAP 메시지를 보호 하는 정책 어설션은 WSE 3.0 `SecurityPolicyAssertion` 클래스에서 파생 되며 WCF의 개념은 <xref:System.ServiceModel.Channels.SecurityBindingElement> 클래스입니다.  
  
 중요 한 점은 WSE 3.0 턴키 보안 어설션이 WCF 인증 모드의 하위 집합 임을 기억 하는 것입니다. WSE 3.0에서 사용자 지정 정책 어설션을 만든 경우 해당 하는 WCF 인증 모드가 있을 수 있습니다. 예를 들어 WSE 3.0에서 `UsernameOverTransport` 턴키 보안 어설션에 해당하는 CertificateOverTransport 보안 어설션을 제공하지는 않지만 클라이언트 인증을 위해 X.509 인증서를 사용합니다. 이 시나리오에 대 한 사용자 고유의 사용자 지정 정책 어설션을 정의한 경우 WCF를 사용 하면 마이그레이션이 간단해 집니다. WCF는이 시나리오에 대 한 인증 모드를 정의 하므로, 정적 인증 모드 도우미 메서드를 활용 하 여 WCF를 구성할 수 있습니다 <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
 SOAP 메시지를 보호 하는 사용자 지정 정책 어설션에 해당 하는 WCF 인증 모드가 없는 경우 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> , 또는 wcf 클래스에서 클래스를 파생 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 시키고 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 해당 바인딩 요소를 지정 합니다. 자세한 내용은 [방법: SecurityBindingElement를 사용 하 여 사용자 지정 바인딩 만들기](how-to-create-a-custom-binding-using-the-securitybindingelement.md)를 참조 하세요.  
  
 SOAP 메시지를 보호 하지 않는 사용자 지정 정책 어설션을 변환 하려면 [필터링](filtering.md) 및 샘플 [사용자 지정 메시지 인터셉터](../samples/custom-message-interceptor.md)를 참조 하세요.  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 사용자 지정 보안 토큰  

 사용자 지정 토큰을 만들기 위한 WCF 프로그래밍 모델은 WSE 3.0과 다릅니다. WSE에서 사용자 지정 토큰을 만드는 방법에 대 한 자세한 내용은 [사용자 지정 보안 토큰 만들기](/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10))를 참조 하세요. WCF에서 사용자 지정 토큰을 만드는 방법에 대 한 자세한 내용은 [방법: 사용자 지정 토큰 만들기](../extending/how-to-create-a-custom-token.md)를 참조 하세요.  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 사용자 지정 토큰 관리자  

 사용자 지정 토큰 관리자를 만드는 프로그래밍 모델은 WSE 3.0이 아닌 WCF에서 다릅니다. 사용자 지정 토큰 관리자 및 사용자 지정 보안 토큰에 필요한 기타 구성 요소를 만드는 방법에 대 한 자세한 내용은 [방법: 사용자 지정 토큰 만들기](../extending/how-to-create-a-custom-token.md)를 참조 하세요.  
  
> [!NOTE]
> 사용자 지정 `UsernameToken` 보안 토큰 관리자를 만든 경우 WCF는 사용자 지정 보안 토큰 관리자를 만드는 것 보다 더 쉽게 인증 논리를 지정 하는 메커니즘을 제공 합니다. 자세한 내용은 [방법: 사용자 지정 사용자 이름 및 암호 유효성 검사기 사용](how-to-use-a-custom-user-name-and-password-validator.md)을 참조 하세요.  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM 인코딩된 SOAP 메시지를 사용하는 WSE 3.0 웹 서비스  

 WSE 3 응용 프로그램과 마찬가지로 WCF 응용 프로그램은 구성에서 MTOM 메시지 인코딩을 지정할 수 있습니다. 이 설정을 마이그레이션하려면 [\<mtomMessageEncoding>](../../configure-apps/file-schema/wcf/mtommessageencoding.md) 서비스의 바인딩에를 추가 합니다. 다음 코드 예제에서는 WCF에 해당 하는 서비스에 대해 MTOM 인코딩을 WSE 3.0에 지정 하는 방법을 보여 줍니다.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>메시징  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 메시징 API를 사용하는 WSE 3.0 애플리케이션  

 WSE 메시징 API를 사용하여 클라이언트와 웹 서비스 간에 전달되는 XML에 직접 액세스할 수 있으면 &quot;POX&quot;(Plain Old XML)를 사용하도록 애플리케이션을 변환할 수 있습니다. POX에 대 한 자세한 내용은 [POX 응용 프로그램과의 상호 운용성](interoperability-with-pox-applications.md)을 참조 하세요. WSE 메시징 API에 대 한 자세한 내용은 [Wse 메시징 api를 사용 하 여 SOAP 메시지 전송 및 수신](/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10))을 참조 하세요.  
  
## <a name="transports"></a>전송  
  
### <a name="tcp"></a>TCP  

 기본적으로 TCP 전송을 사용 하 여 SOAP 메시지를 전송 하는 WSE 3.0 클라이언트와 웹 서비스는 WCF 클라이언트 및 웹 서비스와 상호 운용 되지 않습니다. 이러한 비호환성은 성능상의 이유와 TCP 프로토콜에 사용된 프레이밍의 차이로 인한 것입니다. 그러나 WCF 샘플에서는 WSE 3.0와 상호 운용 되는 사용자 지정 TCP 세션을 구현 하는 방법에 대해 자세히 설명 합니다. 이 샘플에 대 한 자세한 내용은 [Transport: WSE 3.0 TCP 상호 운용성](../samples/transport-wse-3-0-tcp-interoperability.md)을 참조 하세요.  
  
 WCF 응용 프로그램에서 TCP 전송을 사용 하도록 지정 하려면를 사용 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 합니다.  
  
### <a name="custom-transport"></a>사용자 지정 전송  

 WCF의 WSE 3.0 사용자 지정 전송은 채널 확장에 해당 합니다. 채널 확장을 만드는 방법에 대 한 자세한 내용은 [채널 계층 확장](../extending/extending-the-channel-layer.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- [기본 프로그래밍 수명 주기](../basic-programming-lifecycle.md)
- [사용자 지정 바인딩](../extending/custom-bindings.md)
- [방법: SecurityBindingElement를 사용하여 사용자 지정 바인딩 만들기](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [방법: 지정된 인증 모드에 대한 SecurityBindingElement 만들기](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
