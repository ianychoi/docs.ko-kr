---
title: SYSLIB0011 경고
description: 컴파일 시간 경고 SYSLIB0011을 생성하는 사용되지 않음에 대해 알아봅니다.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189859"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="25834-103">SYSLIB0011: BinaryFormatter serialization이 사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="25834-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="25834-104"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>의 [보안 취약성](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities)으로 인해 다음 API는 .NET 5.0부터 사용되지 않는 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25834-104">Due to [security vulnerabilities](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="25834-105">코드에서 이러한 API를 사용하면 컴파일 시간에 `SYSLIB0011` 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="25834-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="25834-106">해결 방법</span><span class="sxs-lookup"><span data-stu-id="25834-106">Workarounds</span></span>

<span data-ttu-id="25834-107"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 대신 <xref:System.Text.Json.JsonSerializer>나 <xref:System.Xml.Serialization.XmlSerializer>를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25834-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="25834-108">권장 작업에 대한 자세한 내용은 [BinaryFormatter 사용 중지 및 비활성화 오류 해결](../../../standard/serialization/binaryformatter-security-guide.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25834-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="25834-109">추가 정보</span><span class="sxs-lookup"><span data-stu-id="25834-109">See also</span></span>

- [<span data-ttu-id="25834-110">BinaryFormatter 사용되지 않음 및 비활성화 오류 해결</span><span class="sxs-lookup"><span data-stu-id="25834-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](../../../standard/serialization/binaryformatter-security-guide.md)
- [<span data-ttu-id="25834-111">ASP.NET 앱에서 BinaryFormatter serialization 메서드가 사용되지 않고 금지됨</span><span class="sxs-lookup"><span data-stu-id="25834-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
