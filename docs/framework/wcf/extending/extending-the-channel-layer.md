---
description: '자세히 알아보기: 채널 계층 확장'
title: 채널 계층 확장
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 4588a2749127e454801615cc8916d83fc15592bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685584"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="49090-103">채널 계층 확장</span><span class="sxs-lookup"><span data-stu-id="49090-103">Extending the Channel Layer</span></span>

<span data-ttu-id="49090-104">채널 계층은 클라이언트 및 서비스 간의 메시지 교환을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="49090-104">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="49090-105">채널 확장은 보안과 같은 새 프로토콜 기능 또는 SOAP 메시지를 전달하기 위한 새 네트워크 전송 구현과 같은 전송 기능을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49090-105">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49090-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="49090-106">In This Section</span></span>  

 [<span data-ttu-id="49090-107">채널 모델 개요</span><span class="sxs-lookup"><span data-stu-id="49090-107">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="49090-108">채널의 정의, 제공하는 기능 및 서비스와 클라이언트 애플리케이션 모두에서 작동하는 방법에 대해 높은 수준의 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="49090-108">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="49090-109">채널 개발</span><span class="sxs-lookup"><span data-stu-id="49090-109">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="49090-110">다양한 채널 인프라 형식이 수행하는 역할, 상태 엔진 및 상태 수명 주기가 작동하는 방법, 예외 및 결함을 처리하는 방법, 메타데이터 지원을 구현하는 방법 및 채널이 메시지 인코더와 작동하는 방법에 대해 자세하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49090-110">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="49090-111">사용자 지정 인코더</span><span class="sxs-lookup"><span data-stu-id="49090-111">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="49090-112">채널에서 메시지 인코더가 수행하는 역할과 이를 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49090-112">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="49090-113">사용자 지정 스트림 업그레이드</span><span class="sxs-lookup"><span data-stu-id="49090-113">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="49090-114">스트림 지향 전송에서 제공하는 스트림의 업그레이드 프로세스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49090-114">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
