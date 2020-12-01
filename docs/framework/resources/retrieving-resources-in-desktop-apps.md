---
title: 데스크톱 응용 프로그램의 리소스 검색
description: 데스크톱 앱의 리소스를 검색합니다. 기본 어셈블리와 함께 기본(중립) 문화권에 대한 리소스를 패키지하고 각 문화권에 대한 위성 어셈블리를 만듭니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
ms.openlocfilehash: 26e4367d28193ce731198ee0ba3d3b35d83cf19c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254547"
---
# <a name="retrieving-resources-in-desktop-apps"></a><span data-ttu-id="f4d2c-104">데스크톱 응용 프로그램의 리소스 검색</span><span class="sxs-lookup"><span data-stu-id="f4d2c-104">Retrieving Resources in Desktop Apps</span></span>

<span data-ttu-id="f4d2c-105">.NET Framework 데스크톱 앱의 지역화된 리소스로 작업할 경우에는 기본 또는 중립 문화권의 리소스를 주 어셈블리와 패키지하여 앱이 지원하는 각 언어 또는 문화권에 대해 별도의 위성 어셈블리를 만드는 것이 가장 바람직합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-105">When you work with localized resources in .NET Framework desktop apps, you should ideally package the resources for the default or neutral culture with the main assembly and create a separate satellite assembly for each language or culture that your app supports.</span></span> <span data-ttu-id="f4d2c-106">그런 다음 <xref:System.Resources.ResourceManager> 클래스를 다음 섹션에 설명한 대로 사용하여 명명된 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-106">You can then use the <xref:System.Resources.ResourceManager> class as described in the next section to access named resources.</span></span> <span data-ttu-id="f4d2c-107">주 어셈블리와 위성 어셈블리에 리소스를 포함하지 않으려는 경우 이 문서의 뒷부분에 나오는 [.resources 파일에서 리소스 검색](#from_file) 섹션에서 설명한 것처럼, 이진 .resources 파일에 직접 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-107">If you choose not to embed your resources in the main assembly and satellite assemblies, you can also access binary .resources files directly, as discussed in the section [Retrieving Resources from .resources files](#from_file) later in this article.</span></span>  <span data-ttu-id="f4d2c-108">Windows 8.x 스토어 앱에서 리소스를 검색하려면 [Windows 스토어 앱에서 리소스 만들기 및 검색](/previous-versions/windows/apps/hh694557(v=vs.140)) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-108">To retrieve resources in Windows 8.x Store apps, see [Creating and retrieving resources in Windows Store apps](/previous-versions/windows/apps/hh694557(v=vs.140)).</span></span>  
  
<a name="from_assembly"></a>

## <a name="retrieving-resources-from-assemblies"></a><span data-ttu-id="f4d2c-109">어셈블리에서 리소스 검색</span><span class="sxs-lookup"><span data-stu-id="f4d2c-109">Retrieving Resources from Assemblies</span></span>  

 <span data-ttu-id="f4d2c-110"><xref:System.Resources.ResourceManager> 클래스는 런타임에 리소스에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-110">The <xref:System.Resources.ResourceManager> class provides access to resources at run time.</span></span> <span data-ttu-id="f4d2c-111"><xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> 메서드를 사용하여 문자열 리소스를 검색하거나, <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> 또는 <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> 메서드를 사용하여 비문자열 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-111">You use the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method to retrieve string resources and the <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> or <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> method to retrieve non-string resources.</span></span> <span data-ttu-id="f4d2c-112">각 메서드에 두 개의 오버로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-112">Each method has two overloads:</span></span>  
  
- <span data-ttu-id="f4d2c-113">단일 매개 변수가 리소스의 이름을 포함하는 문자열인 오버로드입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-113">An overload whose single parameter is a string that contains the name of the resource.</span></span> <span data-ttu-id="f4d2c-114">메서드는 현재 스레드 문화권에 대한 해당 리소스를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-114">The method attempts to retrieve that resource for the current thread culture.</span></span> <span data-ttu-id="f4d2c-115">자세한 내용은 <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>및 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 메서드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-115">For more information, see the <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, and <xref:System.Resources.ResourceManager.GetStream%28System.String%29> methods.</span></span>  
  
- <span data-ttu-id="f4d2c-116">리소스 이름을 포함하는 문자열, 리소스가 검색될 문화권을 나타내는 <xref:System.Globalization.CultureInfo> 개체와 같은 두 개의 매개 변수가 있는 오버로드입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-116">An overload that has two parameters: a string containing the name of the resource, and a <xref:System.Globalization.CultureInfo> object that represents the culture whose resource is to be retrieved.</span></span> <span data-ttu-id="f4d2c-117">해당 문화권에 대해 설정된 리소스를 찾을 수 없는 경우 리소스 관리자는 적절한 리소스를 검색하기 위해 대체(fallback) 규칙을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-117">If a resource set for that culture cannot be found, the resource manager uses fallback rules to retrieve an appropriate resource.</span></span> <span data-ttu-id="f4d2c-118">자세한 내용은 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>및 <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> 메서드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-118">For more information, see the <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, and <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> methods.</span></span>  
  
 <span data-ttu-id="f4d2c-119">리소스 관리자는 앱이 문화권 관련 리소스를 검색하는 방법을 제어하기 위해 리소스 대체 프로세스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-119">The resource manager uses the resource fallback process to control how the app retrieves culture-specific resources.</span></span> <span data-ttu-id="f4d2c-120">자세한 내용은 [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md)의 "리소스 대체 프로세스" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-120">For more information, see the "Resource Fallback Process" section in [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span> <span data-ttu-id="f4d2c-121"><xref:System.Resources.ResourceManager> 개체를 인스턴스화하는 방법에 대한 자세한 내용은 <xref:System.Resources.ResourceManager> 클래스 항목의 "ResourceManager 개체 인스턴스화" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-121">For information about instantiating a <xref:System.Resources.ResourceManager> object, see the "Instantiating a ResourceManager Object" section in the <xref:System.Resources.ResourceManager> class topic.</span></span>  
  
### <a name="retrieving-string-data-an-example"></a><span data-ttu-id="f4d2c-122">문자열 데이터 검색: 예제</span><span class="sxs-lookup"><span data-stu-id="f4d2c-122">Retrieving String Data: An Example</span></span>  

 <span data-ttu-id="f4d2c-123">다음 예제는 현재 UI 문화권의 문자열 리소스를 검색하기 위해 <xref:System.Resources.ResourceManager.GetString%28System.String%29> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-123">The following example calls the <xref:System.Resources.ResourceManager.GetString%28System.String%29> method to retrieve the string resources of the current UI culture.</span></span> <span data-ttu-id="f4d2c-124">영어(미국) 문화권에 대해서는 중립 문자열 리소스를, 프랑스어(프랑스) 및 러시아어(러시아) 문화권에 대해서는 지역화된 리소스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-124">It includes a neutral string resource for the English (United States) culture and localized resources for the French (France) and Russian (Russia) cultures.</span></span> <span data-ttu-id="f4d2c-125">다음 영어(미국) 리소스는 Strings.txt라는 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-125">The following English (United States) resource is in a file named Strings.txt:</span></span>  
  
```text
TimeHeader=The current time is  
```  
  
 <span data-ttu-id="f4d2c-126">프랑스어(프랑스) 리소스 Strings.fr-FR.txt라는 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-126">The French (France) resource is in a file named Strings.fr-FR.txt:</span></span>  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 <span data-ttu-id="f4d2c-127">러시아어(러시아) 리소스는 Strings.ru-RU.txt라는 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-127">The Russian (Russia) resource is in a file named Strings.ru-RU-txt:</span></span>  
  
```text
TimeHeader=Текущее время —  
```  
  
 <span data-ttu-id="f4d2c-128">코드의 C# 버전에 대해서는 GetString.cs라는 이름의 파일에 있고 Visual Basic 버전에 대해서는 GetString.vb에 있는 이 예제의 소스 코드는 리소스를 사용할 수 있는 세 개의 문화권 및 스페인어(스페인) 문화권, 이렇게 네 개 문화권의 이름을 포함하는 문자열 배열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-128">The source code for this example, which is in a file named GetString.cs for the C# version of the code and GetString.vb for the Visual Basic version, defines a string array that contains the name of four cultures: the three cultures for which resources are available and the Spanish (Spain) culture.</span></span> <span data-ttu-id="f4d2c-129">임의로 다섯 번 실행되는 루프는 이러한 문화권 중 하나를 선택하고 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 및 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 속성을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-129">A loop that executes five times randomly selects one of these cultures and assigns it to the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="f4d2c-130">그런 다음 <xref:System.Resources.ResourceManager.GetString%28System.String%29> 메서드를 호출하여 지역화된 문자열을 검색하고 하루 중 시간과 함께 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-130">It then calls the <xref:System.Resources.ResourceManager.GetString%28System.String%29> method to retrieve the localized string, which it displays along with the time of day.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 <span data-ttu-id="f4d2c-131">다음 배치(.bat) 파일은 예제를 컴파일하고 해당 디렉터리에 위성 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-131">The following batch (.bat) file compiles the example and generates satellite assemblies in the appropriate directories.</span></span> <span data-ttu-id="f4d2c-132">C# 언어 및 컴파일러에 대한 명령이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-132">The commands are provided for the C# language and compiler.</span></span> <span data-ttu-id="f4d2c-133">Visual Basic의 경우 `csc` 를 `vbc`로, `GetString.cs` 를 `GetString.vb`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-133">For Visual Basic, change `csc` to `vbc`, and change `GetString.cs` to `GetString.vb`.</span></span>  
  
```console
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 <span data-ttu-id="f4d2c-134">현재 UI 문화권이 스페인어(스페인)인 경우 예제에서는 영어 리소스를 표시합니다. 스페인어 리소스를 사용할 수 없거나 영어가 예제의 기본 문화권이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-134">When the current UI culture is Spanish (Spain), note that the example displays English language resources, because Spanish language resources are unavailable, and English is the example's default culture.</span></span>  
  
### <a name="retrieving-object-data-two-examples"></a><span data-ttu-id="f4d2c-135">개체 데이터 검색: 두 가지 예제</span><span class="sxs-lookup"><span data-stu-id="f4d2c-135">Retrieving Object Data: Two Examples</span></span>  

 <span data-ttu-id="f4d2c-136">개체 데이터를 검색하려면 <xref:System.Resources.ResourceManager.GetObject%2A> 및 <xref:System.Resources.ResourceManager.GetStream%2A> 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-136">You can use the <xref:System.Resources.ResourceManager.GetObject%2A> and <xref:System.Resources.ResourceManager.GetStream%2A> methods to retrieve object data.</span></span> <span data-ttu-id="f4d2c-137">여기에는 기본 데이터 형식, 직렬화 가능 개체, 이진 형식으로 저장된 개체(예: 이미지)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-137">This includes primitive data types, serializable objects, and objects that are stored in binary format (such as images).</span></span>  
  
 <span data-ttu-id="f4d2c-138">다음 예제에서는 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 메서드를 사용하여 앱의 열기 시작 창에 사용되는 비트맵을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-138">The following example uses the <xref:System.Resources.ResourceManager.GetStream%28System.String%29> method to retrieve a bitmap that is used in an app's opening splash window.</span></span> <span data-ttu-id="f4d2c-139">CreateResources.cs(C#) 또는 CreateResources.vb(Visual Basic)라는 이름의 파일에 있는 다음 소스 코드는 serialize된 이미지를 포함하는 .resx 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-139">The following source code in a file named CreateResources.cs (for C#) or CreateResources.vb (for Visual Basic) generates a .resx file that contains the serialized image.</span></span> <span data-ttu-id="f4d2c-140">이 경우 이미지는 SplashScreen.jpg라는 파일에서 로드됩니다. 이 파일 이름을 수정하여 자신의 고유한 이미지로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-140">In this case, the image is loaded from a file named SplashScreen.jpg; you can modify the file name to substitute your own image.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 <span data-ttu-id="f4d2c-141">다음 코드는 리소스를 검색하고 <xref:System.Windows.Forms.PictureBox> 컨트롤에 이미지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-141">The following code retrieves the resource and displays the image in a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 <span data-ttu-id="f4d2c-142">C# 예제를 빌드하려면 다음 배치 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-142">You can use the following batch file to build the C# example.</span></span> <span data-ttu-id="f4d2c-143">Visual Basic의 경우 `csc` 를 `vbc`로 변경하고, 소스 코드 파일의 확장을 `.cs` 에서 `.vb`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-143">For Visual Basic, change `csc` to `vbc`, and change the extension of the source code file from `.cs` to `.vb`.</span></span>  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 <span data-ttu-id="f4d2c-144">다음 예제에서는 <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> 메서드를 사용하여 사용자 지정 개체를 역직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-144">The following example uses the <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> method to deserialize a custom object.</span></span> <span data-ttu-id="f4d2c-145">예제에는 `PersonTable`이라는 다음 구조를 정의하는 UIElements.cs(Visual Basic의 경우 UIElements.vb)라는 소스 코드 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-145">The example includes a source code file named UIElements.cs (UIElements.vb for Visual Basic) that defines the following structure named `PersonTable`.</span></span> <span data-ttu-id="f4d2c-146">이 구조는 테이블 열의 지역화된 이름을 표시하는 일반 테이블 표시 루틴에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-146">This structure is intended to be used by a general table display routine that displays the localized names of table columns.</span></span> <span data-ttu-id="f4d2c-147">`PersonTable` 구조체는 <xref:System.SerializableAttribute> 특성으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-147">Note that the `PersonTable` structure is marked with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 <span data-ttu-id="f4d2c-148">CreateResources.cs(Visual Basic의 경우 CreateResources.vb)라는 파일에서 온 다음 코드는 테이블 제목 및 영어에 대해 지역화된 앱에 대한 정보를 포함하는 `PersonTable` 개체를 저장하는 UIResources.resx라는 XML 리소스 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-148">The following code from a file named CreateResources.cs (CreateResources.vb for Visual Basic) creates an XML resource file named UIResources.resx that stores a table title and a `PersonTable` object that contains information for an app that is localized for the English language.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 <span data-ttu-id="f4d2c-149">그런 다음 GetObject.cs(GetObject.vb)라는 소스 코드 파일의 다음 코드가 리소스를 검색하여 콘솔에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-149">The following code in a source code file named GetObject.cs (GetObject.vb) then retrieves the resources and displays them to the console.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 <span data-ttu-id="f4d2c-150">필요한 리소스 파일 및 어셈블리를 빌드하고 다음 배치 파일을 실행하여 앱을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-150">You can build the necessary resource file and assemblies and run the app by executing the following batch file.</span></span> <span data-ttu-id="f4d2c-151">`/r` 옵션을 사용하여 UIElements.dll에 대한 참조와 함께 Resgen.exe를 제공해야 합니다. 이렇게 해야 `PersonTable` 구조에 대한 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-151">You must use the `/r` option to supply Resgen.exe with a reference to UIElements.dll so that it can access information about the `PersonTable` structure.</span></span> <span data-ttu-id="f4d2c-152">C#을 사용하는 경우 `vbc` 컴파일러 이름을 `csc`로 바꾸고, `.vb` 확장을 `.cs`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-152">If you're using C#, replace the `vbc` compiler name with `csc`, and replace the `.vb` extension with `.cs`.</span></span>  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a><span data-ttu-id="f4d2c-153">위성 어셈블리에 대한 버전 관리 지원</span><span class="sxs-lookup"><span data-stu-id="f4d2c-153">Versioning Support for Satellite Assemblies</span></span>  

 <span data-ttu-id="f4d2c-154">기본적으로 <xref:System.Resources.ResourceManager> 개체는 요청된 리소스를 검색할 때 주 어셈블리의 버전 번호와 일치하는 버전 번호를 가지고 있는 위성 어셈블리를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-154">By default, when the <xref:System.Resources.ResourceManager> object retrieves requested resources, it looks for satellite assemblies that have version numbers that match the version number of the main assembly.</span></span> <span data-ttu-id="f4d2c-155">앱을 배포한 후 주 어셈블리 또는 특정 리소스 위성 어셈블리를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-155">After you have deployed an app, you might want to update the main assembly or specific resource satellite assemblies.</span></span> <span data-ttu-id="f4d2c-156">.NET Framework는 주 어셈블리와 위성 어셈블리 버전 관리에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-156">The .NET Framework provides support for versioning the main assembly and satellite assemblies.</span></span>  
  
 <span data-ttu-id="f4d2c-157"><xref:System.Resources.SatelliteContractVersionAttribute> 특성은 주 어셈블리에 대한 버전 관리 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-157">The <xref:System.Resources.SatelliteContractVersionAttribute> attribute  provides versioning support for a main assembly.</span></span> <span data-ttu-id="f4d2c-158">앱의 주 어셈블리에 대해 이 특성을 지정하면 위성 어셈블리를 업데이트하지 않은 채 주 어셈블리를 업데이트 및 재배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-158">Specifying this attribute on an app's main assembly enables you to update and redeploy a main assembly without updating its satellite assemblies.</span></span> <span data-ttu-id="f4d2c-159">주 어셈블리를 업데이트한 후, 주 어셈블리의 버전 번호는 높이되 위성 계약 버전 번호는 변경하지 않고 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-159">After you update the main assembly, increment the main assembly's version number but leave the satellite contract version number unchanged.</span></span> <span data-ttu-id="f4d2c-160">리소스 관리자는 요청된 리소스를 검색할 때 이 특성에 의해 지정된 위성 어셈블리 버전을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-160">When the resource manager retrieves requested resources, it loads the satellite assembly version specified by this attribute.</span></span>  
  
 <span data-ttu-id="f4d2c-161">게시자 정책 어셈블리는 위성 어셈블리 버전 관리에 대한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-161">Publisher policy assemblies provide support for versioning satellite assemblies.</span></span> <span data-ttu-id="f4d2c-162">주 어셈블리를 업데이트하지 않은 채 위성 어셈블리를 업데이트 및 재배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-162">You can update and redeploy a satellite assembly without updating the main assembly.</span></span> <span data-ttu-id="f4d2c-163">위성 어셈블리를 업데이트한 후, 버전 번호를 높이고 게시자 정책 어셈블리와 함께 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-163">After you update a satellite assembly, increment its version number and ship it with a publisher policy assembly.</span></span> <span data-ttu-id="f4d2c-164">게시자 정책 어셈블리에서 새 위성 어셈블리가 이전 버전과 호환됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-164">In the publisher policy assembly, specify that your new satellite assembly is backward-compatible with its previous version.</span></span> <span data-ttu-id="f4d2c-165">리소스 관리자는 <xref:System.Resources.SatelliteContractVersionAttribute> 특성을 사용하여 위성 어셈블리의 버전을 확인하지만, 어셈블리 로더는 게시자 정책에서 지정한 위성 어셈블리 버전에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-165">The resource manager will use the <xref:System.Resources.SatelliteContractVersionAttribute> attribute to determine the version of the satellite assembly, but the assembly loader will bind to the satellite assembly version specified by the publisher policy.</span></span> <span data-ttu-id="f4d2c-166">게시자 정책 어셈블리에 대한 자세한 내용은 [게시자 정책 파일 만들기](../configure-apps/how-to-create-a-publisher-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-166">For more information about publisher policy assemblies, see [Creating a Publisher Policy File](../configure-apps/how-to-create-a-publisher-policy.md).</span></span>  
  
 <span data-ttu-id="f4d2c-167">전체 어셈블리 버전 관리 지원을 사용하려면 강력한 이름의 어셈블리는 [전역 어셈블리 캐시](../app-domains/gac.md) 에 배포하고, 강력한 이름을 가지고 있지 않은 어셈블리는 애플리케이션 디렉터리에 배포하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-167">To enable full assembly versioning support, we recommend that you deploy strong-named assemblies in the [global assembly cache](../app-domains/gac.md) and deploy assemblies that don't have strong names in the application directory.</span></span> <span data-ttu-id="f4d2c-168">애플리케이션 디렉터리에 강력한 이름의 어셈블리를 배포하려는 경우 어셈블리를 업데이트할 때 위성 어셈블리의 버전 번호를 높일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-168">If you want to deploy strong-named assemblies in the application directory, you will not be able to increment a satellite assembly's version number when you update the assembly.</span></span> <span data-ttu-id="f4d2c-169">대신, 기존 코드를 업데이트된 코드로 바꾸고 동일한 버전 번호를 유지 관리하는 내부 업데이트를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-169">Instead, you must perform an in-place update where you replace the existing code with the updated code and maintain the same version number.</span></span> <span data-ttu-id="f4d2c-170">예를 들어, 위성 어셈블리의 버전 1.0.0.0을 완전히 지정된 어셈블리 이름 "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a"로 업데이트하려는 경우, 완전히 지정된 동일한 어셈블리 이름 "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a"로 컴파일된 업데이트된 myApp.resources.dll로 이를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-170">For example, if you want to update version 1.0.0.0 of a satellite assembly with the fully specified assembly name "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a", overwrite it with the updated myApp.resources.dll that has been compiled with the same, fully specified assembly name "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a".</span></span> <span data-ttu-id="f4d2c-171">위성 어셈블리 파일에서 내부 업데이트를 사용하면 앱이 위성 어셈블리의 버전을 정확히 확인하기가 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-171">Note that using in-place updates on satellite assembly files makes it difficult for an app to accurately determine the version of a satellite assembly.</span></span>  
  
 <span data-ttu-id="f4d2c-172">어셈블리 버전 관리에 대한 자세한 내용은 [어셈블리 버전 관리](../../standard/assembly/versioning.md) 및 [런타임에서 어셈블리를 찾는 방법](../deployment/how-the-runtime-locates-assemblies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-172">For more information about assembly versioning, see [Assembly Versioning](../../standard/assembly/versioning.md) and [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
<a name="from_file"></a>

## <a name="retrieving-resources-from-resources-files"></a><span data-ttu-id="f4d2c-173">.resources 파일에서 리소스 검색</span><span class="sxs-lookup"><span data-stu-id="f4d2c-173">Retrieving Resources from .resources Files</span></span>  

 <span data-ttu-id="f4d2c-174">위성 어셈블리에서 리소스를 배포하지 않더라도 <xref:System.Resources.ResourceManager> 개체를 사용하여 .resources 파일에서 직접 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-174">If you choose not to deploy resources in satellite assemblies, you can still use a <xref:System.Resources.ResourceManager> object to access resources from .resources files directly.</span></span> <span data-ttu-id="f4d2c-175">이렇게 하려면 .resources 파일을 올바르게 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-175">To do this, you must deploy the .resources files correctly.</span></span> <span data-ttu-id="f4d2c-176">그런 다음 <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> 메서드를 사용하여 <xref:System.Resources.ResourceManager> 개체를 인스턴스화하고 독립형 .resources 파일을 포함하는 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-176">Then you use the <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> method to instantiate a <xref:System.Resources.ResourceManager> object and specify the directory that contains the standalone .resources files.</span></span>  
  
### <a name="deploying-resources-files"></a><span data-ttu-id="f4d2c-177">.resources 파일 배포</span><span class="sxs-lookup"><span data-stu-id="f4d2c-177">Deploying .resources Files</span></span>  

 <span data-ttu-id="f4d2c-178">애플리케이션 어셈블리 및 위성 어셈블리에 .resources 파일을 포함하는 경우, 각 위성 어셈블리는 같은 파일 이름을 갖지만 위성 어셈블리의 문화권을 반영하는 하위 디렉터리에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-178">When you embed .resources files in an application assembly and satellite assemblies, each satellite assembly has the same file name, but is placed in a subdirectory that reflects the satellite assembly's culture.</span></span> <span data-ttu-id="f4d2c-179">반면, .resources 파일에서 직접 리소스에 액세스할 경우에는 일반적으로 애플리케이션 디렉터리의 하위 디렉터리인 단일 디렉터리에 모든 .resources 파일을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-179">In contrast, when you access resources from .resources files directly, you can place all the .resources files in a single directory, usually a subdirectory of the application directory.</span></span> <span data-ttu-id="f4d2c-180">앱의 기본 .resources 파일의 이름은 문화권에 대한 암시 없이 루트 이름으로만 구성됩니다(예: strings.resources).</span><span class="sxs-lookup"><span data-stu-id="f4d2c-180">The name of the app's default .resources file consists of a root name only, with no indication of its culture (for example, strings.resources).</span></span> <span data-ttu-id="f4d2c-181">지역화된 각 문화권에 대한 리소스는 이름이 루트 이름과 문화권(예: strings.ja.resources 또는 strings.de-DE.resources)으로 구성된 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-181">The resources for each localized culture are stored in a file whose name consists of the root name followed by the culture (for example, strings.ja.resources or strings.de-DE.resources).</span></span>

 <span data-ttu-id="f4d2c-182">다음 그림은 리소스 파일을 디렉터리 구조에서 어디에 배치해야 하는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-182">The following illustration shows where resource files should be located in the directory structure.</span></span> <span data-ttu-id="f4d2c-183">또한 .resource 파일에 대한 명명 규칙을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-183">It also gives the naming conventions for .resource files.</span></span>  

 ![애플리케이션의 주 디렉터리를 보여주는 그림.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a><span data-ttu-id="f4d2c-185">리소스 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="f4d2c-185">Using the Resource Manager</span></span>  

 <span data-ttu-id="f4d2c-186">리소스를 만들어서 적절한 디렉터리에 배치했으면, <xref:System.Resources.ResourceManager> 메서드를 호출하여 리소스를 사용할 수 있도록 <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-186">After you have created your resources and placed them in the appropriate directory, you create a <xref:System.Resources.ResourceManager> object to use the resources by calling the <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> method.</span></span> <span data-ttu-id="f4d2c-187">첫 번째 매개 변수는 앱의 기본 .resources 파일의 루트 이름을 지정합니다(이전 섹션의 예제에서는 "strings").</span><span class="sxs-lookup"><span data-stu-id="f4d2c-187">The first parameter specifies the root name of the app's default .resources file (this would be "strings" for the example in the previous section).</span></span> <span data-ttu-id="f4d2c-188">두 번째 매개 변수는 리소스의 위치를 지정합니다(이전 예제에서는 "Resources").</span><span class="sxs-lookup"><span data-stu-id="f4d2c-188">The second parameter specifies the location of the resources ("Resources" for the previous example).</span></span> <span data-ttu-id="f4d2c-189">세 번째 매개 변수는 사용할 <xref:System.Resources.ResourceSet> 구현을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-189">The third parameter specifies the <xref:System.Resources.ResourceSet> implementation to use.</span></span> <span data-ttu-id="f4d2c-190">세 번째 매개 변수가 `null`인 경우 기본 런타임 <xref:System.Resources.ResourceSet> 가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-190">If the third parameter is `null`, the default runtime <xref:System.Resources.ResourceSet> is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4d2c-191">독립 실행형 .resources 파일을 사용하여 ASP.NET 앱을 배포해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-191">Do not deploy ASP.NET apps using standalone .resources files.</span></span> <span data-ttu-id="f4d2c-192">그렇게 할 경우 잠금 문제가 발생할 수 있으며 XCOPY 배포가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-192">This can cause locking issues and breaks XCOPY deployment.</span></span> <span data-ttu-id="f4d2c-193">ASP.NET 리소스를 위성 어셈블리에 배포하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-193">We recommend that you deploy ASP.NET resources in satellite assemblies.</span></span> <span data-ttu-id="f4d2c-194">자세한 내용은 [ASP.NET Web Page Resources Overview](/previous-versions/aspnet/ms227427(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-194">For more information, see [ASP.NET Web Page Resources Overview](/previous-versions/aspnet/ms227427(v=vs.100)).</span></span>  
  
 <span data-ttu-id="f4d2c-195"><xref:System.Resources.ResourceManager> 개체를 인스턴스화한 후에는 앞서 설명한 대로 <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>및 <xref:System.Resources.ResourceManager.GetStream%2A> 메서드를 사용하여 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-195">After you instantiate the <xref:System.Resources.ResourceManager> object, you use the <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, and <xref:System.Resources.ResourceManager.GetStream%2A> methods as discussed earlier to retrieve the resources.</span></span> <span data-ttu-id="f4d2c-196">그러나 .resources 파일에서 직접 리소스를 검색하는 것은 어셈블리에서 포함된 리소스를 검색하는 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-196">However, the retrieval of resources directly from .resources files differs from the retrieval of embedded resources from assemblies.</span></span> <span data-ttu-id="f4d2c-197">.resources 파일에서 리소스를 검색할 경우 <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>및 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 메서드는 항상 현재 문화권과 관계없이 기본 문화권의 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-197">When you retrieve resources from .resources files, the <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, and <xref:System.Resources.ResourceManager.GetStream%28System.String%29> methods always retrieve the default culture's resources regardless of the current culture.</span></span> <span data-ttu-id="f4d2c-198">앱의 현재 문화권 또는 특정 문화권의 리소스를 검색하려면 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>또는 <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> 메서드를 호출하고 리소스를 검색할 문화권을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-198">To retrieve the resources of the either the app's current culture or a specific culture, you must call the <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, or <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> method and specify the culture whose resources are to be retrieved.</span></span> <span data-ttu-id="f4d2c-199">현재 문화권의 리소스를 검색하려면 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 속성의 값을 `culture` 인수로서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-199">To retrieve the resources of the current culture, specify the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> property as the `culture` argument.</span></span> <span data-ttu-id="f4d2c-200">리소스 관리자는 `culture`의 리소스를 검색할 수 없는 경우 표준 리소스 대체 규칙을 사용하여 적절한 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-200">If the resource manager cannot retrieve the resources of `culture`, it uses the standard resource fallback rules to retrieve the appropriate resources.</span></span>  
  
### <a name="an-example"></a><span data-ttu-id="f4d2c-201">예제</span><span class="sxs-lookup"><span data-stu-id="f4d2c-201">An Example</span></span>  

 <span data-ttu-id="f4d2c-202">다음 예제에서는 리소스 관리자가 .resources 파일에서 직접 리소스를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-202">The following example illustrates how the resource manager retrieves resources directly from .resources files.</span></span> <span data-ttu-id="f4d2c-203">예제는 영어(미국), 프랑스어(프랑스) 및 러시아어(러시아) 문화권에 대한 세 가지 텍스트 기반 리소스 파일로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-203">The example consists of three text-based resource files for the English (United States), French (France), and Russian (Russia) cultures.</span></span> <span data-ttu-id="f4d2c-204">영어(미국)가 예제의 기본 문화권입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-204">English (United States) is the example's default culture.</span></span> <span data-ttu-id="f4d2c-205">해당 리소스는 Strings.txt라는 다음 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-205">Its resources are stored in the following file named Strings.txt:</span></span>  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 <span data-ttu-id="f4d2c-206">프랑스어(프랑스) 문화권에 대한 리소스는 Strings.fr-FR.txt라는 다음 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-206">Resources for the French (France) culture are stored in the following file, which is named Strings.fr-FR.txt:</span></span>  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 <span data-ttu-id="f4d2c-207">러시아어(러시아) 문화권에 대한 리소스는 Strings.ru-RU.txt라는 다음 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-207">Resources for the Russian (Russia) culture are stored in the following file, which is named Strings.ru-RU.txt:</span></span>  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 <span data-ttu-id="f4d2c-208">다음은 예제의 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-208">The following is the source code for the example.</span></span> <span data-ttu-id="f4d2c-209">이 예제에서는 영어(미국), 영어(캐나다), 프랑스어(프랑스) 및 러시아어(러시아) 문화권에 대한 <xref:System.Globalization.CultureInfo> 개체를 인스턴스화하고 각각을 현재 문화권으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-209">The example instantiates <xref:System.Globalization.CultureInfo> objects for the English (United States), English (Canada), French (France), and Russian (Russia) cultures, and makes each the current culture.</span></span> <span data-ttu-id="f4d2c-210">그런 다음 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> 메서드는 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 속성의 값을 `culture` 인수로 제공하여 적절한 문화권 관련 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-210">The <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> method then supplies the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> property as the `culture` argument to retrieve the appropriate culture-specific resources.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 <span data-ttu-id="f4d2c-211">다음 배치 파일을 실행하여 예제의 C# 버전을 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-211">You can compile the C# version of the example by running the following batch file.</span></span> <span data-ttu-id="f4d2c-212">Visual Basic을 사용하는 경우 `csc`를 `vbc`로 바꾸고 `.cs` 확장을 `.vb`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f4d2c-212">If you're using Visual Basic, replace `csc` with `vbc`, and replace the `.cs` extension with `.vb`.</span></span>  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4d2c-213">참조</span><span class="sxs-lookup"><span data-stu-id="f4d2c-213">See also</span></span>

- <xref:System.Resources.ResourceManager>
- [<span data-ttu-id="f4d2c-214">데스크톱 앱의 리소스</span><span class="sxs-lookup"><span data-stu-id="f4d2c-214">Resources in Desktop Apps</span></span>](index.md)
- [<span data-ttu-id="f4d2c-215">리소스 패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="f4d2c-215">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="f4d2c-216">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="f4d2c-216">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="f4d2c-217">[Windows 스토어 앱에서 리소스 만들기 및 검색](/previous-versions/windows/apps/hh694557(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="f4d2c-217">[Creating and retrieving resources in Windows Store apps](/previous-versions/windows/apps/hh694557(v=vs.140))</span></span>
