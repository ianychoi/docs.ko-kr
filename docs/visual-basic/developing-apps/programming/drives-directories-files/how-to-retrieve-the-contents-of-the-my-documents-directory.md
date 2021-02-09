---
description: '자세한 정보: 방법: Visual Basic에서 내 문서 디렉터리의 내용 검색'
title: '방법: 내 문서 디렉터리의 내용 검색'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: e9e6ffc202332bd8d1849ef886fd4e7d6cc46a54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797395"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="40a74-103">방법: Visual Basic에서 내 문서 디렉터리의 내용 검색</span><span class="sxs-lookup"><span data-stu-id="40a74-103">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="40a74-104"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> 개체를 사용하여 **내 문서**, **바탕 화면** 등의 많은 **모든 사용자** 디렉터리에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40a74-104">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="40a74-105">내 문서 폴더에서 읽으려면</span><span class="sxs-lookup"><span data-stu-id="40a74-105">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="40a74-106">`ReadAllText` 메서드를 사용하여 특정 디렉터리에 있는 각 파일에서 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="40a74-106">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="40a74-107">다음 코드에서는 디렉터리와 파일을 지정한 다음 `ReadAllText`를 사용하여 `patients`라는 문자열로 읽어옵니다.</span><span class="sxs-lookup"><span data-stu-id="40a74-107">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="40a74-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40a74-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
