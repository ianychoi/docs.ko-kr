---
description: '자세한 정보: 로그에 대 한 스트림을 가져올 수 없습니다.'
title: 로그에 대한 스트림을 가져올 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 6eda12eb4dc2b3cf303e543a66e1f2f7d739eb6b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455277"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="bf255-103">로그에 대한 스트림을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-103">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="bf255-104">로그에 대한 스트림을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-104">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="bf255-105">을 기반으로 하는 잠재적인 파일 이름이 \<name> 이미 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-105">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="bf255-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>기반으로 하는 모든 잠재적인 로그 파일 이름이 이미 사용 중 이므로 클래스에서 새 로그 파일을 만들 수 없습니다 \<name> .</span><span class="sxs-lookup"><span data-stu-id="bf255-106">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="bf255-107">로그 파일이 너무 많으면 애플리케이션의 아키텍처 문제를 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-107">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="bf255-108">자세한 내용은 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 클래스에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf255-108">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf255-109">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="bf255-109">To correct this error</span></span>  
  
1. <span data-ttu-id="bf255-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 속성을 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 또는 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> 로 설정하여 로그 파일 이름에 날짜 스탬프를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="bf255-111"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 개체가 새 로그를 만들 수 있도록 기존 로그를 보관하고 컴퓨터에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bf255-111">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf255-112">추가 정보</span><span class="sxs-lookup"><span data-stu-id="bf255-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="bf255-113">내 응용 프로그램 .Log</span><span class="sxs-lookup"><span data-stu-id="bf255-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="bf255-114">DirectoryPath.</span><span class="sxs-lookup"><span data-stu-id="bf255-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
