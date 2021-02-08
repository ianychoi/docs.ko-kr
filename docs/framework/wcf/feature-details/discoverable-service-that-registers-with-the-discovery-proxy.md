---
description: '자세한 정보: 방법: 검색 프록시를 사용 하 여 등록 하는 검색 가능한 서비스 구현'
title: '방법: 검색 프록시에 등록할 검색 가능한 서비스 구현'
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: 71991de6b7fd0180d4f87c2bfc48e99dc398fa53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802959"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="50ee9-103">방법: 검색 프록시에 등록할 검색 가능한 서비스 구현</span><span class="sxs-lookup"><span data-stu-id="50ee9-103">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>

<span data-ttu-id="50ee9-104">이 항목은 검색 프록시를 구현하는 방법에 대해 설명하는 네 항목 중 두 번째 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-104">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="50ee9-105">이전 항목인 [방법: 검색 프록시 구현](how-to-implement-a-discovery-proxy.md)에서는 검색 프록시를 구현 했습니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-105">In the previous topic, [How to: Implement a Discovery Proxy](how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="50ee9-106">이 항목에서는 알림 메시지 (및)를 검색 프록시로 전송 하 여 `Hello` `Bye` 검색 프록시에 등록 하 고 등록을 취소 하는 WCF 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-106">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="50ee9-107">서비스 계약을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="50ee9-107">To define the service contract</span></span>

1. <span data-ttu-id="50ee9-108">`DiscoveryProxyExample` 솔루션에 `Service`라는 새 콘솔 애플리케이션 프로젝트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-108">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="50ee9-109">다음 어셈블리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-109">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="50ee9-110">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50ee9-110">System.ServiceModel</span></span>

    2. <span data-ttu-id="50ee9-111">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="50ee9-111">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="50ee9-112">`CalculatorService`라는 프로젝트에 새 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-112">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="50ee9-113">다음 using 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-113">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="50ee9-114">CalculatorService.cs 내에서 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-114">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="50ee9-115">CalculatorService.cs 내에서 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-115">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="50ee9-116">서비스를 호스트하려면</span><span class="sxs-lookup"><span data-stu-id="50ee9-116">To host the service</span></span>

1. <span data-ttu-id="50ee9-117">프로젝트를 만들 때 생성된 Program.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-117">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="50ee9-118">다음 using 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-118">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="50ee9-119">`Main()` 메서드 안에서 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-119">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="50ee9-120">검색 가능한 서비스의 구현을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-120">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="50ee9-121">[방법: 검색 프록시를 사용 하 여 서비스를 찾는 클라이언트 응용 프로그램 구현](client-app-discovery-proxy-to-find-a-service.md)을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-121">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="50ee9-122">예제</span><span class="sxs-lookup"><span data-stu-id="50ee9-122">Example</span></span>

 <span data-ttu-id="50ee9-123">다음은 이 항목에서 사용되는 전체 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="50ee9-123">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="50ee9-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50ee9-124">See also</span></span>

- [<span data-ttu-id="50ee9-125">WCF 검색</span><span class="sxs-lookup"><span data-stu-id="50ee9-125">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="50ee9-126">방법: 검색 프록시 구현</span><span class="sxs-lookup"><span data-stu-id="50ee9-126">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="50ee9-127">방법: 검색 프록시를 사용하여 서비스를 찾는 클라이언트 애플리케이션 구현</span><span class="sxs-lookup"><span data-stu-id="50ee9-127">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
