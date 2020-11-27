---
title: '방법: COM+ 서비스 설정 구성'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: b75f5c2a64b7184959e929439893b33193aa7bae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257472"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="dae90-102">방법: COM+ 서비스 설정 구성</span><span class="sxs-lookup"><span data-stu-id="dae90-102">How to: Configure COM+ Service Settings</span></span>

<span data-ttu-id="dae90-103">COM+ 서비스 구성 도구를 사용하여 애플리케이션 인터페이스를 추가하거나 제거하면 애플리케이션의 구성 파일에서 웹 서비스 구성이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="dae90-104">COM + 호스팅 모드에서 Application.config 파일은 응용 프로그램 루트 디렉터리 (%Programfiles%\complus applications\ 응용 프로그램 \\ {appid}가 기본값)에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="dae90-105">웹 호스팅 모드에서는 지정된 vroot 디렉터리에 Web.config 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dae90-106">메시지 서명을 사용하여 클라이언트와 서버 사이에서 메시지가 변조되지 않도록 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="dae90-107">또한 메시지 또는 전송 계층 암호화를 사용하여 클라이언트와 서버 간의 메시지에서 정보가 공개되지 않도록 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="dae90-108">WCF (Windows Communication Foundation) 서비스와 마찬가지로, 제한을 사용 하 여 동시 호출, 연결, 인스턴스 및 보류 중인 작업의 수를 제한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="dae90-109">이렇게 하면 리소스를 과도하게 사용하지 않도록 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="dae90-110">스로틀 동작은 서비스 구성 파일 설정을 통해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae90-111">예제</span><span class="sxs-lookup"><span data-stu-id="dae90-111">Example</span></span>  

 <span data-ttu-id="dae90-112">다음 인터페이스를 구현하는 구성 요소를 고려해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-112">Consider a component that implements the following interface:</span></span>  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="dae90-113">구성 요소가 웹 서비스로 노출되는 경우, 노출되어 클라이언트가 준수해야 하는 해당 서비스 계약은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```csharp
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="dae90-114">IID는 계약에 대한 초기 네임스페이스의 일부를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="dae90-115">이 서비스를 사용하는 클라이언트 애플리케이션은 이 계약을 준수함과 동시에 애플리케이션 구성에 지정된 것과 호환되는 바인딩을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="dae90-116">다음 코드 예제는 기본 구성 파일을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="dae90-117">WCF (Windows Communication Foundation) 웹 서비스로 서, 표준 서비스 모델 구성 스키마를 준수 하며 다른 WCF 서비스 구성 파일과 같은 방법으로 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="dae90-118">대표적인 수정 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="dae90-119">엔드포인트 주소를 기본 ApplicationName/ComponentName/InterfaceName 형식에서 보다 사용이 간편한 형식으로 변경</span><span class="sxs-lookup"><span data-stu-id="dae90-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="dae90-120">서비스의 네임 스페이스를 기본 `http://tempuri.org/InterfaceID` 양식에서 보다 적절 한 형식으로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="dae90-121">다른 전송 바인딩을 사용하도록 엔드포인트 변경</span><span class="sxs-lookup"><span data-stu-id="dae90-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="dae90-122">COM+ 호스팅의 경우 기본적으로 명명된 파이프 전송이 사용되지만 대신 TCP 같은 시스템 외 전송을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae90-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dae90-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dae90-123">See also</span></span>

- [<span data-ttu-id="dae90-124">COM + 응용 프로그램과 통합</span><span class="sxs-lookup"><span data-stu-id="dae90-124">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
