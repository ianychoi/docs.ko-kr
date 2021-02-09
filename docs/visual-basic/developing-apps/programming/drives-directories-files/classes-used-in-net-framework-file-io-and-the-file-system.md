---
description: '자세한 정보: .NET Framework 파일 I/O 및 파일 시스템에 사용되는 클래스(Visual Basic)'
title: .NET Framework 파일 I/O 및 파일 시스템에 사용되는 클래스
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: a8cbe476044df92fcdbdd0421b91f3c7c098e063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666331"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="354e9-103">.NET Framework 파일 I/O 및 파일 시스템에 사용되는 클래스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354e9-103">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>

<span data-ttu-id="354e9-104">다음 표에는 .NET Framework 파일 I/O에 공통적으로 사용되고 파일 I/O 클래스로 범주화되는 클래스, 스트림을 만드는 데 사용되는 클래스 및 스트림을 읽고 스트림에 쓰는 데 사용되는 클래스가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-104">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
<span data-ttu-id="354e9-105">더 포괄적인 목록은 [클래스 라이브러리 개요](../../../../standard/class-library-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="354e9-105">For a more comprehensive listing, see [Class Library Overview](../../../../standard/class-library-overview.md).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="354e9-106">파일, 드라이브 및 디렉터리의 기본 I/O 클래스</span><span class="sxs-lookup"><span data-stu-id="354e9-106">Basic I/O Classes for Files, Drives, and Directories</span></span>  

 <span data-ttu-id="354e9-107">다음 표에서는 파일 I/O에 사용되는 기본 클래스를 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-107">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="354e9-108">인스턴스</span><span class="sxs-lookup"><span data-stu-id="354e9-108">Class</span></span>|<span data-ttu-id="354e9-109">Description</span><span class="sxs-lookup"><span data-stu-id="354e9-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|<span data-ttu-id="354e9-110">디렉터리와 하위 디렉터리를 통해 만들고, 이동하고, 열거하기 위한 정적 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-110">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|<span data-ttu-id="354e9-111">디렉터리와 하위 디렉터리를 통해 만들고, 이동하고, 열거하기 위한 인스턴스 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-111">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|<span data-ttu-id="354e9-112">드라이브를 통해 만들고, 이동하고, 열거하기 위한 인스턴스 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-112">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=nameWithType>|<span data-ttu-id="354e9-113">파일 만들기, 복사, 삭제, 이동 및 열기를 위한 정적 메서드를 제공하고 `FileStream`만들기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-113">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|<span data-ttu-id="354e9-114">파일에 대한 읽기, 쓰기 또는 읽기/쓰기 액세스 권한에 대한 상수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-114">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|<span data-ttu-id="354e9-115">`Archive`, `Hidden` 및 `ReadOnly`와 같은 파일 및 디렉터리에 대한 특성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-115">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|<span data-ttu-id="354e9-116">파일 만들기, 복사, 삭제, 이동 및 열기를 위한 정적 메서드를 제공하고 `FileStream`만들기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-116">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|<span data-ttu-id="354e9-117">파일을 여는 방식을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-117">Controls how a file is opened.</span></span> <span data-ttu-id="354e9-118">이 매개 변수는 대부분의 `FileStream` 및 `IsolatedStorageFileStream`에 대한 생성자와 <xref:System.IO.File> 및 <xref:System.IO.FileInfo>의 `Open` 메서드에 대한 생성자에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-118">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|<span data-ttu-id="354e9-119">다른 파일 스트림이 같은 파일에 대해 가질 수 있는 액세스 형식을 제어하기 위한 상수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-119">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=nameWithType>|<span data-ttu-id="354e9-120">디렉터리 문자열을 처리하기 위한 메서드와 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-120">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|<span data-ttu-id="354e9-121"><xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> 및 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 권한을 정의하여 파일 및 폴더 액세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-121">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="354e9-122">스트림을 만드는 데 사용되는 클래스</span><span class="sxs-lookup"><span data-stu-id="354e9-122">Classes Used to Create Streams</span></span>  

 <span data-ttu-id="354e9-123">다음 표에서는 스트림을 만드는 데 사용되는 기본 클래스를 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-123">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="354e9-124">인스턴스</span><span class="sxs-lookup"><span data-stu-id="354e9-124">Class</span></span>|<span data-ttu-id="354e9-125">Description</span><span class="sxs-lookup"><span data-stu-id="354e9-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|<span data-ttu-id="354e9-126">다른 스트림에서 작업을 읽고 쓰기 위한 버퍼링 레이어를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-126">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<span data-ttu-id="354e9-127"><xref:System.IO.FileStream.Seek%2A> 메서드를 통해 임의 파일 액세스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-127">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="354e9-128"><xref:System.IO.FileStream>은 기본적으로 파일을 동기적으로 열지만 비동기 작업도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-128"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|<span data-ttu-id="354e9-129">백업 저장소가 파일이 아니라 메모리인 스트림을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-129">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|<span data-ttu-id="354e9-130">네트워크 액세스를 위한 데이터의 기본 스트림을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-130">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|<span data-ttu-id="354e9-131">데이터 스트림을 암호화 변환에 연결하는 스트림을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-131">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="354e9-132">스트림에서 읽고 스트림에 쓰는 데 사용되는 클래스</span><span class="sxs-lookup"><span data-stu-id="354e9-132">Classes Used to Read from and Write to Streams</span></span>  

 <span data-ttu-id="354e9-133">다음 표에는 스트림을 통해 파일에서 읽고 파일에 쓰는 데 사용되는 특정 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-133">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="354e9-134">**클래스**</span><span class="sxs-lookup"><span data-stu-id="354e9-134">**Class**</span></span>|<span data-ttu-id="354e9-135">**설명**</span><span class="sxs-lookup"><span data-stu-id="354e9-135">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|<span data-ttu-id="354e9-136"><xref:System.IO.FileStream>에서 인코딩된 문자열 및 기본 데이터 형식을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-136">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|<span data-ttu-id="354e9-137"><xref:System.IO.FileStream>에 인코딩된 문자열 및 기본 데이터 형식을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-137">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|<span data-ttu-id="354e9-138"><xref:System.IO.FileStream>에서 문자를 읽고 <xref:System.IO.StreamReader.CurrentEncoding%2A>을 사용하여 문자와 바이트 간을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-138">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="354e9-139"><xref:System.IO.StreamReader>에는 바이트 순서 표시 등의 <xref:System.IO.StreamReader.CurrentEncoding%2A> 관련 프리앰블 유무를 기준으로 하여 지정된 스트림의 올바른 <xref:System.IO.StreamReader.CurrentEncoding%2A> 확인을 시도하는 생성자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-139"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|<span data-ttu-id="354e9-140">`FileStream`에 문자를 쓰고 <xref:System.IO.StreamWriter.Encoding%2A>을 사용하여 문자와 바이트 간을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-140">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|<span data-ttu-id="354e9-141">`String`에서 문자를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-141">Reads characters from a `String`.</span></span> <span data-ttu-id="354e9-142">출력은 인코딩의 스트림 또는 `String` 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-142">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|<span data-ttu-id="354e9-143">`String`에 문자를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-143">Writes characters to a `String`.</span></span> <span data-ttu-id="354e9-144">출력은 인코딩의 스트림 또는 `String` 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="354e9-144">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="354e9-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="354e9-145">See also</span></span>

- [<span data-ttu-id="354e9-146">스트림 작성</span><span class="sxs-lookup"><span data-stu-id="354e9-146">Composing Streams</span></span>](../../../../standard/io/composing-streams.md)
- [<span data-ttu-id="354e9-147">파일 및 스트림 I/O</span><span class="sxs-lookup"><span data-stu-id="354e9-147">File and Stream I/O</span></span>](../../../../standard/io/index.md)
- [<span data-ttu-id="354e9-148">Asynchronous File I/O</span><span class="sxs-lookup"><span data-stu-id="354e9-148">Asynchronous File I/O</span></span>](../../../../standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="354e9-149">.NET Framework 파일 I/O 및 파일 시스템의 기본 사항(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354e9-149">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](basics-of-net-framework-file-io-and-the-file-system.md)
