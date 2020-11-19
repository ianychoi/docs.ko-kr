---
title: 파일 및 스트림 I/O - .NET
description: .NET에서 스토리지 매체로 데이터를 전송하거나 스토리지 매체로부터 데이터를 전송받는 파일 및 스트림 I/O의 기본 사항에 대해 알아보세요.
ms.date: 03/30/2017
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
ms.openlocfilehash: 4c6efc059423740f19460f24f12df81ac54f884a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825821"
---
# <a name="file-and-stream-io"></a><span data-ttu-id="1ba0d-103">파일 및 스트림 I/O</span><span class="sxs-lookup"><span data-stu-id="1ba0d-103">File and Stream I/O</span></span>

<span data-ttu-id="1ba0d-104">파일 및 스트림 I/O(입/출력)는 스토리지 매체로 데이터를 전송하거나 스토리지 매체로부터 데이터를 전송 받습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-104">File and stream I/O (input/output) refers to the transfer of data either to or from a storage medium.</span></span> <span data-ttu-id="1ba0d-105">.NET에서 `System.IO` 네임스페이스는 데이터 스트림과 파일에서 읽기 및 쓰기를 동기적 및 비동기적으로 사용하는 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-105">In .NET, the `System.IO` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files.</span></span> <span data-ttu-id="1ba0d-106">이러한 네임스페이스는 파일의 압축 및 압축 풀기 기능을 수행하는 형식 및 파이프 및 직렬 포트를 통한 통신을 가능하도록 하는 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-106">These namespaces also contain types that perform compression and decompression on files, and types that enable communication through pipes and serial ports.</span></span>

<span data-ttu-id="1ba0d-107">파일은 정돈되고 이름이 지정된 컬렉션의 바이트이며, 이 컬렉션에는 영구 스토리지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-107">A file is an ordered and named collection of bytes that has persistent storage.</span></span> <span data-ttu-id="1ba0d-108">사용자가 파일을 사용할 때, 디렉터리 경로, 디스크 스토리지 및 파일과 디렉터리 이름을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-108">When you work with files, you work with directory paths, disk storage, and file and directory names.</span></span> <span data-ttu-id="1ba0d-109">반대로, 스트림은 여러 가지 스토리지 매체 중 하나인 백업 저장소(예를 들어, 디스크 또는 메모리)에서 읽고 쓸 수 있는 바이트 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-109">In contrast, a stream is a sequence of bytes that you can use to read from and write to a backing store, which can be one of several storage mediums (for example, disks or memory).</span></span> <span data-ttu-id="1ba0d-110">디스크 외에 여러 백업 저장소가 존재하듯이, 파이프 스트림 외에 여러 종류의 스트림, 예를 들어 네트워크, 메모리, 파일 스트림도 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-110">Just as there are several backing stores other than disks, there are several kinds of streams other than file streams, such as network, memory, and pipe streams.</span></span>

## <a name="files-and-directories"></a><span data-ttu-id="1ba0d-111">파일 및 디렉터리</span><span class="sxs-lookup"><span data-stu-id="1ba0d-111">Files and directories</span></span>

<span data-ttu-id="1ba0d-112">사용자는 이 형식들을 <xref:System.IO?displayProperty=nameWithType> 네임스페이스에서 파일 및 디렉터리와 상호 작용하기 위해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-112">You can use the types in the <xref:System.IO?displayProperty=nameWithType> namespace to interact with files and directories.</span></span> <span data-ttu-id="1ba0d-113">예를 들어, 파일 및 디렉터리에 대한 속성을 가져오고 설정할 수 있고, 검색 조건에 따라 파일 및 디렉터리의 컬렉션을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-113">For example, you can get and set properties for files and directories, and retrieve collections of files and directories based on search criteria.</span></span>

