---
description: '자세한 정보: Microsoft.Win32 네임스페이스를 사용하여 레지스트리 읽기 및 쓰기(Visual Basic)'
title: Microsoft.Win32 네임스페이스를 사용하여 레지스트리 읽기 및 쓰기
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: beb81a6385043011a37eee82f2036aca91382240
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701588"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="d6124-103">Microsoft.Win32 네임스페이스를 사용하여 레지스트리 읽기 및 쓰기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6124-103">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="d6124-104">`My.Computer.Registry`는 레지스트리에 대해 프로그래밍할 때 기본 요구 사항을 충족해야 하지만, .NET의 <xref:Microsoft.Win32> 네임스페이스에서 <xref:Microsoft.Win32.Registry> 및 <xref:Microsoft.Win32.RegistryKey> 클래스를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-104">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of .NET.</span></span>
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="d6124-105">레지스트리 클래스의 키</span><span class="sxs-lookup"><span data-stu-id="d6124-105">Keys in the Registry Class</span></span>  

 <span data-ttu-id="d6124-106"><xref:Microsoft.Win32.Registry> 클래스는 하위 키 및 값에 액세스하기 위해 사용할 수 있는 기본 레지스트리 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-106">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="d6124-107">기본 키 자체는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-107">The base keys themselves are read-only.</span></span> <span data-ttu-id="d6124-108">다음 표에서는 <xref:Microsoft.Win32.Registry> 클래스에서 사용되는 7개의 키를 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-108">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="d6124-109">**키**</span><span class="sxs-lookup"><span data-stu-id="d6124-109">**Key**</span></span>|<span data-ttu-id="d6124-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="d6124-110">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="d6124-111">문서의 형식 및 그러한 형식과 관련된 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-111">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="d6124-112">사용자와 관련되지 않은 하드웨어 구성 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-112">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="d6124-113">현재 사용자 기본 설정(예: 환경 변수)에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-113">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="d6124-114">가상 디바이스 드라이버에서 사용하는 것과 같은 동적 레지스트리 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-114">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="d6124-115">로컬 컴퓨터에 대한 구성 데이터를 유지하는 5개의 하위 키(하드웨어, SAM, 보안, 소프트웨어 및 시스템)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-115">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="d6124-116">소프트웨어 구성 요소에 대한 성능 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-116">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="d6124-117">기본 사용자 기본 설정에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-117">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="d6124-118">로컬 컴퓨터(<xref:Microsoft.Win32.Registry.LocalMachine>)보다 현재 사용자(<xref:Microsoft.Win32.Registry.CurrentUser>)에게 데이터를 기록하는 것이 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-118">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="d6124-119">만들고 있는 키가 전에 다른 프로세스(예: 악의적인 프로세스)로 만들어진 경우 일반적으로 "스쿼팅(squatting)"이라는 조건이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-119">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="d6124-120">이 문제가 발생하지 않도록 하려면 키가 존재하지 않을 경우 `Nothing`을 반환하는 메서드(예: <xref:Microsoft.Win32.RegistryKey.GetValue%2A>)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-120">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="d6124-121">레지스트리에서 값 읽기</span><span class="sxs-lookup"><span data-stu-id="d6124-121">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="d6124-122">다음 코드는 HKEY_CURRENT_USER에서 문자열을 읽는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-122">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="d6124-123">다음 코드는 문자열을 읽고, 늘리고, HKEY_CURRENT_USER에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="d6124-123">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d6124-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6124-124">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="d6124-125">Try...Catch...Finally 문</span><span class="sxs-lookup"><span data-stu-id="d6124-125">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="d6124-126">레지스트리 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="d6124-126">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="d6124-127">보안 및 레지스트리</span><span class="sxs-lookup"><span data-stu-id="d6124-127">Security and the Registry</span></span>](security-and-the-registry.md)
