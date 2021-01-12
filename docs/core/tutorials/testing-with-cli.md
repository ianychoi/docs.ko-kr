---
title: .NET CLI를 사용하여 프로젝트 구성 및 테스트
description: 이 자습서에서는 명령줄에서 .NET 프로젝트를 구성하고 테스트하는 방법을 설명합니다.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 263eaf15beac008de8bb353a385b8f3588a7fefc
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633639"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a><span data-ttu-id="2bfd3-103">.NET CLI를 사용하여 프로젝트 구성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="2bfd3-103">Organizing and testing projects with the .NET CLI</span></span>

<span data-ttu-id="2bfd3-104">이 자습서는 [자습서: Visual Studio Code를 사용하여 .NET으로 콘솔 애플리케이션 만들기](with-visual-studio-code.md)의 후속으로, 간단한 콘솔 앱을 만드는 것을 넘어 잘 구성된 고급 애플리케이션을 개발하도록 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-104">This tutorial follows [Tutorial: Create a console application with .NET using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="2bfd3-105">이 자습서에서는 폴더를 사용하여 코드를 구성하는 방법을 보여 준 후에 [xUnit](https://xunit.net/) 테스트 프레임워크를 사용하여 콘솔 애플리케이션을 확장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.net/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="2bfd3-106">폴더를 사용하여 코드 구성</span><span class="sxs-lookup"><span data-stu-id="2bfd3-106">Using folders to organize code</span></span>

<span data-ttu-id="2bfd3-107">콘솔 앱에 새 유형을 도입하려는 경우 유형이 포함된 파일을 앱에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="2bfd3-108">예를 들어 `AccountInformation` 및 `MonthlyReportRecords` 유형이 포함된 파일을 프로젝트에 추가하는 경우 프로젝트 파일 구조가 단순하며 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="2bfd3-109">그러나 이 방법은 프로젝트의 크기가 비교적 작은 경우에만 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="2bfd3-110">프로젝트에 20개의 유형을 추가하면 어떻게 될지 상상이 되시나요?</span><span class="sxs-lookup"><span data-stu-id="2bfd3-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="2bfd3-111">프로젝트의 루트 디렉터리에 너무 많은 파일이 있으면 분명히 프로젝트 탐색과 유지 관리가 쉽지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="2bfd3-112">프로젝트를 구성하려면 유형 파일을 보관할 새 폴더를 만들고 이름을 *Models* 로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="2bfd3-113">*Models* 폴더에 유형 파일을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="2bfd3-114">논리적으로 파일을 폴더로 그룹화하는 프로젝트는 탐색과 유지 관리가 용이합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="2bfd3-115">다음 섹션에서는 폴더 및 유닛 테스트를 사용하여 좀 더 복잡한 샘플을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="2bfd3-116">NewTypes Pets 샘플을 사용하여 구성 및 테스트</span><span class="sxs-lookup"><span data-stu-id="2bfd3-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2bfd3-117">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="2bfd3-117">Prerequisites</span></span>

* <span data-ttu-id="2bfd3-118">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) 이상 버전</span><span class="sxs-lookup"><span data-stu-id="2bfd3-118">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="2bfd3-119">샘플 빌드</span><span class="sxs-lookup"><span data-stu-id="2bfd3-119">Building the sample</span></span>

<span data-ttu-id="2bfd3-120">다음 단계를 위해 [NewTypes Pets 샘플](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild)을 사용할 수도 있고, 고유한 파일과 폴더를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-120">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="2bfd3-121">나중에 더 많은 유형을 추가할 수 있는 폴더 구조로 유형이 논리적으로 구성되며, 테스트도 나중에 더 많은 테스트를 추가할 수 있는 폴더에 논리적으로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-121">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="2bfd3-122">샘플에는 두 유형 `Dog` 및 `Cat`이 포함되어 있으며, 두 유형이 공용 인터페이스 `IPet`을 구현하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-122">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="2bfd3-123">`NewTypes` 프로젝트의 목표는 애완 동물 관련 유형을 *Pets* 폴더로 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-123">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="2bfd3-124">나중에 *WildAnimals* 등의 다른 유형 집합을 추가하면 *Pets* 폴더와 함께 *NewTypes* 폴더에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-124">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="2bfd3-125">*WildAnimals* 폴더에는 애완 동물이 아닌 동물 유형(예: `Squirrel` 및 `Rabbit`)이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-125">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="2bfd3-126">이렇게 하면 유형을 추가해도 프로젝트의 체계적인 구성이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-126">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="2bfd3-127">표시된 파일 내용으로 다음 폴더 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-127">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="2bfd3-128">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-128">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="2bfd3-129">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-129">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="2bfd3-130">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-130">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="2bfd3-131">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-131">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="2bfd3-132">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-132">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="2bfd3-133">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-133">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="2bfd3-134">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-134">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="2bfd3-135">연습(옵션): 이 프로젝트를 확장하여 `Bird` 등의 새로운 애완 동물 유형을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-135">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="2bfd3-136">새의 `TalkToOwner` 메서드를 통해 소유자에게 `Tweet!`을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-136">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="2bfd3-137">앱을 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-137">Run the app again.</span></span> <span data-ttu-id="2bfd3-138">출력에 `Tweet!`이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-138">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="2bfd3-139">샘플 테스트</span><span class="sxs-lookup"><span data-stu-id="2bfd3-139">Testing the sample</span></span>

