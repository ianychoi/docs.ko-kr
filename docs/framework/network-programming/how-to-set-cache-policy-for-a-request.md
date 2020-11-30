---
title: '방법: 요청에 캐시 정책 설정'
description: .NET Framework의 요청에 대한 캐시 정책을 설정하는 방법을 알아봅니다. 이 캐시 정책에 따라, 최대 하루 동안 캐시에서 리소스를 사용할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
ms.openlocfilehash: cbb8f2eaf618cb9faaca1375d829478a645962a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253416"
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="00303-104">방법: 요청에 캐시 정책 설정</span><span class="sxs-lookup"><span data-stu-id="00303-104">How to: Set Cache Policy for a Request</span></span>

<span data-ttu-id="00303-105">다음 예제에서는 요청에 대한 캐시 정책을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00303-105">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="00303-106">예제 입력은 `http://www.contoso.com/` 등의 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="00303-106">The example input is a URI such as `http://www.contoso.com/`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00303-107">예제</span><span class="sxs-lookup"><span data-stu-id="00303-107">Example</span></span>  

 <span data-ttu-id="00303-108">다음 코드 예제에서는 리소스가 캐시에 포함된 기간이 하루를 초과하지 않으면 캐시에서 요청된 리소스를 사용하도록 허용하는 캐시 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="00303-108">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="00303-109">예제에서는 리소스가 캐시에서 사용되었는지 여부를 나타내는 메시지(예: `"The response was retrieved from the cache : False."`)를 표시하고 나서 리소스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="00303-109">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="00303-110">클라이언트와 서버 간에 캐시를 통해 요청을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00303-110">A request can be fulfilled by any cache between the client and server.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Cache;  
using System.IO;  
  
namespace Examples.System.Net.Cache  
{  
    public class CacheExample  
    {
        public static void UseCacheForOneDay(Uri resource)  
        {  
            // Create a policy that allows items in the cache  
            // to be used if they have been cached one day or less.  
            HttpRequestCachePolicy requestPolicy =
                new HttpRequestCachePolicy (HttpCacheAgeControl.MaxAge,  
                TimeSpan.FromDays(1));  
  
            WebRequest request = WebRequest.Create (resource);  
            // Set the policy for this request only.  
            request.CachePolicy = requestPolicy;  
            HttpWebResponse response = (HttpWebResponse)request.GetResponse();  
            // Determine whether the response was retrieved from the cache.  
            Console.WriteLine ("The response was retrieved from the cache : {0}.",  
               response.IsFromCache);  
            Stream s = response.GetResponseStream ();  
            StreamReader reader = new StreamReader (s);  
            // Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd());  
            reader.Close ();  
            s.Close();  
            response.Close();  
        }  
        public static void Main(string[] args)  
        {  
            if (args == null || args.Length != 1)  
            {  
                Console.WriteLine ("You must specify the URI to retrieve.");  
                return;  
            }  
            UseCacheForOneDay (new Uri(args[0]));  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Cache  
Imports System.IO  
Namespace Examples.System.Net.Cache  
    Public Class CacheExample  
        Public Shared Sub UseCacheForOneDay(ByVal resource As Uri)  
            ' Create a policy that allows items in the cache  
            ' to be used if they have been cached one day or less.  
            Dim requestPolicy As New HttpRequestCachePolicy _  
                  (HttpCacheAgeControl.MaxAge, TimeSpan.FromDays(1))  
            Dim request As WebRequest = WebRequest.Create(resource)  
            ' Set the policy for this request only.  
            request.CachePolicy = requestPolicy  
            Dim response As HttpWebResponse = _  
             CType(request.GetResponse(), HttpWebResponse)  
            ' Determine whether the response was retrieved from the cache.  
            Console.WriteLine("The response was retrieved from the cache : {0}.", _  
                response.IsFromCache)  
            Dim s As Stream = response.GetResponseStream()  
            Dim reader As New StreamReader(s)  
            ' Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd())  
            reader.Close()  
            s.Close()  
            response.Close()  
        End Sub  
        Public Shared Sub Main(ByVal args() As String)  
            If args Is Nothing OrElse args.Length <> 1 Then  
                Console.WriteLine("You must specify the URI to retrieve.")  
                Return  
            End If  
            UseCacheForOneDay(New Uri(args(0)))  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="00303-111">참조</span><span class="sxs-lookup"><span data-stu-id="00303-111">See also</span></span>

- [<span data-ttu-id="00303-112">네트워크 애플리케이션에 대한 캐시 관리</span><span class="sxs-lookup"><span data-stu-id="00303-112">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="00303-113">캐시 정책</span><span class="sxs-lookup"><span data-stu-id="00303-113">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="00303-114">위치 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="00303-114">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="00303-115">시간 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="00303-115">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="00303-116">\<requestCaching> 요소(네트워크 설정)</span><span class="sxs-lookup"><span data-stu-id="00303-116">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
