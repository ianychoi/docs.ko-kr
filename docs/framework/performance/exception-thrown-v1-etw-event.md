---
title: 예외가 throw된 V1 ETW 이벤트
description: ExceptionThrown_V1 ETW 이벤트에 대 한 자세한 정보를 확인 합니다. Throw 된 예외에 대해 필드 이름, 데이터 형식 및 설명과 같은 이벤트 데이터가 제공 됩니다.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: c1ba994b291bd278a95e34beb0b02ed6581786e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263479"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="f64ae-104">예외가 throw된 V1 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="f64ae-104">Exception Thrown_V1 ETW Event</span></span>

<span data-ttu-id="f64ae-105">이 이벤트는 throw된 예외에 대한 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="f64ae-106">다음 표에서는 이벤트가 발생하는 키워드 및 이벤트 수준을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="f64ae-107">자세한 내용은 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f64ae-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f64ae-108">이벤트를 발생시키기 위한 키워드</span><span class="sxs-lookup"><span data-stu-id="f64ae-108">Keyword for raising the event</span></span>|<span data-ttu-id="f64ae-109">Level</span><span class="sxs-lookup"><span data-stu-id="f64ae-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f64ae-110">`ExceptionKeyword`(0x8000)</span><span class="sxs-lookup"><span data-stu-id="f64ae-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="f64ae-111">경고(2)</span><span class="sxs-lookup"><span data-stu-id="f64ae-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="f64ae-112">다음 표에서는 이벤트 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="f64ae-113">이벤트</span><span class="sxs-lookup"><span data-stu-id="f64ae-113">Event</span></span>|<span data-ttu-id="f64ae-114">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f64ae-114">Event ID</span></span>|<span data-ttu-id="f64ae-115">발생 시기</span><span class="sxs-lookup"><span data-stu-id="f64ae-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="f64ae-116">80</span><span class="sxs-lookup"><span data-stu-id="f64ae-116">80</span></span>|<span data-ttu-id="f64ae-117">관리되는 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="f64ae-118">다음 표에서는 이벤트 데이터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="f64ae-119">필드 이름</span><span class="sxs-lookup"><span data-stu-id="f64ae-119">Field name</span></span>|<span data-ttu-id="f64ae-120">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f64ae-120">Data type</span></span>|<span data-ttu-id="f64ae-121">Description</span><span class="sxs-lookup"><span data-stu-id="f64ae-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f64ae-122">예외 유형</span><span class="sxs-lookup"><span data-stu-id="f64ae-122">Exception Type</span></span>|<span data-ttu-id="f64ae-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f64ae-123">win:UnicodeString</span></span>|<span data-ttu-id="f64ae-124">예외 형식, 예: `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="f64ae-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="f64ae-125">예외 메시지</span><span class="sxs-lookup"><span data-stu-id="f64ae-125">Exception Message</span></span>|<span data-ttu-id="f64ae-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f64ae-126">win:UnicodeString</span></span>|<span data-ttu-id="f64ae-127">실제 예외 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-127">Actual exception message.</span></span>|  
|<span data-ttu-id="f64ae-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="f64ae-128">EIPCodeThrow</span></span>|<span data-ttu-id="f64ae-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="f64ae-129">win:Pointer</span></span>|<span data-ttu-id="f64ae-130">예외가 발생한 명령 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="f64ae-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="f64ae-131">ExceptionHR</span></span>|<span data-ttu-id="f64ae-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f64ae-132">win:UInt32</span></span>|<span data-ttu-id="f64ae-133">예외 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)입니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="f64ae-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="f64ae-134">ExceptionFlags</span></span>|<span data-ttu-id="f64ae-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f64ae-135">win:UInt16</span></span>|<span data-ttu-id="f64ae-136">0x01: HasInnerException(Visual Basic 설명서에서 [CLR ETW Events](clr-etw-events.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="f64ae-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="f64ae-137">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="f64ae-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="f64ae-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="f64ae-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="f64ae-139">0x08: IsCorruptedStateException (프로세스 상태가 손상 되었음을 나타냅니다. [손상 된 상태 예외 처리](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)를 참조 하세요.)</span><span class="sxs-lookup"><span data-stu-id="f64ae-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="f64ae-140">0x10: IsCLSCompliant(<xref:System.Exception>에서 파생된 예외는 CLS와 호환됨, 그러지 않으면 CLS와 호환되지 않음).</span><span class="sxs-lookup"><span data-stu-id="f64ae-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="f64ae-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f64ae-141">ClrInstanceID</span></span>|<span data-ttu-id="f64ae-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f64ae-142">win:UInt16</span></span>|<span data-ttu-id="f64ae-143">CLR 또는 CoreCLR 인스턴스에 대한 고유 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f64ae-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f64ae-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f64ae-144">See also</span></span>

- [<span data-ttu-id="f64ae-145">CLR ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="f64ae-145">CLR ETW Events</span></span>](clr-etw-events.md)
