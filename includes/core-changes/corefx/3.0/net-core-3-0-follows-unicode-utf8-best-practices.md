---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032143"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="80dcb-101">잘못된 형식의 UTF-8바이트 시퀀스 교체는 유니코드 지침을 따름</span><span class="sxs-lookup"><span data-stu-id="80dcb-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="80dcb-102">바이트-문자 코드 변환 작업 중에 <xref:System.Text.UTF8Encoding> 클래스에서 형식이 잘못된 UTF-8바이트 시퀀스가 있는 경우 출력 문자열에서 이 시퀀스가 '�' 문자(U+FFFD 대체 문자)로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="80dcb-103">.NET Core 3.0은 이전 버전의 .NET Core 및 .NET Framework와 달리 트랜스코딩 작업 도중 이 대체를 수행하기 위해 유니코드 모범 사례를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="80dcb-104">이는 새로운 <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> 및 <xref:System.Text.Rune?displayProperty=nameWithType> 형식을 포함하여 .NET 전체에서 UTF-8 처리를 향상하기 위해 기울인 보다 많은 노력의 일환입니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="80dcb-105"><xref:System.Text.UTF8Encoding> 형식에는 새로 도입된 형식과 일치하는 출력을 생성하도록 향상된 오류 처리 메커니즘이 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="80dcb-106">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="80dcb-106">Change description</span></span>

<span data-ttu-id="80dcb-107">.Net Core 3.0부터 바이트를 문자로 트랜스코딩하는 경우 <xref:System.Text.UTF8Encoding> 클래스는 유니코드 모범 사례를 기반으로 문자 대체를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="80dcb-108">사용되는 대체 메커니즘은 _최대 하위 부분의 U+FFFD 대체_ 항목의 [유니코드 표준 버전 12.0, 섹션 3.9(PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf)에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="80dcb-109">이 동작은 입력 바이트 시퀀스에 잘못된 형식의 UTF-8 데이터가 포함된 _경우에만_ 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="80dcb-110">또한 <xref:System.Text.UTF8Encoding> 인스턴스가 `throwOnInvalidBytes: true`를 사용하여 구성된 경우 `UTF8Encoding` 인스턴스는 U+FFFD 대체를 수행하는 대신 잘못된 입력에 대해 계속 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="80dcb-111">`UTF8Encoding` 생성자에 대한 자세한 내용은 <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80dcb-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="80dcb-112">다음 표에서는 잘못된 3바이트 입력으로 인한 이 변경의 영향을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="80dcb-113">잘못된 형식의 3바이트 입력</span><span class="sxs-lookup"><span data-stu-id="80dcb-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="80dcb-114">.NET Core 3.0 이하의 출력</span><span class="sxs-lookup"><span data-stu-id="80dcb-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="80dcb-115">.NET Core 3.0 이상의 출력</span><span class="sxs-lookup"><span data-stu-id="80dcb-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="80dcb-116">`[ FFFD FFFD ]`(2자 출력)</span><span class="sxs-lookup"><span data-stu-id="80dcb-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="80dcb-117">`[ FFFD FFFD FFFD ]`(3자 출력)</span><span class="sxs-lookup"><span data-stu-id="80dcb-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="80dcb-118">3자 출력은 위에 링크된 유니코드 표준 PDF의 _표 3-9_ 에 따라 선호되는 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="80dcb-119">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="80dcb-119">Version introduced</span></span>

<span data-ttu-id="80dcb-120">3.0</span><span class="sxs-lookup"><span data-stu-id="80dcb-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="80dcb-121">권장 조치</span><span class="sxs-lookup"><span data-stu-id="80dcb-121">Recommended action</span></span>

<span data-ttu-id="80dcb-122">개발자는 아무 작업도 수행하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80dcb-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="80dcb-123">범주</span><span class="sxs-lookup"><span data-stu-id="80dcb-123">Category</span></span>

<span data-ttu-id="80dcb-124">핵심 .NET 라이브러리</span><span class="sxs-lookup"><span data-stu-id="80dcb-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80dcb-125">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="80dcb-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
