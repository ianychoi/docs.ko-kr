---
description: '자세한 정보: 방법: PrincipalPermissionAttribute 클래스를 사용 하 여 액세스 제한'
title: '방법: PrincipalPermissionAttribute 클래스를 사용하여 액세스 제한'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 533bd3358d5e337071c6419264d1dac03b8987ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779350"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="c6338-103">방법: PrincipalPermissionAttribute 클래스를 사용하여 액세스 제한</span><span class="sxs-lookup"><span data-stu-id="c6338-103">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="c6338-104">Windows 도메인 컴퓨터의 리소스에 대한 액세스 제어는 기본적인 보안 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-104">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="c6338-105">예를 들어, 특정 사용자만 급여 정보와 같은 민감한 데이터를 볼 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-105">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="c6338-106">이 항목에서는 사용자가 미리 정의된 그룹에 속하도록 요청하여 메서드에 대한 액세스를 제한하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-106">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="c6338-107">작업 예제는 [서비스 작업에 대 한 액세스 권한 부여](./samples/authorizing-access-to-service-operations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6338-107">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="c6338-108">작업은 두 가지 별도의 절차로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-108">The task consists of two separate procedures.</span></span> <span data-ttu-id="c6338-109">첫 번째는 그룹을 만들어 이 그룹을 사용자로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-109">The first creates the group and populates it with users.</span></span> <span data-ttu-id="c6338-110">두 번째는 그룹을 지정할 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 클래스를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-110">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="c6338-111">Windows 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c6338-111">To create a Windows group</span></span>  
  
1. <span data-ttu-id="c6338-112">**컴퓨터 관리** 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-112">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="c6338-113">왼쪽 패널에서 **로컬 사용자 및 그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-113">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="c6338-114">**그룹** 을 마우스 오른쪽 단추로 클릭 하 고 **새 그룹** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-114">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="c6338-115">**그룹 이름** 상자에 새 그룹의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-115">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="c6338-116">**설명** 상자에 새 그룹에 대 한 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-116">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="c6338-117">**추가** 단추를 클릭 하 여 그룹에 새 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-117">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="c6338-118">사용자 자신을 그룹에 추가하고 다음 코드를 테스트하려면, 컴퓨터를 로그오프한 후 다시 로그온하여 그룹에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-118">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="c6338-119">사용자 멤버 자격을 요구하려면</span><span class="sxs-lookup"><span data-stu-id="c6338-119">To demand user membership</span></span>  
  
1. <span data-ttu-id="c6338-120">구현 된 서비스 계약 코드가 포함 된 WCF (Windows Communication Foundation) 코드 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-120">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="c6338-121">계약을 구현 하는 방법에 대 한 자세한 내용은 [서비스 계약 구현](implementing-service-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6338-121">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="c6338-122"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 특성을 특정 그룹에 대해 제한되어야 하는 각 메서드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-122">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="c6338-123"><xref:System.Security.Permissions.SecurityAttribute.Action%2A> 속성을 <xref:System.Security.Permissions.SecurityAction.Demand>로 설정하고 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> 속성을 그룹 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-123">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="c6338-124">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="c6338-124">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="c6338-125"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 특성을 계약에 적용하면 <xref:System.Security.SecurityException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-125">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="c6338-126">메서드 수준에서만 이 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-126">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="c6338-127">인증서를 사용하여 메서드에 대한 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="c6338-127">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="c6338-128">또한 클라이언트 자격 증명 형식이 인증서인 경우 `PrincipalPermissionAttribute` 클래스를 사용하여 메서드에 대한 액세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-128">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="c6338-129">이를 수행하려면 인증서의 주체 및 지문이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-129">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="c6338-130">인증서의 속성을 검사 하려면 [방법: MMC 스냅인을 사용 하 여 인증서 보기](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6338-130">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="c6338-131">지문 값을 찾으려면 [방법: 인증서의 손 도장 (thumbprint) 검색](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6338-131">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="c6338-132">인증서를 사용하여 액세스를 제어하려면</span><span class="sxs-lookup"><span data-stu-id="c6338-132">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="c6338-133"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 클래스를 액세스를 제한할 메서드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-133">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="c6338-134">특성의 동작을 <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-134">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="c6338-135">`Name` 속성을 주체 이름 및 인증서 지문으로 구성된 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-135">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="c6338-136">다음 예제와 같이 두 개의 값을 세미콜론 및 공백으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-136">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="c6338-137">다음 구성 예제와 같이 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 속성을 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-137">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="c6338-138">이 값을 `UseAspNetRoles`로 설정하면 `Name`의 `PrincipalPermissionAttribute` 속성이 문자열 비교를 수행하는 데 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-138">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="c6338-139">인증서가 클라이언트 자격 증명으로 사용 되는 경우 기본적으로 WCF는 인증서 일반 이름 및 지문을 세미콜론으로 연결 하 여 클라이언트의 기본 id에 대 한 고유한 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-139">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="c6338-140">`UseAspNetRoles`를 서비스의 `PrincipalPermissionMode`로 설정한 경우 이 기본 ID 값을 `Name` 속성 값과 비교하여 사용자의 액세스 권한을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-140">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="c6338-141">또는 자체 호스팅되는 서비스를 만드는 경우 코드의 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 속성을 다음 코드와 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6338-141">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c6338-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6338-142">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="c6338-143">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="c6338-143">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="c6338-144">보안 개요</span><span class="sxs-lookup"><span data-stu-id="c6338-144">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="c6338-145">서비스 계약 구현</span><span class="sxs-lookup"><span data-stu-id="c6338-145">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
