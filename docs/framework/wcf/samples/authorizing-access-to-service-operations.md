---
description: '자세한 정보: 서비스 작업에 대 한 액세스 권한 부여'
title: Authorizing Access to Service Operations
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 052adc6104b75884c90c266e2e0e7a045032c457
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732698"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="60cfa-103">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="60cfa-103">Authorizing Access to Service Operations</span></span>

<span data-ttu-id="60cfa-104">이 샘플에서는를 사용 하 여 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 특성을 사용 하 여 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 서비스 작업에 대 한 액세스 권한을 부여 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-104">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="60cfa-105">이 샘플은 [시작](getting-started-sample.md) 샘플을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-105">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="60cfa-106">서비스와 클라이언트는를 사용 하 여 구성 됩니다 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="60cfa-106">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="60cfa-107">`mode`의 특성이로 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 설정 되 `Message` 고 `clientCredentialType` 가로 설정 `Windows` 된 경우</span><span class="sxs-lookup"><span data-stu-id="60cfa-107">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="60cfa-108"><xref:System.Security.Permissions.PrincipalPermissionAttribute>는 각 서비스 메서드에 적용되고 각 작업에 대한 액세스를 제한하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-108">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="60cfa-109">호출자는 각 작업에 액세스하기 위해 Windows 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-109">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="60cfa-110">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60cfa-111">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="60cfa-112">서비스 구성 파일은를 사용 하 여 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 특성을 설정 합니다 `principalPermissionMode` .</span><span class="sxs-lookup"><span data-stu-id="60cfa-112">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="60cfa-113">`principalPermissionMode`를 `UseWindowsGroups`로 설정하면 Windows 그룹 이름에 기초하여 <xref:System.Security.Permissions.PrincipalPermissionAttribute>를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-113">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="60cfa-114">다음 샘플 코드와 같이 <xref:System.Security.Permissions.PrincipalPermissionAttribute>가 각 작업에 적용되어 호출자가 Windows 관리자 그룹의 일부여야 한다는 것을 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-114">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="60cfa-115">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="60cfa-116">클라이언트는 관리자 그룹의 일부인 계정으로 실행 중인 경우 각 작업과 통신할 수 있고, 그렇지 않은 경우 액세스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-116">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="60cfa-117">권한 부여 오류를 테스트하려면 관리자 그룹의 일부가 아닌 계정으로 클라이언트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-117">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="60cfa-118">클라이언트를 종료하려면 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-118">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="60cfa-119"><xref:System.ServiceModel.Dispatcher.IErrorHandler>를 구현하여 권한 부여 오류를 서비스에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-119">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="60cfa-120">구현에 대 한 자세한 내용은 [오류 처리 및 보고](extending-control-over-error-handling-and-reporting.md) 에 대 한 제어 확장을 참조 하세요 `IErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="60cfa-120">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="60cfa-121">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="60cfa-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="60cfa-122">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="60cfa-123">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="60cfa-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="60cfa-124">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="60cfa-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
