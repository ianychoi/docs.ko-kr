---
title: WCF 개발자를 위한 Docker gRPC
description: ASP.NET Core gRPC 응용 프로그램에 대 한 Docker 이미지 만들기
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970091"
---
# <a name="create-docker-images"></a><span data-ttu-id="d6a34-103">Docker 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="d6a34-103">Create Docker images</span></span>

<span data-ttu-id="d6a34-104">이 섹션에서는 ASP.NET Core gRPC 응용 프로그램에 대 한 Docker 이미지 만들기, Docker, Kubernetes 또는 기타 컨테이너 환경에서 실행할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="d6a34-105">ASP.NET Core MVC 웹 앱 및 gRPC 서비스를 사용 하 여 사용 되는 샘플 응용 프로그램은 GitHub의 [dotnet-아키텍처/grpc-wcf-개발자](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 리포지토리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="d6a34-106">ASP.NET Core 응용 프로그램용 Microsoft 기본 이미지</span><span class="sxs-lookup"><span data-stu-id="d6a34-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="d6a34-107">Microsoft는 .NET 응용 프로그램 빌드 및 실행을 위한 다양 한 기본 이미지를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-107">Microsoft provides a range of base images for building and running .NET applications.</span></span> <span data-ttu-id="d6a34-108">ASP.NET Core 5.0 이미지를 만들려면 다음 두 가지 기본 이미지를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-108">To create an ASP.NET Core 5.0 image, you use two base images:</span></span>

- <span data-ttu-id="d6a34-109">응용 프로그램을 빌드 및 게시 하기 위한 SDK 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="d6a34-110">배포용 런타임 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="d6a34-111">이미지</span><span class="sxs-lookup"><span data-stu-id="d6a34-111">Image</span></span> | <span data-ttu-id="d6a34-112">설명</span><span class="sxs-lookup"><span data-stu-id="d6a34-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="d6a34-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="d6a34-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="d6a34-114">로 응용 프로그램을 빌드하는 데 사용 `docker build` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-114">For building applications with `docker build`.</span></span> <span data-ttu-id="d6a34-115">프로덕션에서는 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="d6a34-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="d6a34-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="d6a34-117">런타임 및 ASP.NET Core 종속성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="d6a34-118">프로덕션의 경우.</span><span class="sxs-lookup"><span data-stu-id="d6a34-118">For production.</span></span> |

<span data-ttu-id="d6a34-119">각 이미지에는 다른 Linux 배포판을 기반으로 하는 네 가지 변형이 있습니다 (태그로 구분).</span><span class="sxs-lookup"><span data-stu-id="d6a34-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="d6a34-120">이미지 태그</span><span class="sxs-lookup"><span data-stu-id="d6a34-120">Image tag(s)</span></span> | <span data-ttu-id="d6a34-121">Linux</span><span class="sxs-lookup"><span data-stu-id="d6a34-121">Linux</span></span> | <span data-ttu-id="d6a34-122">메모</span><span class="sxs-lookup"><span data-stu-id="d6a34-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="d6a34-123">5.0-buster, 5.0</span><span class="sxs-lookup"><span data-stu-id="d6a34-123">5.0-buster-slim, 5.0</span></span> | <span data-ttu-id="d6a34-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="d6a34-124">Debian 10</span></span> | <span data-ttu-id="d6a34-125">OS 변형이 지정 되지 않은 경우 기본 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="d6a34-126">5.0-알파인</span><span class="sxs-lookup"><span data-stu-id="d6a34-126">5.0-alpine</span></span> | <span data-ttu-id="d6a34-127">알파인 3.12</span><span class="sxs-lookup"><span data-stu-id="d6a34-127">Alpine 3.12</span></span> | <span data-ttu-id="d6a34-128">알파인 기본 이미지는 Debian 또는 Ubuntu 1 보다 훨씬 작습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="d6a34-129">5.0-초점면</span><span class="sxs-lookup"><span data-stu-id="d6a34-129">5.0-focal</span></span>| <span data-ttu-id="d6a34-130">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="d6a34-130">Ubuntu 20.04</span></span> | |

<span data-ttu-id="d6a34-131">알파인 기본 이미지는 Debian 및 Ubuntu 이미지의 200 MB와 비교 하 여 약 100입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="d6a34-132">일부 소프트웨어 패키지 또는 라이브러리는 알파인의 패키지 관리에서 사용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-132">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="d6a34-133">사용할 이미지를 잘 모르는 경우 기본 Debian를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-133">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6a34-134">빌드 및 런타임에 동일한 유형의 Linux를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-134">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="d6a34-135">하나의 변형에 빌드되고 게시 된 응용 프로그램은 다른 변형에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-135">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="d6a34-136">Docker 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="d6a34-136">Create a Docker image</span></span>

<span data-ttu-id="d6a34-137">Docker 이미지는 *Dockerfile* 에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-137">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="d6a34-138">이 *Dockerfile* 은 응용 프로그램을 빌드하고 응용 프로그램을 빌드하거나 실행 하는 데 필요한 모든 종속성을 설치 하는 데 필요한 모든 명령을 포함 하는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-138">This *Dockerfile* is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="d6a34-139">다음 예제에서는 ASP.NET Core 5.0 응용 프로그램에 대 한 가장 간단한 Dockerfile을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-139">The following example shows the simplest Dockerfile for an ASP.NET Core 5.0 application:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="d6a34-140">Dockerfile에는 두 부분이 있습니다. 첫 번째는 기본 이미지를 사용 하 여 `sdk` 응용 프로그램을 빌드 및 게시 하 고, 두 번째는 기본에서 런타임 이미지를 만듭니다. `aspnet`</span><span class="sxs-lookup"><span data-stu-id="d6a34-140">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="d6a34-141">이는 `sdk` 900 이미지가 런타임 이미지에 대 한 약 200 mb와 비교 했 고, 런타임에 대부분의 콘텐츠가 필요 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-141">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="d6a34-142">빌드 단계</span><span class="sxs-lookup"><span data-stu-id="d6a34-142">The build steps</span></span>

| <span data-ttu-id="d6a34-143">단계</span><span class="sxs-lookup"><span data-stu-id="d6a34-143">Step</span></span> | <span data-ttu-id="d6a34-144">설명</span><span class="sxs-lookup"><span data-stu-id="d6a34-144">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="d6a34-145">기본 이미지를 선언 하 고 별칭을 할당 합니다 `builder` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-145">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="d6a34-146">디렉터리를 만들고 `/src` 현재 작업 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-146">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="d6a34-147">호스트의 현재 디렉터리 아래에 있는 모든 항목을 이미지의 현재 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-147">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="d6a34-148">외부 패키지를 복원 합니다 (ASP.NET Core 3.0 프레임 워크는 SDK와 함께 사전 설치 됨).</span><span class="sxs-lookup"><span data-stu-id="d6a34-148">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="d6a34-149">릴리스 빌드를 빌드하고 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-149">Builds and publishes a Release build.</span></span> <span data-ttu-id="d6a34-150">`--runtime`플래그가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-150">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="d6a34-151">런타임 이미지 단계</span><span class="sxs-lookup"><span data-stu-id="d6a34-151">The runtime image steps</span></span>

| <span data-ttu-id="d6a34-152">단계</span><span class="sxs-lookup"><span data-stu-id="d6a34-152">Step</span></span> | <span data-ttu-id="d6a34-153">설명</span><span class="sxs-lookup"><span data-stu-id="d6a34-153">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="d6a34-154">새 기본 이미지를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-154">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="d6a34-155">디렉터리를 만들고 `/app` 현재 작업 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-155">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="d6a34-156">첫 번째 줄의 별칭을 사용 하 여 이전 이미지에서 게시 된 응용 프로그램을 복사 합니다 `builder` `FROM` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-156">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="d6a34-157">컨테이너가 시작 될 때 실행할 명령을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-157">Sets the command to run when the container starts.</span></span> <span data-ttu-id="d6a34-158">`dotnet`런타임 이미지의 명령은 DLL 파일만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-158">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="d6a34-159">Docker의 HTTPS</span><span class="sxs-lookup"><span data-stu-id="d6a34-159">HTTPS in Docker</span></span>

<span data-ttu-id="d6a34-160">Docker 용 Microsoft 기본 이미지 `ASPNETCORE_URLS` 환경 변수를로 설정 `http://+:80` 합니다. 즉, Kestrel은 해당 포트에서 HTTPS 없이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-160">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="d6a34-161">[자체 호스팅 gRPC 응용 프로그램](self-hosted.md)에 설명 된 대로 사용자 지정 인증서와 함께 HTTPS를 사용 하는 경우이 구성을 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-161">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this configuration.</span></span> <span data-ttu-id="d6a34-162">Dockerfile의 런타임 이미지 생성 부분에 환경 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-162">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="d6a34-163">. Dockerignore 파일</span><span class="sxs-lookup"><span data-stu-id="d6a34-163">The .dockerignore file</span></span>

<span data-ttu-id="d6a34-164">`.gitignore`특정 파일 및 디렉터리를 소스 제어에서 제외 하는 파일과 마찬가지로, `.dockerignore` 파일을 사용 하 여 빌드하는 동안 파일 및 디렉터리가 이미지에 복사 되지 않도록 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-164">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="d6a34-165">이 파일은 시간 복사를 저장할 뿐 아니라 PC의 디렉터리를 이미지에 복사 하 여 발생 하는 일부 오류를 방지할 수도 있습니다 `obj` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-165">This file not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="d6a34-166">최소한 파일에 및에 대 한 항목을 추가 해야 `bin` `obj` `.dockerignore` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-166">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="d6a34-167">이미지 빌드</span><span class="sxs-lookup"><span data-stu-id="d6a34-167">Build the image</span></span>

<span data-ttu-id="d6a34-168">`StockKube.sln`서로 다른 두 응용 프로그램 및를 포함 하는 솔루션의 경우 `StockData` `StockWeb` 기본 디렉터리에 각각 dockerfile을 배치 하는 것이 가장 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-168">For a `StockKube.sln` solution containing two different applications `StockData` and `StockWeb`, it's simplest to put the Dockerfile for each one of them in the base directory.</span></span> <span data-ttu-id="d6a34-169">이 경우 이미지를 빌드하려면 `docker build` 파일이 있는 디렉터리에서 다음 명령을 사용 `.sln` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-169">In that case, to build the image, use the following `docker build` command from the same directory where `.sln` file resides.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

<span data-ttu-id="d6a34-170">혼동 명명 된 `--tag` 플래그 (로 줄일 수 있음 `-t` )는 지정 된 경우 실제 태그를 포함 하 여 이미지의 전체 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-170">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="d6a34-171">끝에 있는는 `.` 빌드가 실행 되는 컨텍스트를 지정 합니다. Dockerfile의 명령에 대 한 현재 작업 디렉터리입니다 `COPY` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-171">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="d6a34-172">단일 솔루션 내에 여러 응용 프로그램이 있는 경우 각 응용 프로그램에 대 한 Dockerfile을 파일 옆에 있는 자체 폴더에 유지할 수 있습니다 `.csproj` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-172">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="d6a34-173">그래도 `docker build` 기본 디렉터리에서 명령을 실행 하 여 솔루션과 모든 프로젝트가 이미지에 복사 되었는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-173">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="d6a34-174">`--file`(또는) 플래그를 사용 하 여 현재 디렉터리 아래에 Dockerfile을 지정할 수 있습니다 `-f` .</span><span class="sxs-lookup"><span data-stu-id="d6a34-174">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="d6a34-175">컴퓨터의 컨테이너에서 이미지를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-175">Run the image in a container on your machine</span></span>

<span data-ttu-id="d6a34-176">로컬 Docker 인스턴스에서 이미지를 실행 하려면 `docker run` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-176">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

<span data-ttu-id="d6a34-177">`-ti`플래그는 현재 터미널을 컨테이너의 터미널에 연결 하 고 대화형 모드로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-177">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="d6a34-178">는 `-p 5000:80` 컨테이너의 포트 80를 localhost 네트워크 인터페이스의 포트 5000에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-178">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="d6a34-179">이미지를 레지스트리로 푸시</span><span class="sxs-lookup"><span data-stu-id="d6a34-179">Push the image to a registry</span></span>

<span data-ttu-id="d6a34-180">이미지가 작동 하는지 확인 한 후 Docker 레지스트리에 푸시하여 다른 시스템에서 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-180">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="d6a34-181">내부 네트워크에서 Docker 레지스트리를 프로 비전 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-181">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="d6a34-182">이 활동은 docker [의 자체 `registry` 이미지](https://docs.docker.com/registry/deploying/) 를 실행 하는 것 처럼 간단할 수 있습니다 (docker 레지스트리는 docker 컨테이너에서 실행 됨). 하지만 사용할 수 있는 여러 가지 포괄적인 솔루션도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-182">This activity can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="d6a34-183">외부 공유 및 클라우드 사용을 위해 [Azure Container Registry](/azure/container-registry/) 또는 [Docker 허브](https://docs.docker.com/docker-hub/repos/)와 같이 다양 한 관리 되는 레지스트리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-183">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="d6a34-184">Docker 허브에 푸시 하려면 이미지 이름 앞에 사용자 또는 조직 이름을 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-184">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

<span data-ttu-id="d6a34-185">개인 레지스트리에 푸시 하려면 이미지 이름 앞에 레지스트리 호스트 이름 및 조직 이름을 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-185">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

<span data-ttu-id="d6a34-186">이미지가 레지스트리에 있으면 개별 Docker 호스트 또는 Kubernetes와 같은 컨테이너 오케스트레이션 엔진에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6a34-186">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d6a34-187">[이전](self-hosted.md)
>[다음](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="d6a34-187">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
