---
title: 격리 유형
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET], isolated storage
- assemblies [.NET], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
ms.openlocfilehash: ce6afc6438060b88e8740eab24ace960f3b78fa3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830534"
---
# <a name="types-of-isolation"></a><span data-ttu-id="bfc25-102">격리 유형</span><span class="sxs-lookup"><span data-stu-id="bfc25-102">Types of isolation</span></span>

<span data-ttu-id="bfc25-103">격리된 스토리지에 대한 액세스는 항상 스토리지를 만든 사용자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-103">Access to isolated storage is always restricted to the user who created it.</span></span> <span data-ttu-id="bfc25-104">이 유형의 격리를 구현하기 위해 공용 언어 런타임은 운영 체제에서 인식하고 저장소가 열릴 때 코드가 실행 중인 프로세스에 연결된 ID인 사용자 ID의 동일한 표기법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-104">To implement this type of isolation, the common language runtime uses the same notion of user identity that the operating system recognizes, which is the identity associated with the process in which the code is running when the store is opened.</span></span> <span data-ttu-id="bfc25-105">이 ID는 인증된 사용자 ID이지만 가장으로 인해 현재 사용자의 ID가 동적으로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-105">This identity is an authenticated user identity, but impersonation can cause the identity of the current user to change dynamically.</span></span>  
  
 <span data-ttu-id="bfc25-106">격리된 스토리지에 대한 액세스는 애플리케이션의 도메인 및 어셈블리에 연결되거나 어셈블리에만 연결된 ID에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-106">Access to isolated storage is also restricted according to the identity associated with the application's domain and assembly, or with the assembly alone.</span></span> <span data-ttu-id="bfc25-107">런타임은 다음과 같은 방법으로 이러한 ID를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-107">The runtime obtains these identities in the following ways:</span></span>  
  
- <span data-ttu-id="bfc25-108">도메인 ID는 애플리케이션의 증거를 나타내며 웹 애플리케이션의 경우 전체 URL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-108">Domain identity represents the evidence of the application, which in the case of a web application might be the full URL.</span></span> <span data-ttu-id="bfc25-109">셸에 호스트된 코드의 경우 도메인 ID는 애플리케이션 디렉터리 경로를 기반으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-109">For shell-hosted code, the domain identity might be based on the application directory path.</span></span> <span data-ttu-id="bfc25-110">예를 들어 실행 파일이 C:\Office\MyApp.exe 경로에서 실행되는 경우 도메인 ID는 C:\Office\MyApp.exe입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-110">For example, if the executable runs from the path C:\Office\MyApp.exe, the domain identity would be C:\Office\MyApp.exe.</span></span>  
  
- <span data-ttu-id="bfc25-111">어셈블리 ID는 어셈블리의 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-111">Assembly identity is the evidence of the assembly.</span></span> <span data-ttu-id="bfc25-112">이 ID는 암호화 디지털 서명에서 가져올 수 있고 어셈블리의 [강력한 이름](../assembly/strong-named.md), 어셈블리의 소프트웨어 게시자 또는 해당 URL ID가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-112">This might come from a cryptographic digital signature, which can be the assembly's [strong name](../assembly/strong-named.md), the software publisher of the assembly, or its URL identity.</span></span> <span data-ttu-id="bfc25-113">어셈블리에 강력한 이름과 소프트웨어 게시자 ID가 모두 있는 경우 소프트웨어 게시자 ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-113">If an assembly has both a strong name and a software publisher identity, then the software publisher identity is used.</span></span> <span data-ttu-id="bfc25-114">어셈블리를 인터넷에서 가져오고 서명이 없는 경우 URL ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-114">If the assembly comes from the Internet and is unsigned, the URL identity is used.</span></span> <span data-ttu-id="bfc25-115">어셈블리 및 강력한 이름에 대한 자세한 내용은 [어셈블리를 사용한 프로그래밍](../assembly/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfc25-115">For more information about assemblies and strong names, see [Programming with Assemblies](../assembly/index.md).</span></span>  
  
- <span data-ttu-id="bfc25-116">로밍 저장소는 로밍 사용자 프로필이 있는 사용자와 함께 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-116">Roaming stores move with a user that has a roaming user profile.</span></span> <span data-ttu-id="bfc25-117">파일은 네트워크 디렉터리에 기록되고 사용자가 로그인한 컴퓨터로 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-117">Files are written to a network directory and are downloaded to any computer the user logs into.</span></span> <span data-ttu-id="bfc25-118">로밍 사용자 프로필에 대한 자세한 내용은 <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfc25-118">For more information about roaming user profiles, see <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="bfc25-119">사용자, 도메인 및 어셈블리 ID의 개념을 결합하면 격리된 스토리지가 다음 방법으로 데이터를 격리할 수 있으며 각 방법에는 고유한 사용 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-119">By combining the concepts of user, domain, and assembly identity, isolated storage can isolate data in the following ways, each of which has its own usage scenarios:</span></span>  
  
