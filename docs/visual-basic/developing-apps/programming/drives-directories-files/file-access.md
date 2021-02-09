---
description: '자세한 정보: Visual Basic을 사용한 파일 액세스'
title: 파일 액세스
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: b3ea742185e7219ce7fdfb8eee987fd9c17e3a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666318"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="ecb05-103">Visual Basic을 사용한 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="ecb05-103">File Access with Visual Basic</span></span>

<span data-ttu-id="ecb05-104">`My.Computer.FileSystem` 개체는 파일 및 폴더로 작업하기 위한 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-104">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="ecb05-105">해당 속성, 메서드 및 이벤트를 사용하여 파일 및 폴더를 만들고 복사, 이동, 조사 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-105">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="ecb05-106">`My.Computer.FileSystem`은 이전 버전과의 호환성을 위해 Visual Basic에서 제공하는 레거시 함수(`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput` 등)보다 뛰어난 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-106">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecb05-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ecb05-107">In This Section</span></span>  

 [<span data-ttu-id="ecb05-108">파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="ecb05-108">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="ecb05-109">`My.Computer.FileSystem` 개체를 사용하여 파일에서 읽기에 대한 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-109">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="ecb05-110">파일에 쓰기</span><span class="sxs-lookup"><span data-stu-id="ecb05-110">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="ecb05-111">`My.Computer.FileSystem` 개체를 사용하여 파일에 쓰기에 대한 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-111">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="ecb05-112">파일 및 디렉터리 만들기, 삭제 및 이동</span><span class="sxs-lookup"><span data-stu-id="ecb05-112">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="ecb05-113">`My.Computer.FileSystem` 개체를 사용하여 파일 및 폴더 만들기, 복사, 삭제 및 이동에 대한 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-113">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="ecb05-114">TextFieldParser 개체를 사용하여 텍스트 파일 구문 분석</span><span class="sxs-lookup"><span data-stu-id="ecb05-114">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="ecb05-115">`TextFieldReader`를 사용하여 로그와 같은 텍스트 파일을 구문 분석하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-115">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="ecb05-116">파일 인코딩</span><span class="sxs-lookup"><span data-stu-id="ecb05-116">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="ecb05-117">파일 인코딩 및 용도에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-117">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="ecb05-118">연습: Visual Basic에서 파일과 디렉터리 조작</span><span class="sxs-lookup"><span data-stu-id="ecb05-118">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="ecb05-119">파일 및 폴더에 대한 정보를 보고하는 유틸리티를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-119">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="ecb05-120">문제 해결: 텍스트 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="ecb05-120">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="ecb05-121">텍스트 파일에서 일고 쓸 때 발생하는 일반적인 문제를 나열하고 각 문제에 대한 해결책을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb05-121">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
