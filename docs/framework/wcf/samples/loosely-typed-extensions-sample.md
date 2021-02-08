---
description: '자세한 정보: Loosely-Typed 확장 샘플'
title: 느슨한 형 확장 샘플
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: cd430a922a35baf0ed9ce387b7df81fa3af6b35d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793235"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="72fc3-103">느슨한 형 확장 샘플</span><span class="sxs-lookup"><span data-stu-id="72fc3-103">Loosely-Typed Extensions Sample</span></span>

<span data-ttu-id="72fc3-104">배포 개체 모델은 확장 데이터, 즉 배포 피드의 XML 표현에는 있지만 <xref:System.ServiceModel.Syndication.SyndicationFeed> 및 <xref:System.ServiceModel.Syndication.SyndicationItem>과 같은 클래스에서 명시적으로 노출되지 않는 정보로 작업할 수 있도록 풍부한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-104">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="72fc3-105">이 샘플에서는 확장명 데이터로 작업하는 기본적인 기술을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-105">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="72fc3-106">이 샘플에서는 예를 들기 위해 <xref:System.ServiceModel.Syndication.SyndicationFeed> 클래스를 사용하지만</span><span class="sxs-lookup"><span data-stu-id="72fc3-106">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="72fc3-107">이 샘플에 나온 패턴은 확장명 데이터를 지원하는 다음과 같은 모든 배포 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-107">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="72fc3-108">샘플 XML</span><span class="sxs-lookup"><span data-stu-id="72fc3-108">Sample XML</span></span>  

 <span data-ttu-id="72fc3-109">참고로 이 샘플에 사용된 XML 문서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-109">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="72fc3-110">이 문서에는 다음과 같은 확장명 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-110">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="72fc3-111">`myAttribute` 요소의 `<feed>` 특성</span><span class="sxs-lookup"><span data-stu-id="72fc3-111">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="72fc3-112">`<simpleString>` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-112">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="72fc3-113">`<DataContractExtension>` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-113">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="72fc3-114">`<XmlSerializerExtension>` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-114">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="72fc3-115">`<xElementExtension>` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-115">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="72fc3-116">확장명 데이터 쓰기</span><span class="sxs-lookup"><span data-stu-id="72fc3-116">Writing Extension Data</span></span>  

 <span data-ttu-id="72fc3-117">특성 확장명은 다음 샘플 코드에서와 같이 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 컬렉션에 항목을 추가하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-117">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="72fc3-118">요소 확장은 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 컬렉션에 항목을 추가하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-118">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="72fc3-119">이러한 확장은 문자열, .NET Framework 개체의 XML serialization 또는 직접 코딩한 XML 노드와 같은 기본값이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-119">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="72fc3-120">다음 샘플 코드는 `simpleString`이라는 확장명 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-120">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="72fc3-121">이 요소에 대 한 XML 네임 스페이스는 빈 네임 스페이스 ("")이 고 해당 값은 문자열 "hello, 세계!"를 포함 하는 텍스트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-121">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="72fc3-122">여러 개의 중첩 요소로 구성된 복합 요소 확장을 만드는 한 가지 방법은 다음 예제에 나온 것처럼 serialization을 위한 .NET Framework API를 사용하는 것입니다. <xref:System.Runtime.Serialization.DataContractSerializer>와 <xref:System.Xml.Serialization.XmlSerializer>가 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-122">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="72fc3-123">이 예제에서 `DataContractExtension` 및 `XmlSerializerExtension`은 serializer와 함께 사용하도록 작성된 사용자 지정 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-123">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="72fc3-124">또한 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> 클래스를 사용하여 <xref:System.Xml.XmlReader> 인스턴스에서 요소 확장을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-124">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="72fc3-125">이 경우에는 다음 샘플 코드에서와 같이 <xref:System.Xml.Linq.XElement>와 같은 XML 처리 API와 손쉽게 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-125">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="72fc3-126">확장 데이터 읽기</span><span class="sxs-lookup"><span data-stu-id="72fc3-126">Reading Extension Data</span></span>  

 <span data-ttu-id="72fc3-127">특성 확장명의 값은 다음 샘플 코드에서와 같이 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 컬렉션에서 <xref:System.Xml.XmlQualifiedName>으로 특성을 조회하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-127">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="72fc3-128">요소 확장에는 `ReadElementExtensions<T>` 메서드를 사용하여 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-128">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="72fc3-129">`XmlReader` 메서드를 사용하여 개별 요소 확장의 <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-129">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72fc3-130">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="72fc3-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="72fc3-131">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="72fc3-132">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="72fc3-133">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="72fc3-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="72fc3-134">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72fc3-135">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="72fc3-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="72fc3-136">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72fc3-137">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fc3-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="72fc3-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72fc3-138">See also</span></span>

- [<span data-ttu-id="72fc3-139">강력한 형식의 확장</span><span class="sxs-lookup"><span data-stu-id="72fc3-139">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="72fc3-140">WCF 배포</span><span class="sxs-lookup"><span data-stu-id="72fc3-140">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
