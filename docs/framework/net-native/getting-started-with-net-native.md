---
description: '자세히 알아보기: .NET 네이티브 시작'
title: .NET 네이티브 시작
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 6079e21764ebc39515eb9b9f217057d916da8942
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747805"
---
# <a name="getting-started-with-net-native"></a><span data-ttu-id="0f4b6-103">.NET 네이티브 시작</span><span class="sxs-lookup"><span data-stu-id="0f4b6-103">Getting Started with .NET Native</span></span>

<span data-ttu-id="0f4b6-104">새로운 Windows 10용 Windows 앱을 작성하든지 기존 Windows 스토어 앱을 마이그레이션하든지 상관없이 동일한 절차 집합을 따르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-104">Whether you are writing a new Windows app for Windows 10 or you are migrating an existing Windows Store app, you can follow the same set of procedures.</span></span> <span data-ttu-id="0f4b6-105">.NET 네이티브 앱을 만들려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-105">To create a .NET Native app, follow these steps:</span></span>

1. <span data-ttu-id="0f4b6-106">[Windows 10을 대상으로 하는 UWP(유니버설 Windows 플랫폼) 앱을 개발하고](#Step1)앱의 디버그 빌드를 테스트하여 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-106">[Develop a Universal Windows Platform (UWP) app that targets Windows 10](#Step1), and test the debug builds of your app to ensure that it works properly.</span></span>

2. <span data-ttu-id="0f4b6-107">[추가 리플렉션 및 serialization 사용을 처리합니다](#Step2).</span><span class="sxs-lookup"><span data-stu-id="0f4b6-107">[Handle additional reflection and serialization usage](#Step2).</span></span>

3. <span data-ttu-id="0f4b6-108">[앱의 릴리스 빌드를 배포하고 테스트합니다](#Step3).</span><span class="sxs-lookup"><span data-stu-id="0f4b6-108">[Deploy and test the release builds of your app](#Step3).</span></span>

4. <span data-ttu-id="0f4b6-109">[누락된 메타데이터 문제를 수동으로 해결](#Step4)하고 [3단계](#Step3)를 반복하여 모든 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-109">[Manually resolve missing metadata](#Step4), and repeat [step 3](#Step3) until all issues are resolved.</span></span>

> [!NOTE]
> <span data-ttu-id="0f4b6-110">기존 Windows 스토어 앱을 .NET 네이티브로 마이그레이션하려는 경우 [Windows 스토어 앱을 .NET 네이티브로 마이그레이션](migrating-your-windows-store-app-to-net-native.md)을 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-110">If you are migrating an existing Windows Store app to .NET Native, be sure to review [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a><span data-ttu-id="0f4b6-111">1단계: UWP 앱의 디버그 빌드 개발 및 테스트</span><span class="sxs-lookup"><span data-stu-id="0f4b6-111">Step 1: Develop and test debug builds of your UWP app</span></span>

<span data-ttu-id="0f4b6-112">새 앱을 개발하든지 기존 앱을 마이그레이션하든지 상관없이 모든 Windows 앱에 동일한 프로세스를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-112">Whether you are developing a new app or migrating an existing one, you follow the same process as for any Windows app.</span></span>

1. <span data-ttu-id="0f4b6-113">Visual C# 또는 Visual Basic용 유니버설 Windows 앱 템플릿을 사용하여 Visual Studio에서 새 UWP 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-113">Create a new UWP project in Visual Studio by using the Universal Windows app template for Visual C# or Visual Basic.</span></span> <span data-ttu-id="0f4b6-114">기본적으로 모든 UWP 애플리케이션은 CoreCLR을 대상으로 하며 해당 릴리스 빌드는 .NET 네이티브 도구 체인을 사용하여 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-114">By default, all UWP applications target the CoreCLR and their release builds are compiled by using the .NET Native tool chain.</span></span>

2. <span data-ttu-id="0f4b6-115">.NET 네이티브 도구 체인을 사용하는 UWP 앱 프로젝트 컴파일과 도구 체인이 없는 프로젝트 컴파일 간에 알려진 호환성 문제가 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-115">Note that there are some known compatibility issues between compiling UWP app projects with the .NET Native tool chain and without it.</span></span> <span data-ttu-id="0f4b6-116">자세한 내용은 [마이그레이션 가이드](migrating-your-windows-store-app-to-net-native.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-116">Refer to the [migration guide](migrating-your-windows-store-app-to-net-native.md) for more information.</span></span>

<span data-ttu-id="0f4b6-117">이제 로컬 시스템이 나 시뮬레이터에서 실행 되는 .NET 네이티브 노출 영역에 대해 c # 또는 Visual Basic 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-117">You can now write C# or Visual Basic code against the .NET Native surface area that runs on the local system (or in the simulator).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f4b6-118">앱을 개발할 때는 코드에서 serialization 또는 리플렉션 사용을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-118">As you develop your app, note any use of serialization or reflection in your code.</span></span>

<span data-ttu-id="0f4b6-119">기본적으로 디버그 빌드는 신속한 F5 배포를 사용할 수 있도록 JIT 컴파일되지만, 릴리스 빌드는 .NET 네이티브 프리 컴파일 기술을 사용 하 여 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-119">By default, debug builds are JIT-compiled to enable rapid F5 deployment, while release builds are compiled by using the .NET Native pre-compilation technology.</span></span> <span data-ttu-id="0f4b6-120">이는 .NET 네이티브 도구 체인을 사용하여 프로젝트를 컴파일하기 전에 앱의 디버그 빌드를 빌드하고 테스트하여 정상적으로 작동되는지 확인해야 한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-120">This means you should build and test the debug builds of your app to ensure that they work normally before compiling them with the .NET Native tool chain.</span></span>

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a><span data-ttu-id="0f4b6-121">2단계: 추가 리플렉션 및 serialization 사용 처리</span><span class="sxs-lookup"><span data-stu-id="0f4b6-121">Step 2: Handle additional reflection and serialization usage</span></span>

<span data-ttu-id="0f4b6-122">프로젝트를 만들 때 런타임 지시문 파일인 Default.rd.xml이 해당 프로젝트에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-122">A runtime directives file, Default.rd.xml, is automatically added to your project when you create it.</span></span> <span data-ttu-id="0f4b6-123">C#으로 개발하는 경우 프로젝트의 **Properties** 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-123">If you develop in C#, it is found in your project's **Properties** folder.</span></span> <span data-ttu-id="0f4b6-124">Visual Basic으로 개발하는 경우 프로젝트의 **My Project** 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-124">If you develop in Visual Basic, it is found in your project's **My Project** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="0f4b6-125">런타임 지시문 파일이 필요한 이유에 대한 배경 정보를 제공하는 .NET 네이티브 컴파일 프로세스의 개요는 [.NET 네이티브 및 컴파일](net-native-and-compilation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-125">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>

<span data-ttu-id="0f4b6-126">런타임 지시문 파일은 앱에서 런타임에 필요한 메타데이터를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-126">The runtime directives file is used to define the metadata that your app needs at run time.</span></span> <span data-ttu-id="0f4b6-127">일부 경우에는 파일의 기본 버전이 적절할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-127">In some cases, the default version of the file may be adequate.</span></span> <span data-ttu-id="0f4b6-128">그러나 serialization 또는 리플렉션을 사용하는 일부 코드는 런타임 지시문 파일에서 추가 항목을 필요로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-128">However, some code that relies on serialization or reflection may require additional entries in the runtime directives file.</span></span>

<span data-ttu-id="0f4b6-129">**serialization**</span><span class="sxs-lookup"><span data-stu-id="0f4b6-129">**Serialization**</span></span>

<span data-ttu-id="0f4b6-130">직렬 변환기에는 두 가지 범주가 있으며 두 범주 모두 런타임 지시문 파일에 추가 항목이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-130">There are two categories of serializers, and both may require additional entries in the runtime directives file:</span></span>

- <span data-ttu-id="0f4b6-131">리플렉션을 기반으로 하지 않는 serializer.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-131">Non-reflection based serializers.</span></span> <span data-ttu-id="0f4b6-132"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, <xref:System.Xml.Serialization.XmlSerializer> 클래스와 같이 .NET Framework 클래스 라이브러리에 포함된 serializer는 리플렉션을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-132">The serializers found in the .NET Framework class library, such as the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes, do not rely on reflection.</span></span> <span data-ttu-id="0f4b6-133">그러나 직렬화 또는 역직렬화할 개체에 따라 코드를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-133">However, they do require that code be generated based on the object to be serialized or deserialized.</span></span>  <span data-ttu-id="0f4b6-134">자세한 내용은 [Serialization and Metadata](serialization-and-metadata.md)의 "Microsoft 직렬 변환기" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-134">For more information, see the "Microsoft Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

- <span data-ttu-id="0f4b6-135">타사 직렬 변환기.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-135">Third-party serializers.</span></span> <span data-ttu-id="0f4b6-136">Newtonsoft.json JSON serializer가 가장 일반적으로 사용 되는 타사 직렬화 라이브러리는 일반적으로 리플렉션 기반 이며 \* 개체 serialization 및 deserialization을 지원 하기 위해.rd.xml 파일의 항목이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-136">Third-party serialization libraries, the most common of which is the Newtonsoft JSON serializer, are generally reflection-based and require entries in the \*.rd.xml file to support object serialization and deserialization.</span></span> <span data-ttu-id="0f4b6-137">자세한 내용은 [Serialization and Metadata](serialization-and-metadata.md)의 "타사 직렬 변환기" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-137">For more information, see the "Third-Party Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

<span data-ttu-id="0f4b6-138">**리플렉션을 사용하는 메서드**</span><span class="sxs-lookup"><span data-stu-id="0f4b6-138">**Methods that rely on reflection**</span></span>

<span data-ttu-id="0f4b6-139">코드에서 리플렉션이 사용되는지가 분명하지 않은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-139">In some cases, the use of reflection in code is not obvious.</span></span> <span data-ttu-id="0f4b6-140">일부 공통 API 또는 프로그래밍 패턴은 리플렉션 API의 일부로는 간주되지 않지만 리플렉션을 사용해야 올바르게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-140">Some common APIs or programming patterns aren't considered part of the reflection API but rely on reflection to execute successfully.</span></span> <span data-ttu-id="0f4b6-141">여기에는 다음과 같은 형식 인스턴스화 및 메서드 생성 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-141">This includes the following type instantiation and method construction methods:</span></span>

- <span data-ttu-id="0f4b6-142"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 메서드</span><span class="sxs-lookup"><span data-stu-id="0f4b6-142">The <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method</span></span>

- <span data-ttu-id="0f4b6-143"><xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 및 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 메서드</span><span class="sxs-lookup"><span data-stu-id="0f4b6-143">The <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> and <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> methods</span></span>

- <span data-ttu-id="0f4b6-144"><xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 메서드</span><span class="sxs-lookup"><span data-stu-id="0f4b6-144">The <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0f4b6-145">자세한 내용은 [APIs That Rely on Reflection](apis-that-rely-on-reflection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-145">For more information, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0f4b6-146">런타임 지시문 파일에 사용되는 형식 이름은 정규화된 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-146">Type names used in runtime directives files must be fully qualified.</span></span> <span data-ttu-id="0f4b6-147">예를 들어 파일이 "String"이 아닌 "System.String"을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-147">For example, the file must specify "System.String" instead of "String".</span></span>

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a><span data-ttu-id="0f4b6-148">3단계: 앱의 릴리스 빌드 배포 및 테스트</span><span class="sxs-lookup"><span data-stu-id="0f4b6-148">Step 3: Deploy and test the release builds of your app</span></span>

<span data-ttu-id="0f4b6-149">런타임 지시문 파일을 업데이트한 후에는 앱의 릴리스 빌드를 다시 빌드하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-149">After you’ve updated the runtime directives file, you can rebuild and deploy release builds of your app.</span></span> <span data-ttu-id="0f4b6-150">.NET 네이티브 이진 파일은 프로젝트의 **속성** 대화 상자, **컴파일** 탭의 **빌드 출력 경로** 텍스트 상자에 지정 된 디렉터리의 ILC 하위 디렉터리에 배치 됩니다. 이 폴더에 없는 이진 파일은 .NET 네이티브으로 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-150">.NET Native binaries are placed in the ILC.out subdirectory of the directory specified in the **Build output path** text box of  the project's **Properties** dialog box, **Compile** tab. Binaries that aren't in this folder haven't been compiled with .NET Native.</span></span> <span data-ttu-id="0f4b6-151">각각의 대상 플랫폼에서 앱을 철저하게 테스트하고 오류 시나리오를 비롯한 모든 시나리오를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-151">Test your app thoroughly, and test all scenarios, including failure scenarios, on each of its target platforms.</span></span>

<span data-ttu-id="0f4b6-152">앱이 정상적으로 작동하지 않는 경우(특히 런타임에 [MissingMetadataException](missingmetadataexception-class-net-native.md) 또는 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 예외가 throw되는 경우) 다음 섹션인 [4단계: 수동으로 누락된 메타데이터 문제 해결](#Step4)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-152">If your app doesn’t work properly (particularly in cases where it throws [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions at run time), follow the instructions in the next section, [Step 4: Manually resolve missing metadata](#Step4).</span></span> <span data-ttu-id="0f4b6-153">첫째 예외를 사용하도록 설정하면 이러한 버그를 찾는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-153">Enabling first-chance exceptions may help you find these bugs.</span></span>

<span data-ttu-id="0f4b6-154">앱의 디버그 빌드를 테스트 하 고 디버그할 때 [MissingMetadataException](missingmetadataexception-class-net-native.md) 및 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 예외를 제거 하는 것을 확신 하는 경우 앱을 최적화 된 .NET 네이티브 앱으로 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-154">When you’ve tested and debugged the debug builds of your app and you’re confident that you’ve eliminated the [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions, you should test your app as an optimized .NET Native app.</span></span> <span data-ttu-id="0f4b6-155">이렇게 하려면 활성 프로젝트 구성을 **디버그** 에서 **릴리스** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-155">To do this, change your active project configuration from **Debug** to **Release**.</span></span>

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a><span data-ttu-id="0f4b6-156">4단계: 수동으로 누락된 메타데이터 문제 해결</span><span class="sxs-lookup"><span data-stu-id="0f4b6-156">Step 4: Manually resolve missing metadata</span></span>

<span data-ttu-id="0f4b6-157">데스크톱에서 발생 하지 않는 .NET 네이티브 발생 하는 가장 일반적인 오류는 런타임 [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)또는 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-157">The most common failure you'll encounter with .NET Native that you don't encounter on the desktop is a runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="0f4b6-158">경우에 따라서는 메타데이터가 없어서 예측할 수 없는 동작이 발생하거나 앱 자체에도 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-158">In some cases, the absence of metadata can manifest itself in unpredictable behavior or even in app failures.</span></span> <span data-ttu-id="0f4b6-159">이 섹션에서는 런타임 지시문 파일에 지시문을 추가하여 이러한 예외를 디버그 및 해결하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-159">This section discusses how you can debug and resolve these exceptions by adding directives to the runtime directives file.</span></span> <span data-ttu-id="0f4b6-160">런타임 지시문 형식에 대한 자세한 내용은 [런타임 지시문(rd.xml) 구성 파일 참조](runtime-directives-rd-xml-configuration-file-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-160">For information about the format of runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="0f4b6-161">런타임 지시문을 추가한 후에는 다시 [앱을 배포 및 테스트](#Step3) 하고 예외가 더 이상 발생하지 않을 때까지 새로 발생하는 [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)및  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 예외를 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-161">After you’ve added runtime directives, you should [deploy and test your app](#Step3) again and resolve any new [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions until you encounter no more exceptions.</span></span>

> [!TIP]
> <span data-ttu-id="0f4b6-162">코드 변경 시 앱을 복원하려면 런타임 지시문을 대략적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-162">Specify the runtime directives at a high level to enable your app to be resilient to code changes.</span></span>  <span data-ttu-id="0f4b6-163">런타임 지시문은 멤버 수준이 아닌 네임스페이스 및 형식 수준에 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-163">We recommend adding runtime directives at the namespace and type levels rather than the member level.</span></span> <span data-ttu-id="0f4b6-164">복원력을 높이면 이진 파일이 커지고 컴파일 시간이 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-164">Note that there may be a tradeoff between resiliency and larger binaries with longer compile times.</span></span>

<span data-ttu-id="0f4b6-165">누락된 메타데이터 예외를 해결할 때는 다음 문제를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-165">When addressing a missing metadata exception, consider these issues:</span></span>

- <span data-ttu-id="0f4b6-166">예외가 발생하기 전에 앱이 수행하려 했던 작업</span><span class="sxs-lookup"><span data-stu-id="0f4b6-166">What was the app trying to do before the exception?</span></span>

  - <span data-ttu-id="0f4b6-167">예를 들어 데이터 바인딩, 데이터 직렬화/역직렬화, 리플렉션 API 직접 사용 등을 시도했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-167">For example, was it data binding, serializing or deserializing data, or directly using the reflection API?</span></span>

- <span data-ttu-id="0f4b6-168">이 사례가 해당 형식에만 국한된 것인지 아니면 다른 형식에서도 같은 문제가 발생할 것으로 예상되는지 여부</span><span class="sxs-lookup"><span data-stu-id="0f4b6-168">Is this an isolated case, or do you believe you'll encounter the same issue for other types?</span></span>

  - <span data-ttu-id="0f4b6-169">앱 개체 모델에서 형식을 serialize할 때 [MissingMetadataException](missingmetadataexception-class-net-native.md) 예외가 throw된 경우를 예로 들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-169">For example, a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception is thrown when serializing a type in the app’s object model.</span></span>  <span data-ttu-id="0f4b6-170">이때 serialize할 다른 형식을 알고 있으면 해당 형식 또는 코드 구성 효율성에 따라 해당 형식의 포함 네임스페이스에 대해 런타임 지시문을 동시에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-170">If you know other types that will be serialized, you can add runtime directives for those types (or for their containing namespaces, depending on how well the code is organized) at the same time.</span></span>

- <span data-ttu-id="0f4b6-171">리플렉션을 사용하지 않도록 코드를 다시 작성할 수 있는지 여부</span><span class="sxs-lookup"><span data-stu-id="0f4b6-171">Can you rewrite the code so it doesn’t use reflection?</span></span>

  - <span data-ttu-id="0f4b6-172">필요한 형식을 알고 있는 경우 코드에 `dynamic` 키워드가 사용되는지 여부</span><span class="sxs-lookup"><span data-stu-id="0f4b6-172">For example, does the code use the `dynamic` keyword when you know what type to expect?</span></span>

  - <span data-ttu-id="0f4b6-173">보다 효율적인 대안을 사용할 수 있는 경우 코드가 리플렉션을 사용하는 메서드를 호출하는지 여부</span><span class="sxs-lookup"><span data-stu-id="0f4b6-173">Does the code call a method that depends on reflection when some better alternative is available?</span></span>

> [!NOTE]
> <span data-ttu-id="0f4b6-174">리플렉션의 차이로 인해 발생 하는 문제를 처리 하는 방법 및 데스크톱 응용 .NET 네이티브 프로그램에서 메타 데이터를 사용할 때 발생 하는 문제에 대 한 자세한 내용은 [리플렉션을 사용 하는 api](apis-that-rely-on-reflection.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-174">For additional information about handling problems that stem from differences in reflection and the availability of metadata in desktop apps and .NET Native, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

<span data-ttu-id="0f4b6-175">앱을 테스트할 때 발생하는 예외 및 기타 문제를 처리하는 몇 가지 구체적인 예제는 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0f4b6-175">For some specific examples of handling exceptions and other issues that occur when testing your app, see:</span></span>

- [<span data-ttu-id="0f4b6-176">예: 데이터를 바인딩하는 경우 예외 처리</span><span class="sxs-lookup"><span data-stu-id="0f4b6-176">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)

- [<span data-ttu-id="0f4b6-177">예: 동적 프로그래밍 문제 해결</span><span class="sxs-lookup"><span data-stu-id="0f4b6-177">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)

- [<span data-ttu-id="0f4b6-178">.NET 네이티브 앱의 런타임 예외</span><span class="sxs-lookup"><span data-stu-id="0f4b6-178">Runtime Exceptions in .NET Native Apps</span></span>](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a><span data-ttu-id="0f4b6-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f4b6-179">See also</span></span>

- [<span data-ttu-id="0f4b6-180">런타임 지시문(rd.xml) 구성 파일 참조</span><span class="sxs-lookup"><span data-stu-id="0f4b6-180">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="0f4b6-181">[.NET 네이티브 설치 및 구성](/previous-versions/dn600164(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="0f4b6-181">[.NET Native Setup and Configuration](/previous-versions/dn600164(v=vs.110))</span></span>
- [<span data-ttu-id="0f4b6-182">.NET 네이티브 및 컴파일</span><span class="sxs-lookup"><span data-stu-id="0f4b6-182">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
- [<span data-ttu-id="0f4b6-183">리플렉션 및 .NET 네이티브</span><span class="sxs-lookup"><span data-stu-id="0f4b6-183">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
- [<span data-ttu-id="0f4b6-184">리플렉션을 사용하는 API</span><span class="sxs-lookup"><span data-stu-id="0f4b6-184">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)
- [<span data-ttu-id="0f4b6-185">Serialization 및 메타데이터</span><span class="sxs-lookup"><span data-stu-id="0f4b6-185">Serialization and Metadata</span></span>](serialization-and-metadata.md)
- [<span data-ttu-id="0f4b6-186">Windows 스토어 앱을 .NET 네이티브로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="0f4b6-186">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
