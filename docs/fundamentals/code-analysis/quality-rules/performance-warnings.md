---
title: 성능 규칙 (코드 분석)
description: 코드 분석 성능 규칙에 대해 알아봅니다.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- rules, performance
- performance rules
- performance, rules
- managed code analysis rules, performance rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 4409cc46eb73f13f8e59d7a51899da27035bb6af
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592400"
---
# <a name="performance-rules"></a>성능 규칙

성능 규칙은 고성능 라이브러리 및 응용 프로그램을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

| 규칙 | 설명 |
| - | - |
| [CA1802: 가능하면 리터럴을 사용하세요.](ca1802.md) | 필드는 정적 및 읽기 전용으로 선언 되 고 (Visual Basic에서 공유 및 ReadOnly) 컴파일 타임에 계산할 수 값으로 초기화 됩니다. 대상 필드에 할당 되는 값은 컴파일 시간에 계산할 수 때문에 런타임 대신 컴파일 시간에 값이 계산 되도록 선언을 const (Visual Basic의 Const) 필드로 변경 합니다. |
| [CA1805: 불필요 하 게 초기화 하지 마십시오.](ca1805.md) | .NET 런타임은 생성자를 실행 하기 전에 참조 형식의 모든 필드를 기본값으로 초기화 합니다. 대부분의 경우 필드를 기본값으로 명시적으로 초기화 하면 유지 관리 비용이 증가 하 고 성능이 저하 될 수 있습니다 (예: 어셈블리 크기 증가). |
| [CA1806: 메서드 결과를 무시하지 마세요.](ca1806.md) | 새 개체가 만들어졌지만 사용 되지 않거나, 새 문자열을 만들고 반환 하는 메서드가 호출 되 고 새 문자열이 사용 되지 않거나, COM (구성 요소 개체 모델) 또는 P/Invoke 메서드가 사용 되지 않는 HRESULT 또는 오류 코드를 반환 합니다. |
| [CA1810: 참조 형식 정적 필드를 인라인으로 초기화하세요.](ca1810.md) | 형식이 명시적인 정적 생성자를 선언하면 JIT(Just-in-Time) 컴파일러는 형식의 각 정적 메서드와 인스턴스 생성자에 검사를 추가하여 정적 생성자를 이전에 호출했는지 확인합니다. 정적 생성자 검사로 인해 성능이 저하될 수 있습니다. |
| [CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.](ca1812.md) | 어셈블리 수준 형식의 인스턴스가 어셈블리에서 코드에 의해 만들어지지 않습니다. |
| [CA1813: 봉인되지 않은 특성을 사용하지 마세요.](ca1813.md) | .NET에서는 사용자 지정 특성을 검색 하는 메서드를 제공 합니다. 기본적으로 이러한 메서드는 특성 상속 계층을 검색합니다. 특성을 봉인하면 상속 계층을 검색하지 않으므로 성능이 향상될 수 있습니다. |
| [CA1814: 다차원 배열보다 가변 배열을 사용하세요.](ca1814.md) | 가변 배열의 요소에는 배열이 사용됩니다. 요소를 구성 하는 배열은 크기가 다를 수 있으며,이로 인해 일부 데이터 집합에 대해 공간을 낭비 하 게 될 수 있습니다. |
| [CA1815: 값 형식에서 Equals 또는 같음 연산자를 재정의하세요.](ca1815.md) | 값 형식의 경우 Equals의 상속된 구현에서 Reflection 라이브러리를 사용하며 모든 필드의 내용을 비교합니다. Reflection에는 많은 계산이 요구되며 모든 필드의 일치 여부를 비교하는 것이 불필요할 수 있습니다. 사용자가 인스턴스를 비교 또는 정렬하거나 인스턴스를 해시 테이블 키로 사용할 것으로 예측되는 경우에는 값 형식에서 Equals를 구현해야 합니다. |
| [CA1819: 속성은 배열을 반환해서는 안 됩니다.](ca1819.md) | 속성이 읽기 전용 이더라도 속성에 의해 반환 되는 배열은 쓰기 방지 되지 않습니다. 배열을 무단으로 변경하지 못하도록 하려면 속성에서 배열의 복사본을 반환해야 합니다. 일반적으로 사용자는 이러한 속성을 호출할 경우 성능에 부정적인 영향을 준다는 것을 인식하지 못합니다. |
| [CA1820: 문자열 길이를 사용하여 빈 문자열을 테스트하세요.](ca1820.md) | String.Length 속성이나 String.IsNullOrEmpty 메서드를 사용하여 문자열을 비교하는 것이 Equals를 사용하는 것보다 훨씬 더 빠릅니다. |
| [CA1821: 빈 종료자를 제거하십시오.](ca1821.md) | 개체 수명을 추적할 때에는 추가로 성능 오버헤드가 발생하므로 가능한 경우 종료자를 사용하지 마십시오. 빈 종료자는 장점 없이 추가 오버 헤드를 발생 시킵니다. |
| [CA1822: 멤버를 static으로 표시하세요.](ca1822.md) | 인스턴스 데이터에 액세스 하지 않거나 인스턴스 메서드를 호출 하는 멤버는 static으로 표시할 수 있습니다 (Visual Basic에서 공유). 메서드를 static으로 표시하면 컴파일러는 이러한 멤버에 대한 비가상 호출 사이트를 내보냅니다. 이 경우 성능이 중요한 코드에서 성능이 크게 향상될 수 있습니다. |
| [CA1823: 사용되지 않는 전용 필드를 사용하지 마세요.](ca1823.md) | 어셈블리에서 액세스되지 않는 것으로 보이는 전용 필드가 발견되었습니다. |
| [CA1824: NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.](ca1824.md) | NeutralResourcesLanguage 특성은 어셈블리에 대 한 중립 문화권의 리소스를 표시 하는 데 사용 된 언어 리소스 관리자에 게 알립니다. 이렇게 하면 로드한 첫 리소스에 대한 찾기 성능을 향상시킬 수 있으며 작업이 간단해집니다. |
| [CA1825: 길이가 0인 배열 할당 방지](ca1825.md) | 길이가 0 인 배열을 초기화 하면 불필요 한 메모리 할당이 발생 합니다. 대신를 호출 하 여 정적으로 할당 된 빈 배열 인스턴스를 사용 합니다 <xref:System.Array.Empty%2A?displayProperty=nameWithType> . 메모리 할당은이 메서드의 모든 호출에서 공유 됩니다. |
| [CA1826: Linq Enumerable 메서드 대신 속성을 사용하세요.](ca1826.md) | <xref:System.Linq.Enumerable> LINQ 메서드는 보다 효율적인 동등한 속성을 지 원하는 형식에서 사용 되었습니다. |
| [CA1827: Any를 사용할 수 있는 경우 Count/LongCount를 사용하지 마세요.](ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> 또는 메서드가 <xref:System.Linq.Enumerable.LongCount%2A> 더 효율적으로 사용 되었습니다 <xref:System.Linq.Enumerable.Any%2A> . |
| [CA1828: AnyAsync를 사용할 수 있는 경우 CountAsync/LongCountAsync를 사용하지 마세요.](ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> 또는 메서드가 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> 더 효율적으로 사용 되었습니다 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> . |
| [CA1829: Enumerable.Count 메서드 대신 Length/Count 속성을 사용하세요.](ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> LINQ 메서드가 동등한, 보다 효율적인 또는 속성을 지 원하는 형식에서 사용 `Length` 되었습니다 `Count` . |
| [CA1830: StringBuilder에서 강력한 형식의 추가 및 삽입 메서드 오버로드를 사용하세요.](ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> 및 <xref:System.Text.StringBuilder.Insert%2A> 는 system.string 이외의 여러 형식에 대 한 오버 로드를 제공 합니다.  가능 하면 ToString () 및 문자열 기반 오버 로드를 사용 하는 것 보다 강력한 형식의 오버 로드를 사용 하는 것이 좋습니다. |
| [CA1831: 적절한 경우 문자열에 대해 범위 기반 인덱서 대신 AsSpan을 사용하세요.](ca1831.md) | 문자열에 범위-인덱서를 사용 하 고 해당 값을 ReadOnlySpan char 형식에 암시적으로 할당 하는 경우 &lt; &gt; 이 메서드는 <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 문자열의 요청 된 부분 복사본을 생성 하는 대신 사용 됩니다. |
| [CA1832: 배열의 ReadOnlySpan 또는 ReadOnlyMemory 부분을 가져오려면 범위 기반 인덱서 대신 AsSpan 또는 AsMemory를 사용하세요.](ca1832.md) | 배열에 범위-인덱서를 사용 하 고 또는 형식에 값을 암시적으로 할당 하는 경우 <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> 이 메서드는 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 배열에서 요청 된 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 부분의 복사본을 생성 하는 대신 사용 됩니다. |
| [CA1833: 배열의 Span 또는 Memory 부분을 가져오려면 범위 기반 인덱서 대신 AsSpan 또는 AsMemory를 사용하세요.](ca1833.md) | 배열에 범위-인덱서를 사용 하 고 또는 형식에 값을 암시적으로 할당 하는 경우 <xref:System.Span%601> <xref:System.Memory%601> 이 메서드는 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 배열에서 요청 된 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> 부분의 복사본을 생성 하는 대신 사용 됩니다. |
| [CA1834: 단일 문자열에 대해 StringBuilder.Append(char)를 사용하세요.](ca1834.md) | <xref:System.Text.StringBuilder>`Append`에는를 인수로 사용 하는 오버 로드가 있습니다 `char` . `char`성능 향상을 위해 오버 로드를 호출 하는 것이 좋습니다. |
| [CA1835: ' ReadAsync ' 및 ' WriteAsync '에 대해 ' Memory' 기반 오버 로드를 선호 합니다.](ca1835.md) | ' Stream '에는 첫 번째 인수로 ' Memory Byte '를 사용 하는 ' ReadAsync ' 오버 로드 &lt; &gt; 와 ' ReadOnlyMemory &lt; Byte &gt; '를 첫 번째 인수로 사용 하는 ' WriteAsync ' 오버 로드가 있습니다. 더 효율적인 메모리 기반 오버 로드를 호출 하는 것이 좋습니다. |
| [CA1836: `IsEmpty` `Count` 사용 가능한 경우 선호](ca1836.md) | `IsEmpty`, 또는 보다 효율적인 속성을 사용 `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 하 여 개체에 항목이 포함 되어 있는지 여부를 확인 하는 것이 좋습니다. |
| [CA1837: 대신을 사용 합니다. `Environment.ProcessId``Process.GetCurrentProcess().Id`](ca1837.md) | `Environment.ProcessId` 는 보다 간단 하 고 빠릅니다 `Process.GetCurrentProcess().Id` . |
| [CA1838: `StringBuilder` P/invoke에 대 한 매개 변수를 사용 하지 않습니다.](ca1838.md) | 를 마샬링하면 `StringBuilder` 항상 네이티브 버퍼 복사본이 만들어지므로 하나의 마샬링 작업에 대해 여러 할당이 발생 합니다. |