- [<span data-ttu-id="bfc25-120">사용자 및 어셈블리별 격리</span><span class="sxs-lookup"><span data-stu-id="bfc25-120">Isolation by user and assembly</span></span>](#UserAssembly)  
  
- [<span data-ttu-id="bfc25-121">사용자, 도메인 및 어셈블리별 격리</span><span class="sxs-lookup"><span data-stu-id="bfc25-121">Isolation by user, domain, and assembly</span></span>](#UserDomainAssembly)  
  
 <span data-ttu-id="bfc25-122">이러한 경리 중 하나가 로밍 사용자 프로필과 결합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-122">Either of these isolations can be combined with a roaming user profile.</span></span> <span data-ttu-id="bfc25-123">자세한 내용은 [격리된 스토리지 및 로밍](#Roaming) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfc25-123">For more information, see the section [Isolated Storage and Roaming](#Roaming).</span></span>  
  
 <span data-ttu-id="bfc25-124">다음 그림은 저장소를 여러 범위로 격리하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-124">The following illustration demonstrates how stores are isolated in different scopes:</span></span>  
  
 ![사용자 및 어셈블리별 격리를 보여주는 다이어그램](./media/types-of-isolation/isolated-storage-types.gif)  
  
 <span data-ttu-id="bfc25-126">로밍 저장소를 제외하고 격리된 스토리지는 지정된 컴퓨터에 로컬인 스토리지 시설을 사용하므로 항상 컴퓨터에서 암시적으로 격리됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-126">Except for roaming stores, isolated storage is always implicitly isolated by computer because it uses the storage facilities that are local to a given computer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bfc25-127">Windows 8.x 스토어 앱에는 격리된 스토리지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-127">Isolated storage is not available for Windows 8.x Store apps.</span></span> <span data-ttu-id="bfc25-128">대신에 Windows Runtime API에 포함된 `Windows.Storage` 네임스페이스의 애플리케이션 데이터 클래스를 사용하여 로컬 데이터 및 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-128">Instead, use the application data classes in the `Windows.Storage` namespaces included in the Windows Runtime API to store local data and files.</span></span> <span data-ttu-id="bfc25-129">자세한 내용은 Windows 개발자 센터에서 [애플리케이션 데이터](/previous-versions/windows/apps/hh464917(v=win.10)) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfc25-129">For more information, see [Application data](/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.</span></span>  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a><span data-ttu-id="bfc25-130">사용자 및 어셈블리별 격리</span><span class="sxs-lookup"><span data-stu-id="bfc25-130">Isolation by User and Assembly</span></span>  
 <span data-ttu-id="bfc25-131">데이터 저장소를 사용하는 어셈블리를 애플리케이션 도메인에서 액세스할 수 있어야 하는 경우 사용자 및 어셈블리별로 격리하는 것이 적절합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-131">When the assembly that uses the data store needs to be accessible from any application's domain, isolation by user and assembly is appropriate.</span></span> <span data-ttu-id="bfc25-132">일반적으로 이 상황에서 격리된 스토리지는 여러 애플리케이션에 적용되는 데이터를 저장하는 데 사용되며 사용자 이름 또는 라이선스 정보와 같은 특정 애플리케이션에 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-132">Typically, in this situation, isolated storage is used to store data that applies across multiple applications and is not tied to any particular application, such as the user's name or license information.</span></span> <span data-ttu-id="bfc25-133">사용자 및 어셈블리별로 격리된 스토리지에 액세스하려면 애플리케이션 간에 정보를 전송하기 위해 코드를 신뢰할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-133">To access storage isolated by user and assembly, code must be trusted to transfer information between applications.</span></span> <span data-ttu-id="bfc25-134">일반적으로 사용자 및 어셈블리별 격리는 인트라넷에서 허용되지만 인터넷에는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-134">Typically, isolation by user and assembly is allowed on intranets but not on the Internet.</span></span> <span data-ttu-id="bfc25-135">정적 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> 메서드를 호출하고 사용자 및 어셈블리로 전달하면 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>는 이 유형의 격리를 통해 스토리지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-135">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> method and passing in a user and an assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="bfc25-136">다음 코드 예제에서는 사용자 및 어셈블리별로 격리되는 저장소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-136">The following code example retrieves a store that is isolated by user and assembly.</span></span> <span data-ttu-id="bfc25-137">`isoFile` 개체를 통해 저장소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-137">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 <span data-ttu-id="bfc25-138">증거 매개 변수를 사용하는 예제는 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfc25-138">For an example that uses the evidence parameters, see <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.</span></span>  
  
 <span data-ttu-id="bfc25-139"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 메서드는 다음 코드 예제와 같이 바로 가기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-139">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="bfc25-140">이 바로 가기는 로밍할 수 있는 저장소를 여는 데 사용할 수 없습니다. 이 경우에는 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-140">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a><span data-ttu-id="bfc25-141">사용자, 도메인 및 어셈블리별 격리</span><span class="sxs-lookup"><span data-stu-id="bfc25-141">Isolation by User, Domain, and Assembly</span></span>  
 <span data-ttu-id="bfc25-142">애플리케이션에서 개인 데이터 스토리지가 필요한 타사 어셈블리를 사용하는 경우 격리된 스토리지를 사용하여 개인 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-142">If your application uses a third-party assembly that requires a private data store, you can use isolated storage to store the private data.</span></span> <span data-ttu-id="bfc25-143">사용자, 도메인 및 어셈블리별 격리를 사용하면 어셈블리가 저장소를 만들 때 실행 중이던 애플리케이션에서 어셈블리가 사용될 경우 및 저장소를 만든 사용자가 애플리케이션을 실행하는 경우에만 지정된 어셈블리의 코드만 해당 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-143">Isolation by user, domain, and assembly ensures that only code in a given assembly can access the data, and only when the assembly is used by the application that was running when the assembly created the store, and only when the user for whom the store was created runs the application.</span></span> <span data-ttu-id="bfc25-144">사용자, 도메인 및 어셈블리별 격리를 사용하면 타사 어셈블리에 의해 데이터가 다른 애플리케이션으로 누출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-144">Isolation by user, domain, and assembly keeps the third-party assembly from leaking data to other applications.</span></span> <span data-ttu-id="bfc25-145">격리된 스토리지를 사용하려고 하지만 어떤 격리 유형을 사용할지 확신할 수 없는 경우에는 기본적으로 이 격리 유형을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-145">This isolation type should be your default choice if you know that you want to use isolated storage but are not sure which type of isolation to use.</span></span> <span data-ttu-id="bfc25-146"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>의 정적 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 메서드를 호출하고 사용자, 도메인 및 어셈블리로 전달하면 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>는 이 유형의 격리를 통해 스토리지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-146">Calling the static <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> and passing in a user, domain, and assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> returns storage with this kind of isolation.</span></span>  
  
 <span data-ttu-id="bfc25-147">다음 코드 예제에서는 사용자, 도메인 및 어셈블리별로 격리되는 저장소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-147">The following code example retrieves a store isolated by user, domain, and assembly.</span></span> <span data-ttu-id="bfc25-148">`isoFile` 개체를 통해 저장소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-148">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 <span data-ttu-id="bfc25-149">또 다른 메서드는 다음 코드 예제와 같이 바로 가기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-149">Another method is available as a shortcut, as shown in the following code example.</span></span> <span data-ttu-id="bfc25-150">이 바로 가기는 로밍할 수 있는 저장소를 여는 데 사용할 수 없습니다. 이 경우에는 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-150">This shortcut cannot be used to open stores that are capable of roaming; use <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> in such cases.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a><span data-ttu-id="bfc25-151">격리된 스토리지 및 로밍</span><span class="sxs-lookup"><span data-stu-id="bfc25-151">Isolated Storage and Roaming</span></span>  
 <span data-ttu-id="bfc25-152">로밍 사용자 프로필은 사용자가 네트워크에서 ID를 설정하고 해당 ID를 사용하여 모든 개인 설정을 적용하여 네트워크 컴퓨터에 로그인하도록 하는 Windows 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-152">Roaming user profiles are a Windows feature that enables a user to set up an identity on a network and use that identity to log into any network computer, carrying over all personalized settings.</span></span> <span data-ttu-id="bfc25-153">격리된 스토리지를 사용하는 어셈블리는 사용자의 격리된 스토리지가 로밍 사용자 프로필과 함께 이동되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-153">An assembly that uses isolated storage can specify that the user's isolated storage should move with the roaming user profile.</span></span> <span data-ttu-id="bfc25-154">로밍은 사용자 및 어셈블리별 격리 및 사용자, 도메인 및 어셈블리별 격리와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-154">Roaming can be used in conjunction with isolation by user and assembly or with isolation by user, domain, and assembly.</span></span> <span data-ttu-id="bfc25-155">로밍 범위를 사용하지 않으면 로밍 사용자 프로필이 사용되는 경우에도 저장소가 로밍되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-155">If a roaming scope is not used, stores will not roam even if a roaming user profile is used.</span></span>  
  
 <span data-ttu-id="bfc25-156">다음 코드 예제에서는 사용자 및 어셈블리별로 격리된 로밍 저장소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-156">The following code example retrieves a roaming store isolated by user and assembly.</span></span> <span data-ttu-id="bfc25-157">`isoFile` 개체를 통해 저장소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-157">The store can be accessed through the `isoFile` object.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 <span data-ttu-id="bfc25-158">사용자, 도메인 및 애플리케이션별로 격리된 로밍 저장소를 만들 위해 도메인 범위를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-158">A domain scope can be added to create a roaming store isolated by user, domain, and application.</span></span> <span data-ttu-id="bfc25-159">다음 코드 예제에서는 이 작업을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfc25-159">The following code example demonstrates this.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="bfc25-160">참조</span><span class="sxs-lookup"><span data-stu-id="bfc25-160">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="bfc25-161">격리된 스토리지</span><span class="sxs-lookup"><span data-stu-id="bfc25-161">Isolated Storage</span></span>](isolated-storage.md)