<span data-ttu-id="2bfd3-140">`NewTypes` 프로젝트가 구현되었으며, 애완 동물 관련 유형을 폴더에 보관하여 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-140">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="2bfd3-141">다음으로, 테스트 프로젝트를 만들고 [xUnit](https://xunit.net/) 테스트 프레임워크를 사용하여 테스트 작성을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-141">Next, create your test project and start writing tests with the [xUnit](https://xunit.net/) test framework.</span></span> <span data-ttu-id="2bfd3-142">유닛 테스트를 사용하면 애완동물 유형의 동작을 자동으로 검사하여 제대로 작동하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-142">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="2bfd3-143">*src* 폴더를 다시 탐색하고 *test* 폴더를 만들며, 이 폴더 안에 *NewTypesTests* 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-143">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="2bfd3-144">*NewTypesTests* 폴더의 명령 프롬프트에서 `dotnet new xunit`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-144">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="2bfd3-145">이로 인해 *NewTypesTests.csproj* 및 *UnitTest1.cs* 라는 두 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-145">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="2bfd3-146">테스트 프로젝트는 현재 `NewTypes`의 형식을 테스트할 수 없으며, `NewTypes` 프로젝트에 대한 프로젝트 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-146">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="2bfd3-147">프로젝트 참조를 추가하려면 [`dotnet add reference`](../tools/dotnet-add-reference.md) 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-147">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="2bfd3-148">또는 *NewTypesTests.csproj* 파일에 `<ItemGroup>` 노드를 추가하여 수동으로 프로젝트 참조를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-148">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="2bfd3-149">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="2bfd3-149">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="2bfd3-150">*NewTypesTests.csproj* 파일에는 다음이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-150">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="2bfd3-151">.NET 테스트 인프라인 `Microsoft.NET.Test.Sdk`에 대한 패키지 참조</span><span class="sxs-lookup"><span data-stu-id="2bfd3-151">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="2bfd3-152">xUnit 테스트 프레임워크인 `xunit`에 대한 패키지 참조</span><span class="sxs-lookup"><span data-stu-id="2bfd3-152">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="2bfd3-153">테스트 실행기인 `xunit.runner.visualstudio`에 대한 패키지 참조</span><span class="sxs-lookup"><span data-stu-id="2bfd3-153">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="2bfd3-154">테스트할 코드인 `NewTypes`에 대한 프로젝트 참조</span><span class="sxs-lookup"><span data-stu-id="2bfd3-154">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="2bfd3-155">*UnitTest1.cs* 의 이름을 *PetTests.cs* 로 변경하고 파일의 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-155">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="2bfd3-156">연습(옵션): 소유자에 대한 `Tweet!`을 생성하는 `Bird` 유형을 이전에 추가한 경우 *PetTests.cs* 파일에 테스트 메서드 `BirdTalkToOwnerReturnsTweet`을 추가하여 `TalkToOwner` 메서드가 `Bird` 유형에 대해 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-156">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="2bfd3-157">`expected` 및 `actual` 값이 같다고 예상하는 경우에도 `Assert.NotEqual` 검사를 사용한 초기 어설션에서는 이러한 값이 *같지 않다* 고 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-157">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="2bfd3-158">테스트 논리를 검사하기 위해 항상 먼저 실패할 테스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-158">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="2bfd3-159">테스트가 실패했음을 확인한 후 테스트를 통과할 수 있도록 어설션을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-159">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="2bfd3-160">전체 프로젝트 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-160">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="2bfd3-161">*test/NewTypesTests* 디렉터리에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="2bfd3-162">[`dotnet test`](../tools/dotnet-test.md) 명령을 사용하여 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="2bfd3-163">이 명령은 프로젝트 파일에 지정된 Test Runner를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-163">This command starts the test runner specified in the project file.</span></span>

<span data-ttu-id="2bfd3-164">예상대로 테스트에 실패하고, 콘솔에 다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-164">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="2bfd3-165">테스트 어설션을 `Assert.NotEqual`에서 `Assert.Equal`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="2bfd3-166">`dotnet test` 명령을 사용하여 테스트를 다시 실행하면 다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="2bfd3-167">테스트를 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-167">Testing passes.</span></span> <span data-ttu-id="2bfd3-168">애완 동물 유형의 메서드가 소유자에게 설명할 때 올바른 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="2bfd3-169">xUnit을 사용하여 프로젝트를 구성 및 테스트하는 기술을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="2bfd3-170">이러한 기술을 활용하여 사용자 고유의 프로젝트에 적용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="2bfd3-171">*즐거운 코딩을 경험하시기 바랍니다!*</span><span class="sxs-lookup"><span data-stu-id="2bfd3-171">*Happy coding!*</span></span>
