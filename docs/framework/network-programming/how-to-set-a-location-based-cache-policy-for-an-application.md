---
title: '방법: 애플리케이션에 대해 위치 기반 캐시 정책 설정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 7331845c391265d72d3025fd9bf7856d83c783e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253494"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="2978c-102">방법: 애플리케이션에 대해 위치 기반 캐시 정책 설정</span><span class="sxs-lookup"><span data-stu-id="2978c-102">How to: Set a Location-Based Cache Policy for an Application</span></span>

<span data-ttu-id="2978c-103">위치 기반 캐시 정책을 사용하면 애플리케이션이 요청된 리소스의 위치를 기반으로 캐싱 동작을 명시적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="2978c-104">이 항목에서는 캐시 정책을 프로그래밍 방식으로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="2978c-105">구성 파일을 사용하여 애플리케이션에 대한 정책을 설정하는 방법에 대한 자세한 내용은 [\<requestCaching> 요소(네트워크 설정)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2978c-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="2978c-106">애플리케이션에 대해 위치 기반 캐시 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="2978c-107"><xref:System.Net.Cache.RequestCachePolicy> 또는 <xref:System.Net.Cache.HttpRequestCachePolicy> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="2978c-108">정책 개체를 애플리케이션 도메인의 기본값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="2978c-109">캐시에서 요청된 리소스를 가져오는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="2978c-110">캐시를 사용할 수 있으면 캐시에서 요청된 리소스를 가져오는 정책을 만듭니다. 사용할 수 없으면 캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>로 설정하여 요청을 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="2978c-111">원격 캐시를 포함하여 클라이언트와 서버 간에 캐시를 통해 요청을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="2978c-112">캐시가 리소스를 제공하지 못하도록 제한하는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="2978c-113">캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>로 설정하여 캐시가 요청된 리소스를 제공하지 못하도록 제한하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="2978c-114">이 정책 수준은 캐시가 있는 경우 로컬 캐시에서 리소스를 제거하고 원격 캐시에서도 리소스를 제거해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="2978c-115">리소스가 로컬 캐시에 있는 경우에만 요청된 리소스를 반환하는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="2978c-116">캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>로 설정하여 리소스가 로컬 캐시에 있는 경우에만 요청된 리소스를 반환하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="2978c-117">요청된 리소스가 캐시에 없으면 <xref:System.Net.WebException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="2978c-118">로컬 캐시가 리소스를 제공하지 못하도록 제한하는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="2978c-119">캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>로 설정하여 로컬 캐시가 요청된 리소스를 제공하지 못하도록 제한하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="2978c-120">요청된 리소스가 중간 캐시에 있고 성공적으로 유효성이 다시 검증된 경우 중간 캐시는 요청된 리소스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="2978c-121">캐시가 요청된 리소스를 제공하지 못하도록 제한하는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="2978c-122">캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>로 설정하여 캐시가 요청된 리소스를 제공하지 못하도록 제한하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="2978c-123">서버에서 반환된 리소스를 캐시에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="2978c-124">서버의 리소스가 캐시된 복사본보다 최신 버전이 아닐 경우 캐시가 요청된 리소스를 제공하도록 허용하는 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2978c-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="2978c-125">캐시 수준을 <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>로 설정하여 서버의 리소스가 캐시된 복사본보다 최신 버전이 아닐 경우 캐시가 요청된 리소스를 제공하도록 허용하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2978c-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2978c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2978c-126">See also</span></span>

- [<span data-ttu-id="2978c-127">네트워크 애플리케이션에 대한 캐시 관리</span><span class="sxs-lookup"><span data-stu-id="2978c-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="2978c-128">캐시 정책</span><span class="sxs-lookup"><span data-stu-id="2978c-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="2978c-129">위치 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="2978c-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="2978c-130">시간 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="2978c-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="2978c-131">\<requestCaching> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="2978c-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
