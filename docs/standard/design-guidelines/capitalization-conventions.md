---
title: 대/소문자 표기법
description: 식별자, 복합 단어 및 일반적인 용어에 대 한 대/소문자 규칙을 적용 합니다. .NET에서 대/소문자 구분이 작동 하는 방식을 이해 합니다.
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: e416a8346952a41d9c89f526bfce990dfc277fc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701265"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="705e5-104">대/소문자 표기법</span><span class="sxs-lookup"><span data-stu-id="705e5-104">Capitalization Conventions</span></span>

<span data-ttu-id="705e5-105">이 장의 지침은 일관 되 게 적용 될 때 형식, 멤버 및 매개 변수에 대 한 식별자를 쉽게 읽을 수 있도록 하는 사례를 사용 하는 간단한 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="705e5-106">식별자에 대 한 대/소문자 규칙</span><span class="sxs-lookup"><span data-stu-id="705e5-106">Capitalization Rules for Identifiers</span></span>

 <span data-ttu-id="705e5-107">식별자에서 단어를 구분 하려면 식별자에서 각 단어의 첫 글자를 대문자로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="705e5-108">밑줄을 사용 하 여 단어를 구분 하거나 식별자의 어디에서 나 해당 문제를 구분 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="705e5-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="705e5-109">식별자를 사용 하는 방법에 따라 두 가지 적절 한 방법으로 식별자를 대문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="705e5-110">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="705e5-110">PascalCasing</span></span>

- <span data-ttu-id="705e5-111">camelCasing</span><span class="sxs-lookup"><span data-stu-id="705e5-111">camelCasing</span></span>

 <span data-ttu-id="705e5-112">매개 변수 이름을 제외한 모든 식별자에 사용 되는 대/소문자 구분 규칙은 다음 예제에 표시 된 것과 같이 각 단어의 첫 번째 문자 (두 문자 길이에 대 한 머리글자어 포함)를 대문자로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="705e5-113">다음 식별자에 표시 된 것 처럼 두 문자를 대문자로 표기 하는 두 문자로 된 머리글자어에 대해 특별 한 사례가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="705e5-114">다음 예제와 같이 매개 변수 이름에만 사용 되는 camelCasing 규칙은 첫 번째 단어를 제외 하 고 각 단어의 첫 번째 문자를 대문자로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="705e5-115">또한이 예제에서는 카멜식 대/소문자를 구분 하는 식별자를 시작 하는 두 문자로 된 머리글자어는 모두 소문자입니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="705e5-116">✔️는 여러 단어로 구성 된 모든 public 멤버, 형식 및 네임 스페이스 이름에 대 한 대/소문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="705e5-117">매개 변수 이름에 camelCasing를 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="705e5-118">다음 표에서는 다양 한 유형의 식별자에 대 한 대/소문자 규칙을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="705e5-119">ID</span><span class="sxs-lookup"><span data-stu-id="705e5-119">Identifier</span></span>|<span data-ttu-id="705e5-120">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="705e5-120">Casing</span></span>|<span data-ttu-id="705e5-121">예제</span><span class="sxs-lookup"><span data-stu-id="705e5-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="705e5-122">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="705e5-122">Namespace</span></span>|<span data-ttu-id="705e5-123">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="705e5-124">Type</span><span class="sxs-lookup"><span data-stu-id="705e5-124">Type</span></span>|<span data-ttu-id="705e5-125">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="705e5-126">인터페이스</span><span class="sxs-lookup"><span data-stu-id="705e5-126">Interface</span></span>|<span data-ttu-id="705e5-127">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="705e5-128">메서드</span><span class="sxs-lookup"><span data-stu-id="705e5-128">Method</span></span>|<span data-ttu-id="705e5-129">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="705e5-130">속성</span><span class="sxs-lookup"><span data-stu-id="705e5-130">Property</span></span>|<span data-ttu-id="705e5-131">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="705e5-132">이벤트</span><span class="sxs-lookup"><span data-stu-id="705e5-132">Event</span></span>|<span data-ttu-id="705e5-133">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="705e5-134">필드</span><span class="sxs-lookup"><span data-stu-id="705e5-134">Field</span></span>|<span data-ttu-id="705e5-135">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="705e5-136">열거형 값</span><span class="sxs-lookup"><span data-stu-id="705e5-136">Enum value</span></span>|<span data-ttu-id="705e5-137">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="705e5-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="705e5-138">Parameter</span></span>|<span data-ttu-id="705e5-139">Camel</span><span class="sxs-lookup"><span data-stu-id="705e5-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="705e5-140">복합 단어 및 일반적인 단어를 대문자로</span><span class="sxs-lookup"><span data-stu-id="705e5-140">Capitalizing Compound Words and Common Terms</span></span>

 <span data-ttu-id="705e5-141">대부분의 복합 용어는 대문자 표시를 위해 단일 단어로 취급 됩니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="705e5-142">❌ 닫힌 형태의 복합 단어에서 각 단어를 대문자로 표기 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="705e5-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="705e5-143">이러한 단어는 끝점과 같이 단일 단어로 작성 된 복합 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="705e5-144">대/소문자를 구분 하기 위해 폐쇄형 형식의 복합 단어를 단일 단어로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="705e5-145">현재 사전을 사용 하 여 복합 단어가 닫힌 형태로 작성 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="705e5-146">파스칼식</span><span class="sxs-lookup"><span data-stu-id="705e5-146">Pascal</span></span>|<span data-ttu-id="705e5-147">Camel</span><span class="sxs-lookup"><span data-stu-id="705e5-147">Camel</span></span>|<span data-ttu-id="705e5-148">not</span><span class="sxs-lookup"><span data-stu-id="705e5-148">Not</span></span>|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a><span data-ttu-id="705e5-149">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="705e5-149">Case Sensitivity</span></span>

 <span data-ttu-id="705e5-150">CLR에서 실행할 수 있는 언어는 대/소문자 구분을 지 원하는 데 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="705e5-151">언어가 지 원하는 경우에도 프레임 워크에 액세스할 수 있는 다른 언어는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="705e5-152">따라서 외부에서 액세스할 수 있는 모든 Api는 사례를 단독으로 사용 하 여 동일한 컨텍스트에서 두 이름을 구분할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="705e5-153">❌ 모든 프로그래밍 언어가 대/소문자를 구분 한다고 가정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="705e5-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="705e5-154">그러나 동일하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-154">They are not.</span></span> <span data-ttu-id="705e5-155">이름은 대/소문자만 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="705e5-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="705e5-156">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="705e5-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="705e5-157">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="705e5-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="705e5-158">참조</span><span class="sxs-lookup"><span data-stu-id="705e5-158">See also</span></span>

- [<span data-ttu-id="705e5-159">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="705e5-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="705e5-160">명명 지침</span><span class="sxs-lookup"><span data-stu-id="705e5-160">Naming Guidelines</span></span>](naming-guidelines.md)
