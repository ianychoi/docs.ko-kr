---
description: '자세한 정보: 방법: 코드에서 서비스 바인딩 지정'
title: '방법: 코드에서 서비스 바인딩 지정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 744919fee4ec28d7df4581ac1d608d1fa9e99a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755943"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="cba2b-103">방법: 코드에서 서비스 바인딩 지정</span><span class="sxs-lookup"><span data-stu-id="cba2b-103">How to: Specify a Service Binding in Code</span></span>

<span data-ttu-id="cba2b-104">이 예제에서는 계산기 서비스에 대해 `ICalculator` 계약을 정의하고, `CalculatorService` 클래스에서 서비스를 구현한 다음 코드로 엔드포인트를 정의합니다. 이 때 서비스가 <xref:System.ServiceModel.BasicHttpBinding> 클래스를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-104">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="cba2b-105">일반적으로 바인딩 및 주소 정보를 코드에서 명령적으로 지정하지 않고 구성에서 선언적으로 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="cba2b-106">일반적으로 배포 된 서비스에 대 한 바인딩 및 주소가 서비스를 개발 하는 동안 사용 된 것과 다르기 때문에 일반적으로 코드에서 끝점을 정의 하는 것은 실용적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="cba2b-107">일반적으로 바인딩 및 주소 지정 정보를 코드와 구분하면 애플리케이션을 다시 컴파일하거나 다시 배포할 필요 없이 해당 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="cba2b-108">코드 대신 구성 요소를 사용 하 여이 서비스를 구성 하는 방법에 대 한 설명은 [방법: 구성에서 서비스 바인딩 지정](how-to-specify-a-service-binding-in-configuration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cba2b-108">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="cba2b-109">코드에서 서비스에 BasicHttpBinding을 사용하도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="cba2b-109">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="cba2b-110">서비스 유형에 대한 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-110">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="cba2b-111">서비스 클래스에 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-111">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="cba2b-112">호스팅 애플리케이션에서 서비스에 사용할 바인딩 및 서비스에 대한 기본 주소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-112">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="cba2b-113">서비스에 대한 호스트를 만들고 엔드포인트를 추가한 다음 호스트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-113">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="cba2b-114">바인딩 속성의 기본값을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="cba2b-114">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="cba2b-115"><xref:System.ServiceModel.BasicHttpBinding> 클래스의 기본 속성 값 중 하나를 수정하려면 호스트를 만들기 전에 바인딩의 속성 값을 새 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-115">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="cba2b-116">예를 들어, 기본 열기 및 닫기 시간 제한 값을 1분에서 2분으로 변경하려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cba2b-116">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="cba2b-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cba2b-117">See also</span></span>

- [<span data-ttu-id="cba2b-118">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="cba2b-118">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cba2b-119">엔드포인트 주소 지정</span><span class="sxs-lookup"><span data-stu-id="cba2b-119">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
