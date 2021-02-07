---
description: '자세히 알아보기: 강력한 형식의 확장 샘플'
title: 강력한 형식의 확장 샘플
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: dd0a12b07db3f805f041742c8957cd46bb418bad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668762"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="032ce-103">강력한 형식의 확장 샘플</span><span class="sxs-lookup"><span data-stu-id="032ce-103">Strongly typed extensions sample</span></span>

<span data-ttu-id="032ce-104">이 샘플에서는 예를 들기 위해 <xref:System.ServiceModel.Syndication.SyndicationFeed> 클래스를 사용하지만</span><span class="sxs-lookup"><span data-stu-id="032ce-104">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="032ce-105">이 샘플에 나온 패턴은 확장 데이터를 지원하는 모든 배포 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-105">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="032ce-106">배포 개체 모델(<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem> 및 관련 클래스)은 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 및 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 속성을 사용하여 확장명 데이터에 대한 자유로운 형식의 액세스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-106">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="032ce-107">이 샘플에서는 <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> 특정 응용 프로그램 관련 확장을 강력한 형식의 속성으로 사용할 수 있게 하는 및의 사용자 지정 파생 클래스를 구현 하 여 확장 데이터에 대 한 강력한 형식의 액세스를 제공 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-107">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="032ce-108">한 예로 이 샘플에서는 제안된 Atom Threading Extensions RFC에 정의된 확장명 요소를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-108">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="032ce-109">이 샘플은 데모용으로만 사용되며 제안된 사양을 전체 구현할 용도는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-109">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="032ce-110">샘플 XML</span><span class="sxs-lookup"><span data-stu-id="032ce-110">Sample XML</span></span>  

 <span data-ttu-id="032ce-111">다음 XML 예제에서는 추가 `<in-reply-to>` 확장명 요소가 포함된 Atom 1.0 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-111">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="032ce-112">`<in-reply-to>`요소는 세 가지 필수 특성 ( `ref` , `type` 및)을 지정 `href` 하 고 추가 확장 특성 및 확장 요소도 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-112">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="032ce-113">In-Reply-To 요소 모델링</span><span class="sxs-lookup"><span data-stu-id="032ce-113">Modeling the In-Reply-To element</span></span>  

 <span data-ttu-id="032ce-114">이 샘플에서는 `<in-reply-to>`와 함께 사용할 수 있도록 <xref:System.Xml.Serialization.IXmlSerializable> 요소가 <xref:System.Runtime.Serialization.DataContractSerializer>을 구현하는 CLR로 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-114">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="032ce-115">또한 다음 샘플 코드에 표시 된 것 처럼 요소 데이터에 액세스 하기 위한 몇 가지 메서드와 속성을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-115">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="032ce-116">`InReplyToElement` 클래스는 필수 특성의 속성(`HRef`, `MediaType` 및 `Source`)뿐 아니라 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 및 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>를 보유하는 컬렉션을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-116">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="032ce-117">`InReplyToElement` 클래스는 XML에서 개체 인스턴스를 읽고 쓰는 방법을 직접 제어하는 <xref:System.Xml.Serialization.IXmlSerializable> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-117">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="032ce-118">`ReadXml` 메서드는 먼저 자신에게 전달된 `Ref`에서 `HRef`, `Source`, `MediaType` 및 <xref:System.Xml.XmlReader> 속성의 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-118">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="032ce-119">알 수 없는 특성은 모두 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 컬렉션에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-119">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="032ce-120">모든 특성을 읽으면 <xref:System.Xml.XmlReader.ReadStartElement>가 호출되어 판독기가 다음 요소로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-120">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="032ce-121">이 클래스에서 모델링된 요소에는 필수 자식이 없으므로 다음 코드에 나온 것처럼 자식 요소는 `XElement` 인스턴스로 버퍼링되고 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 컬렉션에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-121">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="032ce-122">`WriteXml`에서 `InReplyToElement` 메서드는 먼저 `Ref`, `HRef`, `Source` 및 `MediaType` 속성의 값을 XML 특성으로 씁니다. `WriteXml`은 `WriteXml`의 호출자가 수행한 실제 외부 요소는 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-122">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="032ce-123">다음 코드에 나온 것처럼 이 메서드는 또한 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 및 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>의 내용을 작성기에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-123">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="032ce-124">ThreadedFeed 및 ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="032ce-124">ThreadedFeed and ThreadedItem</span></span>  

 <span data-ttu-id="032ce-125">이 샘플에서는 `SyndicationItems` 확장을 포함하는 `InReplyTo`가 `ThreadedItem` 클래스에 의해 모델링됩니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-125">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="032ce-126">마찬가지로 `ThreadedFeed` 클래스는 항목이 `SyndicationFeed`의 모든 인스턴스인 `ThreadedItem`입니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-126">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="032ce-127">`ThreadedFeed` 클래스는 `SyndicationFeed`에서 상속되고 `OnCreateItem`을 재정의하여 `ThreadedItem`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-127">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="032ce-128">다음 코드에 나온 것처럼 이 클래스는 또한 `Items` 컬렉션에 액세스하기 위한 메서드를 `ThreadedItems`로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-128">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="032ce-129">클래스는 `ThreadedItem` 에서 상속 `SyndicationItem` 되며 `InReplyToElement` 강력한 형식의 속성으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-129">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="032ce-130">이 클래스는 `InReplyTo` 확장 데이터에 대한 편리한 프로그래밍 액세스를 제공하며,</span><span class="sxs-lookup"><span data-stu-id="032ce-130">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="032ce-131">다음 코드에 나온 것처럼 이 클래스는 또한 확장 데이터를 읽고 쓰기 위한 `TryParseElement` 및 `WriteElementExtensions`를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-131">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="032ce-132">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="032ce-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="032ce-133">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="032ce-134">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="032ce-135">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="032ce-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="032ce-136">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-136">The samples may already be installed on your computer.</span></span> <span data-ttu-id="032ce-137">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="032ce-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="032ce-138">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="032ce-139">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="032ce-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
