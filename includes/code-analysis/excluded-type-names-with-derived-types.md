---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97531906"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="0ecfe-101">특정 형식 및 파생 형식 제외</span><span class="sxs-lookup"><span data-stu-id="0ecfe-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="0ecfe-102">분석에서 특정 형식과 해당 파생 형식을 제외할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="0ecfe-103">예를 들어 이름이이 고 파생 형식이 인 모든 메서드에서 규칙이 실행 되지 않도록 지정 하려면 `MyType` 프로젝트의 *editorconfig* 파일에 다음 키-값 쌍을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="0ecfe-104">옵션 값의 허용 되는 기호 이름 형식 (로 구분 `|` ):</span><span class="sxs-lookup"><span data-stu-id="0ecfe-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="0ecfe-105">형식 이름만 (포함 하는 형식 또는 네임 스페이스에 관계 없이 이름이 인 모든 형식 포함).</span><span class="sxs-lookup"><span data-stu-id="0ecfe-105">Type name only (includes all types with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="0ecfe-106">기호 [설명서 ID 형식의](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)정규화 된 이름 (옵션 접두사 포함) `T:`</span><span class="sxs-lookup"><span data-stu-id="0ecfe-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="0ecfe-107">예제:</span><span class="sxs-lookup"><span data-stu-id="0ecfe-107">Examples:</span></span>

| <span data-ttu-id="0ecfe-108">옵션 값</span><span class="sxs-lookup"><span data-stu-id="0ecfe-108">Option Value</span></span> | <span data-ttu-id="0ecfe-109">요약</span><span class="sxs-lookup"><span data-stu-id="0ecfe-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="0ecfe-110">모든 형식과 `MyType` 해당 파생 형식 모두와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="0ecfe-111">`MyType1`또는 `MyType2` 와 모든 파생 형식 중 하나에 해당 하는 모든 형식을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="0ecfe-112">`MyType`지정 된 정규화 된 이름 및 모든 파생 형식과 특정 형식을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="0ecfe-113">특정 형식 및 해당 하는 `MyType1` `MyType2` 정규화 된 이름과 모든 파생 형식을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0ecfe-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |
