---
description: '자세히 알아보기: DataContractJsonSerializer 샘플'
title: DataContractJsonSerializer 샘플
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 258cd38f9ee532e5d750b4cabaa4214366835be7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726353"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="0fbd7-103">DataContractJsonSerializer 샘플</span><span class="sxs-lookup"><span data-stu-id="0fbd7-103">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="0fbd7-104">이 샘플은에 대 한 것입니다 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0fbd7-104">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="0fbd7-105">JSON 직렬화 및 역직렬화를 포함 하는 대부분의 시나리오에서는 [ 네임 스페이스의System.Text.Js](../../../standard/serialization/system-text-json-overview.md)에 api를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="0fbd7-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>는 <xref:System.Runtime.Serialization.DataContractSerializer>와 동일한 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="0fbd7-107">JSON 데이터 형식은 AJAX(Asynchronous JavaScript and XML) 스타일 웹 애플리케이션을 작성하는 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-107">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="0fbd7-108">WCF (Windows Communication Foundation)의 AJAX 지원은 ScriptManager 컨트롤을 통해 ASP.NET AJAX와 함께 사용 하도록 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-108">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="0fbd7-109">ASP.NET AJAX에서 WCF (Windows Communication Foundation)를 사용 하는 방법에 대 한 예제는 [Ajax 샘플](ajax.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-109">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="0fbd7-110">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-110">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="0fbd7-111">샘플에서는 `Person` 데이터 계약을 사용하여 serialization 및 deserialization을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-111">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="0fbd7-112">`Person` 형식의 인스턴스를 JSON으로 serialize하려면 먼저 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>를 만들고 `WriteObject` 메서드를 사용하여 스트림에 JSON 데이터를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-112">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="0fbd7-113">메모리 스트림에는 유효한 JSON 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-113">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="0fbd7-114">샘플에서는 JSON 데이터에서 개체로의 역직렬화를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-114">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="0fbd7-115">그 후에 스트림을 되감고 `ReadObject`를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-115">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="0fbd7-116">`p2` 개체를 확인하면 JSON 데이터가 올바르게 역직렬화된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-116">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0fbd7-117">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fbd7-118">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0fbd7-119">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fbd7-120">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0fbd7-121">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="0fbd7-121">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="0fbd7-122">[Windows Communication Foundation 샘플 빌드](building-the-samples.md)에 설명 된 대로 JsonSerialization 솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-122">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="0fbd7-123">결과 콘솔 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0fbd7-123">Run the resulting console application.</span></span>  
