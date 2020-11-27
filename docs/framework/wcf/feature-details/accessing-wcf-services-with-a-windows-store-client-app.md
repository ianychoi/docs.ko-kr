---
title: Windows 스토어 클라이언트 응용 프로그램을 사용하여 WCF 서비스에 액세스
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: ab57adbe0effa2b74541053aa0fcc5b572a6b7fd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293938"
---
# <a name="access-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="1a827-102">Windows 스토어 클라이언트 앱을 사용 하 여 WCF 서비스에 액세스</span><span class="sxs-lookup"><span data-stu-id="1a827-102">Access WCF Services with a Windows Store Client App</span></span>

<span data-ttu-id="1a827-103">Windows 8에서는 Windows 스토어 애플리케이션이라는 새로운 형식의 애플리케이션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="1a827-104">이러한 애플리케이션은 터치 스크린 인터페이스를 바탕으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="1a827-105">.NET Framework 4.5에서는 Windows 스토어 애플리케이션을 사용하여 WCF 서비스를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="1a827-106">Windows 스토어 애플리케이션의 WCF 지원</span><span class="sxs-lookup"><span data-stu-id="1a827-106">WCF Support in Windows Store Applications</span></span>  

 <span data-ttu-id="1a827-107">Windows 스토어 애플리케이션 내에서 일부 WCF 기능을 사용할 수 있습니다. 자세한 내용은 다음 단원을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a827-108">WCF에서 노출하는 API 대신 WinRT 배포 API를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="1a827-109">자세한 내용은 [WinRT 배포 API](xref:Windows.Web.Syndication)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1a827-110">서비스 참조 추가를 사용 하 여 Windows 런타임 구성 요소에 웹 서비스 참조를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn't supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="1a827-111">지원되는 바인딩</span><span class="sxs-lookup"><span data-stu-id="1a827-111">Supported Bindings</span></span>  

 <span data-ttu-id="1a827-112">Windows 스토어 애플리케이션에서는 다음과 같은 WCF 바인딩이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="1a827-113">Windows 스토어 애플리케이션에서는 다음과 같은 바인딩 요소가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="1a827-114">텍스트 인코딩과 이진 인코딩 모두가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="1a827-115">모든 WCF 전송 모드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="1a827-116">자세한 내용은 [Streaming Message Transfer](streaming-message-transfer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-116">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="1a827-117">에서</span><span class="sxs-lookup"><span data-stu-id="1a827-117">Add Service Reference</span></span>  

 <span data-ttu-id="1a827-118">Windows 스토어 애플리케이션에서 WCF 서비스를 호출하려면 Visual Studio 2012의 서비스 참조 추가 기능을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="1a827-119">Windows 스토어 애플리케이션 내에서 서비스 참조 추가 기능이 완료될 때 몇 가지 변경 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="1a827-120">먼저, 구성 파일이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-120">First no configuration file is generated.</span></span> <span data-ttu-id="1a827-121">Windows 스토어 애플리케이션은 구성 파일을 사용하지 않으므로 코드로 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="1a827-122">이 구성 코드는 서비스 참조 추가를 통해 생성된 References.cs 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="1a827-123">이 파일을 보려면 솔루션 탐색기에서 "모든 파일 표시"를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="1a827-124">해당 파일은 프로젝트 내의 서비스 참조 노드 및 Reference.svcmap 노드 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="1a827-125">Windows 스토어 애플리케이션 내의 WCF 서비스에 대해 생성된 모든 작업은 태스크 기반 비동기 패턴을 사용하여 비동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="1a827-126">자세한 내용은 비동기 [작업-작업을 사용 하 여 비동기 프로그래밍 단순화](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a827-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="1a827-127">이제 구성이 코드로 생성되므로 서비스 참조가 업데이트될 때마다 Reference.cs 파일의 모든 변경 내용을 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="1a827-128">이러한 문제를 해결하기 위해 구성 코드는 부분 메서드(Partial Method) 내에서 생성됩니다. 부분 메서드는 클라이언트 프록시 클래스에서 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="1a827-129">부분 메서드는 다음과 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="1a827-130">이 부분 메서드를 구현하고 다음과 같이 클라이언트 프록시 클래스에서 바인딩 또는 엔드포인트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="1a827-131">Serialization</span><span class="sxs-lookup"><span data-stu-id="1a827-131">Serialization</span></span>  

 <span data-ttu-id="1a827-132">Windows 스토어 애플리케이션에서는 다음과 같은 serializer가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="1a827-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="1a827-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="1a827-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="1a827-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="1a827-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="1a827-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1a827-136">이제 XmlDictionaryWriter.Write(DateTime)는 DateTime 개체를 문자열로 씁니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="1a827-137">보안</span><span class="sxs-lookup"><span data-stu-id="1a827-137">Security</span></span>  

<span data-ttu-id="1a827-138">Windows 스토어 응용 프로그램에서 지원 되는 보안 모드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="1a827-139">Windows 스토어 응용 프로그램에서는 다음과 같은 클라이언트 자격 증명 형식이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="1a827-140">없음</span><span class="sxs-lookup"><span data-stu-id="1a827-140">None</span></span>  
  
2. <span data-ttu-id="1a827-141">기본</span><span class="sxs-lookup"><span data-stu-id="1a827-141">Basic</span></span>  
  
3. <span data-ttu-id="1a827-142">다이제스트</span><span class="sxs-lookup"><span data-stu-id="1a827-142">Digest</span></span>  
  
4. <span data-ttu-id="1a827-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1a827-143">Negotiate</span></span>  
  
5. <span data-ttu-id="1a827-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="1a827-144">NTLM</span></span>  
  
6. <span data-ttu-id="1a827-145">Windows</span><span class="sxs-lookup"><span data-stu-id="1a827-145">Windows</span></span>  
  
7. <span data-ttu-id="1a827-146">Username(메시지 보안)</span><span class="sxs-lookup"><span data-stu-id="1a827-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="1a827-147">Windows(전송 보안)</span><span class="sxs-lookup"><span data-stu-id="1a827-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="1a827-148">Windows 스토어 애플리케이션이 기본 Windows 자격 증명에 액세스하여 이를 보내도록 하려면 Package.appmanifest 파일 내에서 이 기능을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="1a827-149">이 파일을 열고 기능 탭을 선택한 다음 "기본 Windows 자격 증명"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="1a827-150">그러면 도메인 자격 증명이 필요한 인트라넷 리소스에 애플리케이션을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a827-151">Windows 스토어 응용 프로그램이 컴퓨터 간 호출을 수행 하도록 하려면 "홈/회사 네트워킹" 이라는 다른 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="1a827-152">이 설정은 appmanifest 파일의 기능 탭에도 있습니다. 홈/회사 네트워킹 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="1a827-153">이를 통해 응용 프로그램은 home 및 work와 같이 사용자가 신뢰할 수 있는 장소의 네트워크에 대 한 인바운드 및 아웃 바운드 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-153">This gives your application inbound and outbound access to the networks of the user's trusted places like home and work.</span></span> <span data-ttu-id="1a827-154">중요한 인바운드 포트는 항상 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="1a827-155">인터넷의 서비스에 액세스하려면 인터넷(클라이언트) 기능도 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="1a827-156">기타</span><span class="sxs-lookup"><span data-stu-id="1a827-156">Misc</span></span>  

 <span data-ttu-id="1a827-157">Windows 스토어 애플리케이션에 는 다음 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="1a827-158">서비스 계약 정의</span><span class="sxs-lookup"><span data-stu-id="1a827-158">Defining Service Contracts</span></span>  

 <span data-ttu-id="1a827-159">태스크 기반 비동기 패턴을 사용하여 비동기 서비스 작업만 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="1a827-160">그러면 서비스 작업을 호출하는 동안 Windows 스토어 애플리케이션이 응답을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1a827-161">동기 작업을 정의하더라도 예외가 throw되지는 않지만 비동기 작업만 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="1a827-162">Windows 스토어 애플리케이션에서 WCF 서비스 호출</span><span class="sxs-lookup"><span data-stu-id="1a827-162">Calling WCF Services from Windows Store Applications</span></span>  

 <span data-ttu-id="1a827-163">앞에서 설명한 것처럼 모든 구성은 생성된 프록시 클래스의 GetBindingForEndpoint 메서드에서 코드로 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="1a827-164">서비스 작업 호출은 다음 코드 조각과 같이 태스크 기반 비동기 메서드를 호출할 때와 동일한 방법으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="1a827-165">비동기 호출을 수행하는 메서드에서는 async 키워드가 사용되고 비동기 메서드를 호출할 때는 await 키워드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a827-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a827-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a827-166">See also</span></span>

- [<span data-ttu-id="1a827-167">WCF 보안 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="1a827-167">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="1a827-168">바인딩</span><span class="sxs-lookup"><span data-stu-id="1a827-168">Bindings</span></span>](../bindings.md)
