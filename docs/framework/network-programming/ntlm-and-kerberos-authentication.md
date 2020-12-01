---
title: NTLM 및 Kerberos 인증
description: 기본 NTLM 인증과 Kerberos 인증이 .NET Framework 애플리케이션에 대해 작동하는 방법을 알아보고 기본이 아닌 NTLM 인증에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: 3fcd39f5414bca9bfcb368f6962ae36891458151
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262829"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="60913-103">NTLM 및 Kerberos 인증</span><span class="sxs-lookup"><span data-stu-id="60913-103">NTLM and Kerberos Authentication</span></span>

<span data-ttu-id="60913-104">기본 NTLM 인증 및 Kerberos 인증에서는 호출 애플리케이션과 연결된 Microsoft Windows NT 사용자 자격 증명을 사용하여 서버에 인증을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="60913-104">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="60913-105">기본이 아닌 NTLM 인증을 사용할 때, 다음 예제에 표시된 대로 애플리케이션에서 인증 형식을 NTLM으로 설정하고 <xref:System.Net.NetworkCredential> 개체를 사용하여 호스트에 사용자 이름, 암호 및 도메인을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="60913-105">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="60913-106">애플리케이션 사용자의 자격 증명을 사용하여 인터넷 서비스에 연결해야 하는 애플리케이션에서는 다음 예제에 표시된 대로 사용자의 기본 자격 증명을 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60913-106">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="60913-107">협상 인증 모듈을 통해 원격 서버에서 NTLM 또는 Kerberos 인증을 사용하는지 판별하고 적절한 응답을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="60913-107">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60913-108">NTLM 인증은 프록시 서버를 통해 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60913-108">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60913-109">참조</span><span class="sxs-lookup"><span data-stu-id="60913-109">See also</span></span>

- [<span data-ttu-id="60913-110">기본 인증 및 다이제스트 인증</span><span class="sxs-lookup"><span data-stu-id="60913-110">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="60913-111">인터넷 인증</span><span class="sxs-lookup"><span data-stu-id="60913-111">Internet Authentication</span></span>](internet-authentication.md)
