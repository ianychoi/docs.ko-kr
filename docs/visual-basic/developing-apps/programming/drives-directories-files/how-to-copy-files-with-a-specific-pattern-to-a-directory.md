---
description: '자세한 정보: 방법: Visual Basic에서 특정 패턴의 파일을 디렉터리에 복사'
title: '방법: 특정 패턴의 파일을 디렉터리로 복사'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 2a5163e6420d747a724fec9b8ede8dbcc6a938be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797629"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="9be8d-103">방법: Visual Basic에서 특정 패턴의 파일을 디렉터리에 복사</span><span class="sxs-lookup"><span data-stu-id="9be8d-103">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="9be8d-104"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 메서드는 파일의 경로 이름을 나타내는 읽기 전용 문자열 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-104">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="9be8d-105">`wildCards` 매개 변수를 사용하여 특정 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="9be8d-106">일치하는 파일이 없으면 빈 컬렉션이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-106">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="9be8d-107"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> 메서드를 사용하여 파일을 디렉터리로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-107">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="9be8d-108">특정 패턴의 파일을 디렉터리로 복사하려면</span><span class="sxs-lookup"><span data-stu-id="9be8d-108">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="9be8d-109">`GetFiles` 메서드를 사용하여 파일 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-109">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="9be8d-110">이 예제에서는 지정된 디렉터리에 있는 .rtf 파일을 모두 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-110">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="9be8d-111">`CopyFile` 메서드를 사용하여 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-111">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="9be8d-112">이 예제에서는 `testdirectory`라는 디렉터리로 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-112">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="9be8d-113">`For` 문으로 `Next` 문을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-113">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="9be8d-114">예제</span><span class="sxs-lookup"><span data-stu-id="9be8d-114">Example</span></span>  

 <span data-ttu-id="9be8d-115">위 코드 조각의 완전한 형식인 다음 예제에서는 지정된 디렉터리의 모든 .rtf 파일을 `testdirectory`라는 이름의 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-115">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="9be8d-116">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="9be8d-116">.NET Framework Security</span></span>  

 <span data-ttu-id="9be8d-117">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9be8d-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9be8d-118">길이가 0인 문자열이거나, 공백만 포함하거나, 잘못된 문자를 포함하거나, 경로가 디바이스 경로인 경우(\\\\.\\로 시작됨)와 같은 여러 가지 이유 중 하나로 경로가 올바르지 않은 경우(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="9be8d-119">경로가 `Nothing` 이기 때문에 올바르지 않은 경우(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="9be8d-120">디렉터리가 없는 경우(<xref:System.IO.DirectoryNotFoundException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-120">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="9be8d-121">디렉터리가 기존 파일을 가리키는 경우(<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-121">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="9be8d-122">경로가 시스템 정의 최대 길이를 초과하는 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9be8d-123">경로의 파일 이름이나 디렉터리 이름에 콜론(:)이 있거나 이름의 형식이 잘못된 경우(<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="9be8d-124">경로를 보는 데 필요한 권한이 사용자에게 없는 경우(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="9be8d-125">사용자에게 필요한 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="9be8d-125">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be8d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9be8d-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="9be8d-127">방법: 특정 패턴의 하위 디렉터리 찾기</span><span class="sxs-lookup"><span data-stu-id="9be8d-127">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="9be8d-128">문제 해결: 텍스트 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="9be8d-128">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="9be8d-129">방법: 디렉터리의 파일 컬렉션 가져오기</span><span class="sxs-lookup"><span data-stu-id="9be8d-129">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
