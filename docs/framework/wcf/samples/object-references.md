---
description: '자세한 정보: 개체 참조'
title: 개체 참조
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ae76cf13b4ccbbde2ad6d5022248bbcfeb263879
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732412"
---
# <a name="object-references"></a><span data-ttu-id="124a0-103">개체 참조</span><span class="sxs-lookup"><span data-stu-id="124a0-103">Object References</span></span>

<span data-ttu-id="124a0-104">이 샘플에서는 서버와 클라이언트 간에 개체를 참조로 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-104">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="124a0-105">이 샘플에서는 시뮬레이트된 *소셜 네트워크* 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-105">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="124a0-106">인맥 네트워크는 친구 목록을 포함하는 `Person` 클래스로 구성되며, 이 목록의 친구는 `Person` 클래스의 인스턴스이며 자체적으로도 친구 목록을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-106">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="124a0-107">이를 기반으로 개체 그래프가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-107">This creates a graph of objects.</span></span> <span data-ttu-id="124a0-108">서비스는 이러한 인맥 네트워크에 대한 작업을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-108">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="124a0-109">이 샘플에서 서비스는 IIS(인터넷 정보 서비스)를 통해 호스팅되고 클라이언트는 콘솔 애플리케이션(.exe)입니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-109">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="124a0-110">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="124a0-111">서비스</span><span class="sxs-lookup"><span data-stu-id="124a0-111">Service</span></span>  

 <span data-ttu-id="124a0-112">`Person` 클래스에는 <xref:System.Runtime.Serialization.DataContractAttribute> 특성이 적용되어 있으며, 클래스를 참조 형식으로 선언하도록 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 필드가 `true`로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-112">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="124a0-113">모든 속성에는 <xref:System.Runtime.Serialization.DataMemberAttribute> 특성이 적용되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-113">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="124a0-114">`GetPeopleInNetwork` 작업은 `Person` 형식의 매개 변수를 받아 인맥 네트워크의 모든 사람, 즉 `friends` 목록에 있는 모든 사람과 친구의 친구 등을 중복되는 항목 없이 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-114">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="124a0-115">`GetMutualFriends` 작업은 `Person` 형식의 매개 변수를 받아 서로의 `friends` 목록에 동시에 존재하는 모든 친구를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-115">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="124a0-116">`GetCommonFriends` 작업은 `Person` 형식의 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-116">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="124a0-117">이 목록에는 두 개의 `Person` 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-117">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="124a0-118">이 작업은 입력 목록에 있는 두 `Person` 개체 모두의 `friends` 목록에 있는 `Person` 개체의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-118">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="124a0-119">클라이언트</span><span class="sxs-lookup"><span data-stu-id="124a0-119">Client</span></span>  

 <span data-ttu-id="124a0-120">클라이언트 프록시는 Visual Studio의 **서비스 참조 추가** 기능을 사용 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-120">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="124a0-121">5개의 `Person` 개체로 구성된 인맥 네트워크가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-121">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="124a0-122">클라이언트는 서비스의 메서드 3개를 각각 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-122">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="124a0-123">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="124a0-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="124a0-124">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="124a0-125">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="124a0-126">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="124a0-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="124a0-127">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="124a0-128">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="124a0-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="124a0-129">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="124a0-130">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="124a0-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="124a0-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="124a0-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="124a0-132">상호 운영 가능한 개체 참조</span><span class="sxs-lookup"><span data-stu-id="124a0-132">Interoperable Object References</span></span>](../feature-details/interoperable-object-references.md)