<span data-ttu-id="1ba0d-114">.NET Core 1.1 및 .NET Framework 4.6.2 이상에서 지원되는 DOS 디바이스 구문을 비롯한 Windows 시스템에 대한 경로 명명 규칙 및 파일 경로를 표현하는 방법은 [Windows 시스템의 파일 경로 형식](file-path-formats.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-114">For path naming conventions and the ways to express a file path for Windows systems, including with the DOS device syntax supported in .NET Core 1.1 and later and .NET Framework 4.6.2 and later, see [File path formats on Windows systems](file-path-formats.md).</span></span>

<span data-ttu-id="1ba0d-115">다음은 몇 가지 흔히 사용되는 파일 및 디렉터리 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-115">Here are some commonly used file and directory classes:</span></span>

- <span data-ttu-id="1ba0d-116"><xref:System.IO.File> - 파일 만들기, 복사, 삭제, 이동 및 열기를 위한 정적 메서드를 제공하고 <xref:System.IO.FileStream> 개체 만들기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-116"><xref:System.IO.File> - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>

- <span data-ttu-id="1ba0d-117"><xref:System.IO.FileInfo> - 파일 만들기, 복사, 삭제, 이동 및 열기를 위한 인스턴스 메서드를 제공하고 <xref:System.IO.FileStream> 개체 만들기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-117"><xref:System.IO.FileInfo> - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>

- <span data-ttu-id="1ba0d-118"><xref:System.IO.Directory> - 디렉터리와 하위 디렉터리를 통해 만들고, 이동하고, 열거하기 위한 정적 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-118"><xref:System.IO.Directory> - provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>

- <span data-ttu-id="1ba0d-119"><xref:System.IO.DirectoryInfo> - 디렉터리와 하위 디렉터리를 통해 만들고, 이동하고, 열거하기 위한 인스턴스 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-119"><xref:System.IO.DirectoryInfo> - provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>

- <span data-ttu-id="1ba0d-120"><xref:System.IO.Path> - 플랫폼 간에 호환되는 방식으로 디렉터리 문자열을 처리하기 위한 메서드와 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-120"><xref:System.IO.Path> - provides methods and properties for processing directory strings in a cross-platform manner.</span></span>

<span data-ttu-id="1ba0d-121">파일 시스템 메서드를 호출할 때 항상 강력한 예외 처리를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-121">You should always provide robust exception handling when calling filesystem methods.</span></span> <span data-ttu-id="1ba0d-122">자세한 내용은 [I/O 오류 처리](handling-io-errors.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-122">For more information, see [Handling I/O errors](handling-io-errors.md).</span></span>

<span data-ttu-id="1ba0d-123">Visual Basic 사용자는 이러한 클래스를 사용하는 것 외에도, 파일 I/O에 대한 <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> 클래스에서 제공하는 메서드와 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-123">In addition to using these classes, Visual Basic users can use the methods and properties provided by the <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> class for file I/O.</span></span>

<span data-ttu-id="1ba0d-124">[방법: 디렉터리 복사](how-to-copy-directories.md), [방법: 디렉터리 목록 만들기](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100)) 및 [방법: 디렉터리 및 파일 열거](how-to-enumerate-directories-and-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-124">See [How to: Copy Directories](how-to-copy-directories.md), [How to: Create a Directory Listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100)), and [How to: Enumerate Directories and Files](how-to-enumerate-directories-and-files.md).</span></span>

## <a name="streams"></a><span data-ttu-id="1ba0d-125">스트림</span><span class="sxs-lookup"><span data-stu-id="1ba0d-125">Streams</span></span>

<span data-ttu-id="1ba0d-126">추상 기본 클래스 <xref:System.IO.Stream>은 바이트 읽기 및 쓰기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-126">The abstract base class <xref:System.IO.Stream> supports reading and writing bytes.</span></span> <span data-ttu-id="1ba0d-127">스트림을 나타내는 모든 클래스는 <xref:System.IO.Stream> 클래스로부터 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-127">All classes that represent streams inherit from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="1ba0d-128"><xref:System.IO.Stream> 클래스와 이 클래스에서 파생되는 클래스는 데이터 소스와 리포지토리의 일반 뷰를 제공하고, 이때 프로그래머는 운영 체제 및 내부 디바이스의 세부 사항에서 격리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-128">The <xref:System.IO.Stream> class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.</span></span>

<span data-ttu-id="1ba0d-129">스트림에는 다음의 세 가지 기본 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-129">Streams involve three fundamental operations:</span></span>

- <span data-ttu-id="1ba0d-130">읽기 - 스트림의 데이터를 바이트 배열과 같은 데이터 구조로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-130">Reading - transferring data from a stream into a data structure, such as an array of bytes.</span></span>

- <span data-ttu-id="1ba0d-131">쓰기 - 데이터 소스에서 스트림으로 데이터를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-131">Writing - transferring data to a stream from a data source.</span></span>

- <span data-ttu-id="1ba0d-132">검색 - 스트림 내에서 현재 위치를 쿼리하고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-132">Seeking - querying and modifying the current position within a stream.</span></span>

<span data-ttu-id="1ba0d-133">내부 데이터 소스 또는 리포지토리에 따라 스트림에서 이러한 기능 중 일부만 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-133">Depending on the underlying data source or repository, a stream might support only some of these capabilities.</span></span> <span data-ttu-id="1ba0d-134">예를 들어, <xref:System.IO.Pipes.PipeStream> 클래스는 검색을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-134">For example, the <xref:System.IO.Pipes.PipeStream> class does not support seeking.</span></span> <span data-ttu-id="1ba0d-135"><xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, <xref:System.IO.Stream.CanSeek%2A> 스트림 속성은 스트림이 지원하는 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-135">The <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, and <xref:System.IO.Stream.CanSeek%2A> properties of a stream specify the operations that the stream supports.</span></span>

<span data-ttu-id="1ba0d-136">다음은 몇 가지 자주 사용되는 스트림 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-136">Here are some commonly used stream classes:</span></span>

- <span data-ttu-id="1ba0d-137"><xref:System.IO.FileStream> – 파일을 읽고 쓰는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-137"><xref:System.IO.FileStream> – for reading and writing to a file.</span></span>

- <span data-ttu-id="1ba0d-138"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 격리된 스토리지의 파일을 읽고 파일에 기록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-138"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – for reading and writing to a file in isolated storage.</span></span>

- <span data-ttu-id="1ba0d-139"><xref:System.IO.MemoryStream> – 메모리를 백업 저장소로 읽고 여기에 기록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-139"><xref:System.IO.MemoryStream> – for reading and writing to memory as the backing store.</span></span>

- <span data-ttu-id="1ba0d-140"><xref:System.IO.BufferedStream> – 읽기 및 쓰기 작업의 성능을 향상시키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-140"><xref:System.IO.BufferedStream> – for improving performance of read and write operations.</span></span>

- <span data-ttu-id="1ba0d-141"><xref:System.Net.Sockets.NetworkStream> – 네트워크 소켓을 통한 읽기 및 쓰기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-141"><xref:System.Net.Sockets.NetworkStream> – for reading and writing over network sockets.</span></span>

- <span data-ttu-id="1ba0d-142"><xref:System.IO.Pipes.PipeStream> – 익명 및 명명된 파이프를 통한 읽기와 쓰기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-142"><xref:System.IO.Pipes.PipeStream> – for reading and writing over anonymous and named pipes.</span></span>

- <span data-ttu-id="1ba0d-143"><xref:System.Security.Cryptography.CryptoStream> – 데이터 스트림을 암호화 변형에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-143"><xref:System.Security.Cryptography.CryptoStream> – for linking data streams to cryptographic transformations.</span></span>

<span data-ttu-id="1ba0d-144">스트림의 비동기화 작업에 대한 예제는 [비동기 파일 I/O](asynchronous-file-i-o.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-144">For an example of working with streams asynchronously, see [Asynchronous File I/O](asynchronous-file-i-o.md).</span></span>

## <a name="readers-and-writers"></a><span data-ttu-id="1ba0d-145">판독기 및 작성기</span><span class="sxs-lookup"><span data-stu-id="1ba0d-145">Readers and writers</span></span>

<span data-ttu-id="1ba0d-146">또한 <xref:System.IO?displayProperty=nameWithType> 네임스페이스는 스트림으로부터 인코딩된 문자를 읽고 이를 스트림에 쓰기 위한 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-146">The <xref:System.IO?displayProperty=nameWithType> namespace also provides types for reading encoded characters from streams and writing them to streams.</span></span> <span data-ttu-id="1ba0d-147">일반적으로 스트림은 바이트 입력 및 출력용으로 디자인됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-147">Typically, streams are designed for byte input and output.</span></span> <span data-ttu-id="1ba0d-148">판독기 및 작성기 형식은 스트림 작업을 완료할 수 있도록 인코딩된 문자와 바이트의 변환을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-148">The reader and writer types handle the conversion of the encoded characters to and from bytes so the stream can complete the operation.</span></span> <span data-ttu-id="1ba0d-149">각 판독기 및 작성기 클래스는 스트림과 연결되어 있고, 이것은 클래스의 `BaseStream` 속성을 통해 검색될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-149">Each reader and writer class is associated with a stream, which can be retrieved through the class's `BaseStream` property.</span></span>

<span data-ttu-id="1ba0d-150">일부 자주 사용되는 판독기 및 작성기 클래스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-150">Here are some commonly used reader and writer classes:</span></span>

- <span data-ttu-id="1ba0d-151"><xref:System.IO.BinaryReader> 및 <xref:System.IO.BinaryWriter> – 기본 데이터 형식을 바이너리 값으로 읽고 쓰는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-151"><xref:System.IO.BinaryReader> and <xref:System.IO.BinaryWriter> – for reading and writing primitive data types as binary values.</span></span>

- <span data-ttu-id="1ba0d-152"><xref:System.IO.StreamReader> 및 <xref:System.IO.StreamWriter> – 인코딩 값을 사용하여 바이트에서 문자, 문자에서 바이트로 변환함으로써 문자를 읽고 쓰는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-152"><xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> – for reading and writing characters by using an encoding value to convert the characters to and from bytes.</span></span>

- <span data-ttu-id="1ba0d-153"><xref:System.IO.StringReader> 및 <xref:System.IO.StringWriter> – 문자열에서 문자를, 문자에서 문자열을 읽고 쓰는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-153"><xref:System.IO.StringReader> and <xref:System.IO.StringWriter> – for reading and writing characters to and from strings.</span></span>

- <span data-ttu-id="1ba0d-154"><xref:System.IO.TextReader> 및 <xref:System.IO.TextWriter> – 이진 데이터가 아닌 문자 및 문자열을 읽고 쓰는 다른 판독기와 작성기에 대한 추상 기본 클래스로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-154"><xref:System.IO.TextReader> and <xref:System.IO.TextWriter> – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.</span></span>

<span data-ttu-id="1ba0d-155">[방법: 파일에서 텍스트 읽기](how-to-read-text-from-a-file.md), [방법: 파일에 텍스트 쓰기](how-to-write-text-to-a-file.md), [방법: 문자열에서 문자 읽기](how-to-read-characters-from-a-string.md) 및 [방법: 문자열에 문자 쓰기](how-to-write-characters-to-a-string.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-155">See [How to: Read Text from a File](how-to-read-text-from-a-file.md), [How to: Write Text to a File](how-to-write-text-to-a-file.md), [How to: Read Characters from a String](how-to-read-characters-from-a-string.md), and [How to: Write Characters to a String](how-to-write-characters-to-a-string.md).</span></span>

## <a name="asynchronous-io-operations"></a><span data-ttu-id="1ba0d-156">비동기 I/O 작업</span><span class="sxs-lookup"><span data-stu-id="1ba0d-156">Asynchronous I/O operations</span></span>

<span data-ttu-id="1ba0d-157">많은 양의 데이터를 읽거나 쓸 때 리소스가 많이 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-157">Reading or writing a large amount of data can be resource-intensive.</span></span> <span data-ttu-id="1ba0d-158">이러한 작업은 애플리케이션 사용자에게 응답을 유지해야 하는 경우 비동기적으로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-158">You should perform these tasks asynchronously if your application needs to remain responsive to the user.</span></span> <span data-ttu-id="1ba0d-159">동기 I/O 작업에서 UI 스레드는 리소스 집약적인 작업이 완료될 때까지 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-159">With synchronous I/O operations, the UI thread is blocked until the resource-intensive operation has completed.</span></span>  <span data-ttu-id="1ba0d-160">Windows 8.x 스토어 앱을 개발할 때 비동기 I/O 작업을 사용하여 앱이 작동을 멈춘 것처럼 보이지 않게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-160">Use asynchronous I/O operations when developing Windows 8.x Store apps to prevent creating the impression that your app has stopped working.</span></span>

<span data-ttu-id="1ba0d-161">비동기 멤버의 이름에는 `Async`가 포함됩니다(예: <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> 및 <xref:System.IO.Stream.WriteAsync%2A> 메서드).</span><span class="sxs-lookup"><span data-stu-id="1ba0d-161">The asynchronous members contain `Async` in their names, such as the <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>,  <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> methods.</span></span> <span data-ttu-id="1ba0d-162">이러한 메서드는 `async` 및 `await` 키워드와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-162">You use these methods with the `async` and `await` keywords.</span></span>

<span data-ttu-id="1ba0d-163">자세한 내용은 [비동기 파일 I/O](asynchronous-file-i-o.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-163">For more information, see [Asynchronous File I/O](asynchronous-file-i-o.md).</span></span>

## <a name="compression"></a><span data-ttu-id="1ba0d-164">압축</span><span class="sxs-lookup"><span data-stu-id="1ba0d-164">Compression</span></span>

<span data-ttu-id="1ba0d-165">압축은 스토리지에 맞춰 파일 크기를 줄이는 프로세스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-165">Compression refers to the process of reducing the size of a file for storage.</span></span> <span data-ttu-id="1ba0d-166">압축 해제는 압축된 파일의 내용을 사용 가능한 형식으로 추출하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-166">Decompression is the process of extracting the contents of a compressed file so they are in a usable format.</span></span> <span data-ttu-id="1ba0d-167"><xref:System.IO.Compression?displayProperty=nameWithType> 네임스페이스는 파일 및 스트림을 압축하고 압축을 푸는 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-167">The <xref:System.IO.Compression?displayProperty=nameWithType> namespace contains types for compressing and decompressing files and streams.</span></span>

<span data-ttu-id="1ba0d-168">다음 클래스는 파일과 스트림을 압축하고 압축 해제할 때 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-168">The following classes are frequently used when compressing and decompressing files and streams:</span></span>

- <span data-ttu-id="1ba0d-169"><xref:System.IO.Compression.ZipArchive> – zip 보관 파일에 항목을 만들고 이를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-169"><xref:System.IO.Compression.ZipArchive> – for creating and retrieving entries in the zip archive.</span></span>

- <span data-ttu-id="1ba0d-170"><xref:System.IO.Compression.ZipArchiveEntry> – 압축된 파일을 표시할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-170"><xref:System.IO.Compression.ZipArchiveEntry> – for representing a compressed file.</span></span>

- <span data-ttu-id="1ba0d-171"><xref:System.IO.Compression.ZipFile> – 압축된 패키지를 만들고 추출하고 여는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-171"><xref:System.IO.Compression.ZipFile> – for creating,  extracting, and opening a compressed package.</span></span>

- <span data-ttu-id="1ba0d-172"><xref:System.IO.Compression.ZipFileExtensions> – 압축된 패키지에 항목을 만들고 추출하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-172"><xref:System.IO.Compression.ZipFileExtensions> – for creating and extracting entries in a compressed package.</span></span>

- <span data-ttu-id="1ba0d-173"><xref:System.IO.Compression.DeflateStream> – Deflate 알고리즘을 사용하여 스트림을 압축 및 압축 해제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-173"><xref:System.IO.Compression.DeflateStream> – for compressing and decompressing streams using the Deflate algorithm.</span></span>

- <span data-ttu-id="1ba0d-174"><xref:System.IO.Compression.GZipStream> – gzip 데이터 형식의 스트림을 압축 및 압축 해제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-174"><xref:System.IO.Compression.GZipStream> – for compressing and decompressing streams in gzip data format.</span></span>

<span data-ttu-id="1ba0d-175">[방법: 파일 압축 및 추출](how-to-compress-and-extract-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-175">See [How to: Compress and Extract Files](how-to-compress-and-extract-files.md).</span></span>

## <a name="isolated-storage"></a><span data-ttu-id="1ba0d-176">격리된 스토리지</span><span class="sxs-lookup"><span data-stu-id="1ba0d-176">Isolated storage</span></span>

<span data-ttu-id="1ba0d-177">격리된 스토리지는 코드와 저장된 데이터를 연결하는 표준화된 방법을 정의하여 격리와 안전을 제공하는 데이터 스토리지 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-177">Isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span> <span data-ttu-id="1ba0d-178">스토리지는 사용자, 어셈블리 및 도메인(옵션)에 의해 격리된 가상 파일 시스템을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-178">The storage provides a virtual file system that is isolated by user, assembly, and (optionally) domain.</span></span> <span data-ttu-id="1ba0d-179">격리된 스토리지는 애플리케이션에 사용자 파일을 액세스할 수 있는 권한이 없는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-179">Isolated storage is particularly useful when your application does not have permission to access user files.</span></span> <span data-ttu-id="1ba0d-180">컴퓨터의 보안 정책에 의해 제어되는 방식으로 애플리케이션에 대한 설정이나 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-180">You can save settings or files for your application in a manner that is controlled by the computer's security policy.</span></span>

<span data-ttu-id="1ba0d-181">격리된 스토리지는 Windows 8.x 스토어 앱에 사용할 수 없습니다. 대신 <xref:Windows.Storage?displayProperty=nameWithType> 네임스페이스의 애플리케이션 데이터 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-181">Isolated storage is not available for Windows 8.x Store apps; instead, use application data classes in the <xref:Windows.Storage?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1ba0d-182">자세한 내용은 [애플리케이션 데이터](/previous-versions/windows/apps/hh464917(v=win.10))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-182">For more information, see [Application data](/previous-versions/windows/apps/hh464917(v=win.10)).</span></span>

<span data-ttu-id="1ba0d-183">다음의 클래스는 격리된 스토리지를 구현할 때 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-183">The following classes are frequently used when implementing isolated storage:</span></span>

- <span data-ttu-id="1ba0d-184"><xref:System.IO.IsolatedStorage.IsolatedStorage> – 격리된 스토리지 구현을 위한 기본 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-184"><xref:System.IO.IsolatedStorage.IsolatedStorage> – provides the base class for isolated storage implementations.</span></span>

- <span data-ttu-id="1ba0d-185"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – 파일 및 디렉터리를 포함하는 격리된 스토리지 영역을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-185"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – provides an isolated storage area that contains files and directories.</span></span>

- <span data-ttu-id="1ba0d-186"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - 격리된 스토리지 내에서 파일을 노출시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-186"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - exposes a file within isolated storage.</span></span>

<span data-ttu-id="1ba0d-187">[격리된 스토리지](isolated-storage.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-187">See [Isolated Storage](isolated-storage.md).</span></span>

## <a name="io-operations-in-windows-store-apps"></a><span data-ttu-id="1ba0d-188">Windows 스토어 앱에서 I/O 작업</span><span class="sxs-lookup"><span data-stu-id="1ba0d-188">I/O operations in Windows Store apps</span></span>

<span data-ttu-id="1ba0d-189">Windows 8.x 스토어 앱용 .NET에는 스트림에서 읽고 스트림에 쓰기 위한 다양한 형식이 포함되어 있습니다. 하지만, 이 세트에 모든 .NET I/O 형식이 포함되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-189">.NET for Windows 8.x Store apps contains many of the types for reading from and writing to streams; however, this set does not include all the .NET I/O types.</span></span>

<span data-ttu-id="1ba0d-190">다음은 Windows 8.x 스토어 앱에서 I/O 작업을 사용할 때 알아야 할 몇 가지 중요한 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-190">Some important differences to note when using I/O operations in Windows 8.x Store apps:</span></span>

- <span data-ttu-id="1ba0d-191"><xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> 및 <xref:System.IO.DirectoryInfo>과(와) 같은 파일 작업과 관련된 형식은 Windows 8.x 스토어 앱용 .NET에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-191">Types specifically related to file operations, such as <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> and <xref:System.IO.DirectoryInfo>, are not included in the .NET for Windows 8.x Store apps.</span></span> <span data-ttu-id="1ba0d-192">대신 <xref:Windows.Storage.StorageFile> 및 <xref:Windows.Storage.StorageFolder> 등 Windows 런타임의 <xref:Windows.Storage?displayProperty=nameWithType> 네임스페이스에 있는 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-192">Instead, use the types in the <xref:Windows.Storage?displayProperty=nameWithType> namespace of the Windows Runtime, such as <xref:Windows.Storage.StorageFile> and <xref:Windows.Storage.StorageFolder>.</span></span>

- <span data-ttu-id="1ba0d-193">격리된 스토리지는 사용할 수 없습니다. 대신에 [애플리케이션 데이터](/previous-versions/windows/apps/hh464917(v=win.10))를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-193">Isolated storage is not available; instead, use [application data](/previous-versions/windows/apps/hh464917(v=win.10)).</span></span>

- <span data-ttu-id="1ba0d-194">비동기 메서드(예: <xref:System.IO.Stream.ReadAsync%2A> 및 <xref:System.IO.Stream.WriteAsync%2A>)를 사용하여 UI 스레드를 차단하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-194">Use asynchronous methods, such as <xref:System.IO.Stream.ReadAsync%2A> and <xref:System.IO.Stream.WriteAsync%2A>, to prevent blocking the UI thread.</span></span>

- <span data-ttu-id="1ba0d-195">경로 기반 압축 형식 <xref:System.IO.Compression.ZipFile> 및 <xref:System.IO.Compression.ZipFileExtensions>는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-195">The path-based compression types <xref:System.IO.Compression.ZipFile> and <xref:System.IO.Compression.ZipFileExtensions> are not available.</span></span> <span data-ttu-id="1ba0d-196">대신 <xref:Windows.Storage.Compression?displayProperty=nameWithType> 네임스페이스에 있는 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-196">Instead, use the types in the <xref:Windows.Storage.Compression?displayProperty=nameWithType> namespace.</span></span>

<span data-ttu-id="1ba0d-197">필요하다면 .NET Framework 스트림과 Windows 런타임 스트림 간에 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-197">You can convert between .NET Framework streams and Windows Runtime streams, if necessary.</span></span> <span data-ttu-id="1ba0d-198">자세한 내용은 [방법: .NET Framework 스트림과 Windows 런타임 스트림 간 변환](how-to-convert-between-dotnet-streams-and-winrt-streams.md) 또는 <xref:System.IO.WindowsRuntimeStreamExtensions>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-198">For more information, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md) or <xref:System.IO.WindowsRuntimeStreamExtensions>.</span></span>

<span data-ttu-id="1ba0d-199">Windows 8.x 스토어 앱에서의 I/O 작업에 대한 자세한 내용은 [빠른 시작: 파일 읽기 및 쓰기](/previous-versions/windows/apps/hh758325(v=win.10))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-199">For more information about I/O operations in a Windows 8.x Store app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span>

## <a name="io-and-security"></a><span data-ttu-id="1ba0d-200">I/O 및 보안</span><span class="sxs-lookup"><span data-stu-id="1ba0d-200">I/O and security</span></span>

<span data-ttu-id="1ba0d-201"><xref:System.IO?displayProperty=nameWithType> 네임스페이스에서 클래스를 사용할 때, 파일 및 디렉터리에 대한 액세스를 제어하기 위해 액세스 제어 목록(ACL)과 같은 운영 체제 보안 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-201">When you use the classes in the <xref:System.IO?displayProperty=nameWithType> namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories.</span></span> <span data-ttu-id="1ba0d-202"><xref:System.Security.Permissions.FileIOPermission> 요구 사항에 이 요구 사항이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-202">This requirement is in addition to any <xref:System.Security.Permissions.FileIOPermission> requirements.</span></span> <span data-ttu-id="1ba0d-203">ACL은 프로그래밍 방식으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-203">You can manage ACLs programmatically.</span></span> <span data-ttu-id="1ba0d-204">자세한 내용은 [방법: 액세스 제어 목록 항목 추가 또는 제거](how-to-add-or-remove-access-control-list-entries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-204">For more information, see [How to: Add or Remove Access Control List Entries](how-to-add-or-remove-access-control-list-entries.md).</span></span>

<span data-ttu-id="1ba0d-205">기본 보안 정책은 인터넷 또는 인트라넷 애플리케이션에서 사용자의 컴퓨터에 있는 파일에 액세스하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-205">Default security policies prevent Internet or intranet applications from accessing files on the user's computer.</span></span> <span data-ttu-id="1ba0d-206">따라서 실제 파일의 경로를 인터넷이나 인트라넷을 통해 다운로드되는 코드를 작성할 때 필요한 I/O 클래스를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-206">Therefore, do not use the I/O classes that require a path to a physical file when writing code that will be downloaded over the internet or intranet.</span></span> <span data-ttu-id="1ba0d-207">대신 .NET 애플리케이션에는 [격리된 스토리지](isolated-storage.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-207">Instead, use [isolated storage](isolated-storage.md) for .NET applications.</span></span>

<span data-ttu-id="1ba0d-208">스트림이 생성될 때만 보안 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-208">A security check is performed only when the stream is constructed.</span></span> <span data-ttu-id="1ba0d-209">따라서 스트림을 열지 말고, 이것을 신뢰할 수 없는 코드 또는 애플리케이션 도메인으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-209">Therefore, do not open a stream and then pass it to less-trusted code or application domains.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1ba0d-210">관련 항목</span><span class="sxs-lookup"><span data-stu-id="1ba0d-210">Related topics</span></span>

- <span data-ttu-id="1ba0d-211">[공통 I/O 작업](common-i-o-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="1ba0d-211">[Common I/O Tasks](common-i-o-tasks.md)</span></span>\
<span data-ttu-id="1ba0d-212">파일, 디렉터리 및 스트림과 관련된 I/O 작업 목록과 각 작업에 대한 예제 및 관련 내용에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-212">Provides a list of I/O tasks associated with files, directories, and streams, and links to relevant content and examples for each task.</span></span>

- <span data-ttu-id="1ba0d-213">[비동기 파일 I/O](asynchronous-file-i-o.md)</span><span class="sxs-lookup"><span data-stu-id="1ba0d-213">[Asynchronous File I/O](asynchronous-file-i-o.md)</span></span>\
<span data-ttu-id="1ba0d-214">비동기 I/O의 기본 연산 및 성능상의 이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-214">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>

- <span data-ttu-id="1ba0d-215">[격리된 스토리지](isolated-storage.md)</span><span class="sxs-lookup"><span data-stu-id="1ba0d-215">[Isolated Storage](isolated-storage.md)</span></span>\
<span data-ttu-id="1ba0d-216">코드와 저장된 데이터를 연결하는 표준화된 방법을 정의하여 격리와 안전을 제공하는 데이터 스토리지 메커니즘에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-216">Describes a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span>

- <span data-ttu-id="1ba0d-217">[파이프](pipe-operations.md)</span><span class="sxs-lookup"><span data-stu-id="1ba0d-217">[Pipes](pipe-operations.md)</span></span>\
<span data-ttu-id="1ba0d-218">.NET의 익명 및 명명된 파이프 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-218">Describes anonymous and named pipe operations in .NET.</span></span>

- <span data-ttu-id="1ba0d-219">[메모리 매핑된 파일](memory-mapped-files.md)</span><span class="sxs-lookup"><span data-stu-id="1ba0d-219">[Memory-Mapped Files](memory-mapped-files.md)</span></span>\
<span data-ttu-id="1ba0d-220">가상 메모리의 디스크에 있는 파일의 내용을 포함하는 메모리 매핑된 파일에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-220">Describes memory-mapped files, which contain the contents of files on disk in virtual memory.</span></span> <span data-ttu-id="1ba0d-221">메모리 매핑된 파일을 사용하면 매우 큰 파일을 편집하고 프로세스 간 통신을 위한 공유 메모리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ba0d-221">You can use memory-mapped files to edit very large files and to create shared memory for interprocess communication.</span></span>
