---
title: '호환성이 손상되는 변경: Nullable 참조 형식 주석 변경'
description: Nullable 참조 형식 주석 변경이라는 제목이 붙은 ASP.NET Core 6.0의 호환성이 손상되는 변경에 대해 알아봅니다.
author: scottaddie
ms.author: scaddie
ms.date: 02/16/2021
ms.openlocfilehash: 6277b57e0340d099d11ddf2e955ab1fc969e3270
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643587"
---
# <a name="nullable-reference-type-annotations-changed"></a><span data-ttu-id="4559f-103">Nullable 참조 형식 주석 변경</span><span class="sxs-lookup"><span data-stu-id="4559f-103">Nullable reference type annotations changed</span></span>

<span data-ttu-id="4559f-104">**이 문제는 진행 중인 작업을 나타냅니다. Null 허용 여부 주석에 대한 호환성이 손상되는 변경은 ASP.NET Core 6.0 과정에서 모두 이 문제로 집계됩니다.**</span><span class="sxs-lookup"><span data-stu-id="4559f-104">_**This issue represents a work-in-progress. All breaking changes to nullability annotations will be aggregated into this issue throughout the course of ASP.NET Core 6.0.**_</span></span>

<span data-ttu-id="4559f-105">ASP.NET Core 5.0부터 Null 허용 여부 주석이 코드의 일부에 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-105">Starting in ASP.NET Core 5.0, nullability annotations have been applied to parts of the code.</span></span> <span data-ttu-id="4559f-106">이 작업의 처음부터 이러한 주석에 [실수가 발생할 것이 예상되었으며](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/api-guidelines/nullability.md#breaking-change-guidance) 수정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-106">From the outset of this effort, [mistakes were expected](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/api-guidelines/nullability.md#breaking-change-guidance) in these annotations and fixes would need to be made.</span></span> <span data-ttu-id="4559f-107">ASP.NET Core 6.0에서 이전에 적용한 일부 주석을 업데이트하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-107">In ASP.NET Core 6.0, some previously applied annotations are being updated.</span></span> <span data-ttu-id="4559f-108">이러한 변경 내용 중 일부는 원본 호환성이 손상되는 변경으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-108">Some of these changes are considered source breaking changes.</span></span> <span data-ttu-id="4559f-109">이러한 변경으로 인해 API가 호환되지 않거나 추가적인 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-109">The changes lead to the APIs being incompatible or more restrictive.</span></span> <span data-ttu-id="4559f-110">Nullable 참조 유형을 사용 설정한 프로젝트에서 업데이트된 API를 사용할 경우 빌드 시간 경고가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-110">The updated APIs may result in build-time warnings when used in projects that have nullable reference types enabled.</span></span>

<span data-ttu-id="4559f-111">자세한 내용은 GitHub 이슈 [dotnet/aspnetcore#27564](https://github.com/dotnet/aspnetcore/issues/27564)를 참고하세요.</span><span class="sxs-lookup"><span data-stu-id="4559f-111">For discussion, see GitHub issue [dotnet/aspnetcore#27564](https://github.com/dotnet/aspnetcore/issues/27564).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4559f-112">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="4559f-112">Version introduced</span></span>

<span data-ttu-id="4559f-113">6.0</span><span class="sxs-lookup"><span data-stu-id="4559f-113">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="4559f-114">이전 동작</span><span class="sxs-lookup"><span data-stu-id="4559f-114">Old behavior</span></span>

<span data-ttu-id="4559f-115">영향을 받는 API에 잘못된 Nullable 참조 유형 주석이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-115">The affected APIs have incorrect nullable reference type annotations.</span></span> <span data-ttu-id="4559f-116">빌드 경고가 없거나 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-116">Build warnings are either absent or incorrect.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="4559f-117">새 동작</span><span class="sxs-lookup"><span data-stu-id="4559f-117">New behavior</span></span>

<span data-ttu-id="4559f-118">새 빌드 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-118">New build warnings are produced.</span></span> <span data-ttu-id="4559f-119">영향을 받는 API에 대해 잘못된 빌드 경고가 더 이상 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-119">Incorrect build warnings are no longer produced for the affected APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4559f-120">변경 이유</span><span class="sxs-lookup"><span data-stu-id="4559f-120">Reason for change</span></span>

<span data-ttu-id="4559f-121">피드백 및 추가 테스트를 통해 영향을 받는 API의 nullable 주석은 부정확한 것으로 확인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-121">Through feedback and further testing, the nullable annotations for the affected APIs were determined to be inaccurate.</span></span> <span data-ttu-id="4559f-122">업데이트된 주석에 API의 Null 허용 여부 계약이 이제 올바르게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-122">The updated annotations now correctly represent the nullability contracts for the APIs.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4559f-123">권장 조치</span><span class="sxs-lookup"><span data-stu-id="4559f-123">Recommended action</span></span>

<span data-ttu-id="4559f-124">수정된 Null 허용 여부 계약을 반영하도록 API 호출 코드를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4559f-124">Update code calling these APIs to reflect the revised nullability contracts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4559f-125">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="4559f-125">Affected APIs</span></span>

* <xref:Microsoft.AspNetCore.Components.ParameterView.FromDictionary%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Components.RenderTree.Renderer.DispatchEventAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeEdit.RemovedAttributeName?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector%2A?displayProperty=nameWithType>
* <xref:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.RequestDelegate%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.Cookies.ITicketStore.RetrieveAsync%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%60%601?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%60%601(%60%600)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%60%601(%60%600)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.SetModelValue(System.String,System.Object,System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.Item(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.Validator%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Http.Endpoint.%23ctor%2A?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd(System.String,System.Object)?displayProperty=nameWithType>>
* <xref:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%60%601(%60%600,Microsoft.AspNetCore.Routing.RouteValueDictionary,System.String,Microsoft.AspNetCore.Http.HostString,Microsoft.AspNetCore.Http.PathString,Microsoft.AspNetCore.Http.FragmentString,Microsoft.AspNetCore.Routing.LinkOptions)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier(System.IServiceProvider)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate(System.String)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>
* <xref:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector?displayProperty=nameWithType>
* <xref:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.%23ctor(Microsoft.Net.Http.Headers.EntityTagHeaderValue)?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Components.ParameterView.FromDictionary`
- `Overload:Microsoft.AspNetCore.Components.RenderTree.Renderer.DispatchEventAsync`
- `F:Microsoft.AspNetCore.Components.RenderTree.RenderTreeEdit.RemovedAttributeName`
- `Overload:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector`
- `Overload:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.#ctor`
- `Overload:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync`
- `Overload:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator`
- `Overload:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor`
- `Overload:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository`
- `Overload:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate`
- `Overload:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier`
- `Overload:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory`
- `Overload:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey`
- `Overload:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.#ctor`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.RequestDelegate`
- `Overload:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd`
- `Overload:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress`
- `Overload:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set`
- `Overload:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set`
- `Overload:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get`
- `Overload:Microsoft.AspNetCore.Authentication.Cookies.ITicketStore.RetrieveAsync`
- `M:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Get%60%601`
- `M:Microsoft.AspNetCore.Http.Features.IFeatureCollection.Set%60%601(%60%600)`
- `M:Microsoft.AspNetCore.Http.Features.FeatureCollection.Set%60%601(%60%600)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.SetModelValue(System.String,System.Object,System.String)`
- `P:Microsoft.AspNetCore.Mvc.ModelBinding.ModelStateDictionary.Item(System.String)`
- `Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.#ctor`
- `Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ClientValidatorItem.Validator`
- `Overload:Microsoft.AspNetCore.Http.Endpoint.#ctor`
- `M:Microsoft.AspNetCore.Routing.RouteValueDictionary.TryAdd(System.String,System.Object)`
- `M:Microsoft.AspNetCore.Routing.LinkGenerator.GetUriByAddress%60%601(%60%600,Microsoft.AspNetCore.Routing.RouteValueDictionary,System.String,Microsoft.AspNetCore.Http.HostString,Microsoft.AspNetCore.Http.PathString,Microsoft.AspNetCore.Http.FragmentString,Microsoft.AspNetCore.Routing.LinkOptions)`
- `P:Microsoft.AspNetCore.DataProtection.Infrastructure.IApplicationDiscriminator.Discriminator`
- `P:Microsoft.AspNetCore.DataProtection.DataProtectionOptions.ApplicationDiscriminator`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.AuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngCbcAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.CngGcmAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.IAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.AuthenticatedEncryption.ManagedAuthenticatedEncryptorFactory.CreateEncryptorInstance(Microsoft.AspNetCore.DataProtection.KeyManagement.IKey)`
- `M:Microsoft.AspNetCore.DataProtection.KeyManagement.IKey.CreateEncryptor`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.AuthenticatedEncryptorConfiguration`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlEncryptor`
- `P:Microsoft.AspNetCore.DataProtection.KeyManagement.KeyManagementOptions.XmlRepository`
- `M:Microsoft.AspNetCore.DataProtection.XmlEncryption.ICertificateResolver.ResolveCertificate(System.String)`
- `M:Microsoft.AspNetCore.DataProtection.DataProtectionUtilityExtensions.GetApplicationUniqueIdentifier(System.IServiceProvider)`
- `P:Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository.DefaultKeyStorageDirectory`
- `P:Microsoft.AspNetCore.DataProtection.Repositories.RegistryXmlRepository.DefaultRegistryKey`
- `M:Microsoft.AspNetCore.DataProtection.XmlEncryption.CertificateResolver.ResolveCertificate(System.String)`
- `M:Microsoft.AspNetCore.Connections.IConnectionListener.AcceptAsync(System.Threading.CancellationToken)`
- `P:Microsoft.AspNetCore.Authentication.AuthenticationSchemeOptions.ForwardDefaultSelector`
- `M:Microsoft.Net.Http.Headers.RangeConditionHeaderValue.#ctor(Microsoft.Net.Http.Headers.EntityTagHeaderValue)`

-->
