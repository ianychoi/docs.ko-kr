---
description: '자세한 정보: 방법: Visual Basic에서 레지스트리 키 값 읽기'
title: '방법: 레지스트리 키에서 값 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: e062e40fe1c8876864e633079fc22e2c83cfb5d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797681"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="21022-103">방법: Visual Basic에서 레지스트리 키 값 읽기</span><span class="sxs-lookup"><span data-stu-id="21022-103">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="21022-104">`My.Computer.Registry` 개체의 `GetValue` 메서드를 사용하여 Windows 레지스트리의 값을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-104">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="21022-105">다음 예제의 "Software\MyApp" 키가 없으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="21022-105">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="21022-106">`ValueName`(다음 예제의 "Name")이 없으면 `Nothing`이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="21022-106">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="21022-107">`GetValue` 메서드를 사용하여 지정된 값이 특정 레지스트리 키에 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-107">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="21022-108">코드가 웹 애플리케이션에서 레지스트리를 읽는 경우 현재 사용자는 웹 애플리케이션에 구현된 인증 및 가장에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="21022-108">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="21022-109">레지스트리 키에서 값을 읽으려면</span><span class="sxs-lookup"><span data-stu-id="21022-109">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="21022-110">`GetValue` 메서드를 사용하고 경로 및 이름을 지정하여 레지스트리 키에서 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-110">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="21022-111">다음 예제에서는 `HKEY_CURRENT_USER\Software\MyApp`에서 `Name` 값을 읽고 메시지 상자에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-111">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="21022-112">이 코드 예제는 IntelliSense 코드 조각으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-112">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="21022-113">코드 조각 선택에서 **Windows 운영 체제 > 레지스트리** 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-113">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="21022-114">자세한 내용은 [코드 조각](/visualstudio/ide/code-snippets)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21022-114">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="21022-115">레지스트리 키에 값이 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="21022-115">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="21022-116">`GetValue` 메서드를 사용하여 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-116">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="21022-117">다음 코드는 값이 있는지 확인하고, 값이 없는 경우 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-117">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="21022-118">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="21022-118">Robust Programming</span></span>  

 <span data-ttu-id="21022-119">레지스트리는 데이터를 저장하는 데 사용되는 최상위 또는 루트 키를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-119">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="21022-120">예를 들어 HKEY_LOCAL_MACHINE 루트 키는 모든 사용자가 사용하는 컴퓨터 수준 설정을 저장하는 데 사용되고, HKEY_CURRENT_USER는 개별 사용자와 관련된 데이터를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21022-120">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="21022-121">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-121">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="21022-122">키의 이름이 `Nothing`인 경우(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="21022-122">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="21022-123">사용자에게 레지스트리 키에서 읽을 수 있는 권한이 없는 경우(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="21022-123">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="21022-124">키 이름이 255자 제한을 초과하는 경우(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="21022-124">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="21022-125">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="21022-125">.NET Framework Security</span></span>  

 <span data-ttu-id="21022-126">이 프로세스를 실행하려면 어셈블리에 <xref:System.Security.Permissions.RegistryPermission> 클래스에서 부여한 권한 수준이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-126">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="21022-127">부분 신뢰 컨텍스트에서 실행하는 경우 프로세스가 권한 부족으로 인해 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-127">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="21022-128">마찬가지로, 사용자에게 설정을 만들거나 쓸 수 있는 올바른 ACL이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21022-128">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="21022-129">예를 들어 코드 액세스 보안 권한이 있는 로컬 애플리케이션에는 운영 체제 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21022-129">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="21022-130">자세한 내용은 [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21022-130">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21022-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21022-131">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="21022-132">레지스트리 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="21022-132">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
