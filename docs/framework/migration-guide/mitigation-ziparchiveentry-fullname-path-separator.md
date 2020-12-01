---
title: '완화: ZipArchiveEntry.FullName 경로 구분 기호'
description: ZipArchiveEntry.FullName의 경로 구분 기호가 .NET Framework 4.6.1을 대상으로 하는 앱부터 변경되는 방식을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283447"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="e3cd7-103">완화: ZipArchiveEntry.FullName 경로 구분 기호</span><span class="sxs-lookup"><span data-stu-id="e3cd7-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="e3cd7-104">.NET Framework 4.6.1을 대상으로 하는 앱부터 <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> 속성에 사용되는 경로 구분 기호가 이전 버전의 .NET Framework에서 사용된 백슬래시("\\")에서 슬래시("/")로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="e3cd7-105"><xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> 메서드의 오버로드 중 하나를 호출하여 <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e3cd7-106">영향</span><span class="sxs-lookup"><span data-stu-id="e3cd7-106">Impact</span></span>  

 <span data-ttu-id="e3cd7-107">이 변경으로 인해 .NET 구현은 [.ZIP 파일 형식 사양](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)의 섹션 4.4.17.1과 일치하게 되고 비 Windows 시스템에서.ZIP 아카이브의 압축이 풀리게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="e3cd7-108">MacOS와 같은 비 Windows 운영 체제에서 이전 버전의 .NET Framework를 대상으로 하는 앱이 만든 zip 파일의 압축을 풀면 디렉터리 구조가 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="e3cd7-109">예를 들어 MacOS에서는 해당 파일 이름이 디렉터리 경로, 백슬래시("\\") 문자 및 파일 이름을 연결하는 파일 세트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="e3cd7-110">결과적으로 압축을 푼 파일의 디렉터리 구조는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="e3cd7-111">.NET Framework <xref:System.IO> 네임스페이스의 API는 슬래시("/") 또는 백슬래시("\\")를 경로 구분 기호 문자로 원활하게 처리할 수 있으므로 이러한 API에 의해 Windows 운영 체제에서 압축 해제된 .ZIP 파일에 이러한 변경이 미치는 영향은 최소로 유지될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e3cd7-112">완화</span><span class="sxs-lookup"><span data-stu-id="e3cd7-112">Mitigation</span></span>  

 <span data-ttu-id="e3cd7-113">이 동작을 원치 않을 경우 애플리케이션 구성 파일의 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 섹션에 구성 설정을 추가하여 옵트아웃(opt out)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="e3cd7-114">다음에서는 `<runtime>` 섹션 및 옵트아웃 스위치를 둘 다 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="e3cd7-115">또한 이전 버전의 .NET Framework를 대상으로 하지만 .NET Framework 4.6.1 이상 버전에서 실행되는 앱은 애플리케이션 구성 파일의 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 섹션에 구성 설정을 추가하여 이 동작을 옵트인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="e3cd7-116">다음에서는 `<runtime>` 섹션 및 옵트인 스위치를 둘 다 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e3cd7-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3cd7-117">참조</span><span class="sxs-lookup"><span data-stu-id="e3cd7-117">See also</span></span>

- [<span data-ttu-id="e3cd7-118">애플리케이션 호환성</span><span class="sxs-lookup"><span data-stu-id="e3cd7-118">Application compatibility</span></span>](application-compatibility.md)
