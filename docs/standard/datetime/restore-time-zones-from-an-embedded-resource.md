---
description: '자세히 알아보기: 방법: 포함 리소스에서 표준 시간대 복원'
title: '방법: 포함 리소스에서 표준 시간대 복원'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702485"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="bc4c2-103">방법: 포함 리소스에서 표준 시간대 복원</span><span class="sxs-lookup"><span data-stu-id="bc4c2-103">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="bc4c2-104">이 항목에서는 리소스 파일에 저장 된 표준 시간대를 복원 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-104">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="bc4c2-105">표준 시간대를 저장 하는 방법에 대 한 자세한 내용 및 지침은 [방법: 포함 리소스에 표준 시간대 저장](save-time-zones-to-an-embedded-resource.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-105">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="bc4c2-106">포함 리소스에서 TimeZoneInfo 개체를 deserialize 하려면</span><span class="sxs-lookup"><span data-stu-id="bc4c2-106">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="bc4c2-107">검색할 표준 시간대가 사용자 지정 표준 시간대가 아닌 경우 메서드를 사용 하 여 인스턴스화합니다 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-107">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="bc4c2-108">포함 된 <xref:System.Resources.ResourceManager> 리소스 파일의 정규화 된 이름과 리소스 파일을 포함 하는 어셈블리에 대 한 참조를 전달 하 여 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-108">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="bc4c2-109">포함 된 리소스 파일의 정규화 된 이름을 확인할 수 없는 경우 [Ildasm.exe (IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md) 를 사용 하 여 어셈블리의 매니페스트를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-109">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="bc4c2-110">`.mresource`항목은 리소스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-110">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="bc4c2-111">이 예제에서 리소스의 정규화 된 이름은 `SerializeTimeZoneData.SerializedTimeZones` 입니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-111">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="bc4c2-112">리소스 파일이 표준 시간대 인스턴스화 코드를 포함 하는 동일한 어셈블리에 포함 된 경우 `static` ( `Shared` Visual Basic) 메서드를 호출 하 여 해당 파일에 대 한 참조를 검색할 수 있습니다 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-112">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="bc4c2-113">메서드에 대 한 호출이 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 실패 하거나 사용자 지정 표준 시간대를 인스턴스화하는 경우 메서드를 호출 하 여 serialize 된 표준 시간대가 포함 된 문자열을 검색 합니다 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-113">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="bc4c2-114">메서드를 호출 하 여 표준 시간대 데이터를 Deserialize 합니다 <xref:System.TimeZoneInfo.FromSerializedString%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-114">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="bc4c2-115">예제</span><span class="sxs-lookup"><span data-stu-id="bc4c2-115">Example</span></span>

<span data-ttu-id="bc4c2-116">다음 예제에서는 포함 된 <xref:System.TimeZoneInfo> .NET XML 리소스 파일에 저장 된 개체를 deserialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-116">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="bc4c2-117">이 코드에서는 응용 프로그램에 필요한 개체가 있는지 확인 하는 예외 처리를 보여 줍니다 <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-117">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="bc4c2-118">먼저 <xref:System.TimeZoneInfo> 메서드를 사용 하 여 레지스트리에서 개체를 검색 하 여 인스턴스화합니다 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-118">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="bc4c2-119">표준 시간대를 인스턴스화할 수 없는 경우 코드는 포함 된 리소스 파일에서 해당 표준 시간대를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-119">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="bc4c2-120">사용자 지정 표준 시간대 (메서드를 사용 하 여 인스턴스화된 표준 시간대 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> )의 데이터는 레지스트리에 저장 되지 않으므로 코드는를 호출 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 하 여 Palmer, 남극 지역에 대 한 표준 시간대를 인스턴스화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-120">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="bc4c2-121">대신, 메서드를 호출 하기 전에 표준 시간대의 데이터가 포함 된 문자열을 검색 하기 위해 포함 된 리소스 파일을 즉시 찾습니다 <xref:System.TimeZoneInfo.FromSerializedString%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc4c2-121">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="bc4c2-122">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="bc4c2-122">Compiling the code</span></span>

<span data-ttu-id="bc4c2-123">이 예제에는 다음 사항이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-123">This example requires:</span></span>

- <span data-ttu-id="bc4c2-124">System.Windows.Forms.dll에 대 한 참조가 프로젝트에 추가 System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-124">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="bc4c2-125">다음 네임 스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bc4c2-125">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="bc4c2-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc4c2-126">See also</span></span>

- [<span data-ttu-id="bc4c2-127">날짜, 시간 및 표준 시간대</span><span class="sxs-lookup"><span data-stu-id="bc4c2-127">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="bc4c2-128">표준 시간대 개요</span><span class="sxs-lookup"><span data-stu-id="bc4c2-128">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="bc4c2-129">방법: 포함 리소스에 표준 시간대 저장</span><span class="sxs-lookup"><span data-stu-id="bc4c2-129">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
