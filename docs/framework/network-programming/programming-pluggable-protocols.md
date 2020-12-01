---
title: 플러그형 프로토콜 프로그래밍
description: 추상 WebRequest 및 WebResponse 클래스가 플러그형 프로토콜을 지원함으로써 프로토콜을 지정하지 않고 애플리케이션에서 데이터를 가져올 수 있게 하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: a3f8106b238c28de77362e73aa26667209f6b517
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263180"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="71d69-103">플러그형 프로토콜 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="71d69-103">Programming Pluggable Protocols</span></span>

<span data-ttu-id="71d69-104">추상 <xref:System.Net.WebRequest> 및 <xref:System.Net.WebResponse> 클래스에서 플러그형 프로토콜의 기초를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-104">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="71d69-105"><xref:System.Net.WebRequest> 및 <xref:System.Net.WebResponse>에서 프로토콜별 클래스를 파생시키면, 애플리케이션에서 사용할 프로토콜을 지정하지 않아도 인터넷 리소스에서 데이터를 요청하고 응답을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-105">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="71d69-106">Create 메서드를 등록해야 프로토콜별 <xref:System.Net.WebRequest>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-106">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="71d69-107">특정 인터넷 구성표, 구성표와 서버 또는 구성표, 서버 및 경로에 대한 요청 집합을 처리하려면 <xref:System.Net.WebRequest>의 정적 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> 메서드를 사용하여 <xref:System.Net.WebRequest> 하위 항목을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-107">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="71d69-108">대부분의 경우 <xref:System.Net.WebRequest> 클래스의 속성과 메서드를 사용하여 데이터를 보내고 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-108">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="71d69-109">그러나 프로토콜별 속성에 액세스해야 하는 경우 <xref:System.Net.WebRequest>를 특정 파생 클래스 인스턴스로 형식 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-109">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="71d69-110">플러그형 프로토콜을 이용하려면 <xref:System.Net.WebRequest> 하위 항목에서 프로토콜별 속성을 설정하지 않아도 되는 기본 요청 및 응답 트랜잭션을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-110">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="71d69-111">예를 들어 HTTP의 <xref:System.Net.WebRequest> 클래스를 구현하는 <xref:System.Net.HttpWebRequest> 클래스에서 기본적으로 `GET` 요청을 제공하고 웹 서버에서 반환된 스트림을 포함하는 <xref:System.Net.HttpWebResponse>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="71d69-111">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d69-112">참조</span><span class="sxs-lookup"><span data-stu-id="71d69-112">See also</span></span>

- [<span data-ttu-id="71d69-113">WebRequest에서 파생</span><span class="sxs-lookup"><span data-stu-id="71d69-113">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="71d69-114">WebResponse에서 파생</span><span class="sxs-lookup"><span data-stu-id="71d69-114">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="71d69-115">.NET Framework의 네트워크 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="71d69-115">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="71d69-116">방법: 프로토콜 관련 속성에 액세스하기 위해 WebRequest 형식 캐스팅</span><span class="sxs-lookup"><span data-stu-id="71d69-116">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
