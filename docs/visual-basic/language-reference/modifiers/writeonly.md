---
description: '자세히 알아보기: WriteOnly (Visual Basic)'
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 514a1de3c8c2cfbde6a9cffc5c235d92454dd966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674742"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="c3e61-103">WriteOnly(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3e61-103">WriteOnly (Visual Basic)</span></span>

<span data-ttu-id="c3e61-104">속성을 쓸 수 있지만 읽을 수 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-104">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3e61-105">설명</span><span class="sxs-lookup"><span data-stu-id="c3e61-105">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c3e61-106">규칙</span><span class="sxs-lookup"><span data-stu-id="c3e61-106">Rules</span></span>  

 <span data-ttu-id="c3e61-107">**선언 컨텍스트.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-107">**Declaration Context.**</span></span> <span data-ttu-id="c3e61-108">`WriteOnly`는 모듈 수준에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-108">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="c3e61-109">즉, 속성에 대 한 선언 컨텍스트는 `WriteOnly` 클래스, 구조체 또는 모듈 이어야 하며 소스 파일, 네임 스페이스 또는 프로시저일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-109">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="c3e61-110">속성은 선언할 수 `WriteOnly` 있지만 변수는 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-110">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="c3e61-111">WriteOnly를 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="c3e61-111">When to Use WriteOnly</span></span>  

 <span data-ttu-id="c3e61-112">소비 하는 코드에서 값을 설정할 수 있지만 해당 값을 검색 하지 않으려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-112">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="c3e61-113">예를 들어 소셜 등록 번호 또는 암호와 같은 중요 한 데이터는 해당 데이터를 설정 하지 않은 구성 요소에의 한 액세스 로부터 보호 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-113">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="c3e61-114">이 경우 속성을 사용 하 여 값을 설정할 수 있습니다 `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="c3e61-114">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3e61-115">속성을 정의 하 고 사용 하는 경우 `WriteOnly` 다음과 같은 추가 보호 조치를 고려 하십시오.</span><span class="sxs-lookup"><span data-stu-id="c3e61-115">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="c3e61-116">**덮어쓰지.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-116">**Overriding.**</span></span> <span data-ttu-id="c3e61-117">속성이 클래스의 멤버인 경우 [NotOverridable](notoverridable.md)에 대 한 기본값을 지정할 수 있으며, 또는로 선언 하지 않습니다 `Overridable` `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="c3e61-117">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="c3e61-118">이렇게 하면 파생 클래스가 재정의를 통해 원치 않는 액세스를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-118">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="c3e61-119">**액세스 수준입니다.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-119">**Access Level.**</span></span> <span data-ttu-id="c3e61-120">하나 이상의 변수에 속성의 중요 한 데이터를 저장 하는 경우 다른 코드에서 액세스할 수 없도록 [Private](private.md) 을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-120">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="c3e61-121">**암호화.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-121">**Encryption.**</span></span> <span data-ttu-id="c3e61-122">모든 중요 한 데이터를 일반 텍스트가 아닌 암호화 된 형식으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-122">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="c3e61-123">악의적인 코드가 해당 메모리 영역에 대 한 액세스 권한을 얻으면 데이터를 사용 하는 것이 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-123">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="c3e61-124">암호화는 중요 한 데이터를 직렬화 해야 하는 경우에도 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-124">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="c3e61-125">**다시 설정.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-125">**Resetting.**</span></span> <span data-ttu-id="c3e61-126">속성을 정의 하는 클래스, 구조체 또는 모듈을 종료 하는 경우 중요 한 데이터를 기본값으로 다시 설정 하거나 다른 의미 없는 값으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-126">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="c3e61-127">이는 일반 액세스를 위해 메모리 영역을 해제할 때 추가 보호 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-127">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="c3e61-128">**지.**</span><span class="sxs-lookup"><span data-stu-id="c3e61-128">**Persistence.**</span></span> <span data-ttu-id="c3e61-129">중요 한 데이터 (예: 디스크를 사용 하지 않는 경우)를 유지 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c3e61-129">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="c3e61-130">또한 중요 한 데이터를 클립보드에 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-130">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="c3e61-131">`WriteOnly`이 컨텍스트에서는 한정자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3e61-131">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="c3e61-132">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c3e61-132">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3e61-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3e61-133">See also</span></span>

- [<span data-ttu-id="c3e61-134">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="c3e61-134">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="c3e61-135">개인</span><span class="sxs-lookup"><span data-stu-id="c3e61-135">Private</span></span>](private.md)
- [<span data-ttu-id="c3e61-136">C++ 키워드</span><span class="sxs-lookup"><span data-stu-id="c3e61-136">Keywords</span></span>](../keywords/index.md)
