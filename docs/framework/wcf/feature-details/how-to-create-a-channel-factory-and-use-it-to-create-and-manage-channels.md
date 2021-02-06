---
description: '자세히 알아보기: 방법: 채널 팩터리를 만들어 채널을 만들고 관리 하는 데 사용'
title: '방법: 채널 팩터리를 만들어 채널을 만들고 관리하는 데 사용'
ms.date: 03/30/2017
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
ms.openlocfilehash: 4e76e5ea0c6776e5623a2e716a3702e628f146f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643477"
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="98c8f-103">방법: 채널 팩터리를 만들어 채널을 만들고 관리하는 데 사용</span><span class="sxs-lookup"><span data-stu-id="98c8f-103">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>

<span data-ttu-id="98c8f-104">ph x="1" /&gt; 클래스에서는 서비스 엔드포인트에서 메시지를 받거나 보내기 위해 클라이언트에서 사용하는 여러 형식의 이중 채널을 만들고 관리하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98c8f-104">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c8f-105">예제</span><span class="sxs-lookup"><span data-stu-id="98c8f-105">Example</span></span>  

 <span data-ttu-id="98c8f-106">다음 코드에서는 채널 팩터리를 만드는 방법과 이 채널 팩터리를 사용하여 채널을 만들고 관리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98c8f-106">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98c8f-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98c8f-107">See also</span></span>

- <xref:System.ServiceModel.DuplexChannelFactory%601>
