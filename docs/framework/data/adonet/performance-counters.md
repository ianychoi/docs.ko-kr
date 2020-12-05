---
title: 성능 카운터
description: ADO.NET 성능 카운터를 사용 하 여 Windows 성능 모니터를 사용 하거나 프로그래밍 방식으로 응용 프로그램 상태 및 해당 연결 리소스를 모니터링할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: dca259ef6d8a2229349d88a9fcae3298cb8a829c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739466"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="17899-103">성능 카운터(ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="17899-103">Performance Counters in ADO.NET</span></span>

<span data-ttu-id="17899-104">ADO.NET 2.0에는 <xref:System.Data.SqlClient> 및 <xref:System.Data.OracleClient>를 모두 지원하는 성능 카운터에 대한 확장된 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="17899-105">이전 버전의 ADO.NET에서 사용 가능한 <xref:System.Data.SqlClient> 성능 카운터는 더 이상 사용되지 않는 대신 이 항목에 설명할 새 성능 카운터로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="17899-106">ADO.NET 성능 카운터를 사용하여 애플리케이션 상태와 애플리케이션에서 사용하는 연결 리소스를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="17899-107">성능 카운터는 Windows 성능 카운터를 사용하여 모니터링하거나 <xref:System.Diagnostics.PerformanceCounter> 네임스페이스의 <xref:System.Diagnostics> 클래스를 사용하여 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>

## <a name="available-performance-counters"></a><span data-ttu-id="17899-108">사용 가능한 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="17899-108">Available Performance Counters</span></span>

 <span data-ttu-id="17899-109"><xref:System.Data.SqlClient> 및 <xref:System.Data.OracleClient> 에서 사용 가능한 성능 카운터는 현재 14가지가 있으며 다음 표에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="17899-110">개별 카운터 이름은 Microsoft .NET Framework의 국가별 버전에서 지역화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>

|<span data-ttu-id="17899-111">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="17899-111">Performance counter</span></span>|<span data-ttu-id="17899-112">Description</span><span class="sxs-lookup"><span data-stu-id="17899-112">Description</span></span>|
|-------------------------|-----------------|
|`HardConnectsPerSecond`|<span data-ttu-id="17899-113">데이터베이스 서버에 대한 초당 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-113">The number of connections per second that are being made to a database server.</span></span>|
|`HardDisconnectsPerSecond`|<span data-ttu-id="17899-114">데이터베이스 서버에 대한 초당 끊긴 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-114">The number of disconnects per second that are being made to a database server.</span></span>|
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="17899-115">활성화되어 있는 고유 연결 풀 그룹 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="17899-116">이 카운터는 AppDomain에 있는 고유 연결 문자열 수에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="17899-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|
|`NumberOfActiveConnectionPools`|<span data-ttu-id="17899-117">연결 풀의 총 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-117">The total number of connection pools.</span></span>|
|`NumberOfActiveConnections`|<span data-ttu-id="17899-118">현재 사용 중인 활성 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="17899-119">**참고:**  이 성능 카운터는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="17899-120">이 성능 카운터를 사용 하도록 설정 하려면 [기본적으로 활성화 되지 않은 카운터 활성화](#ActivatingOffByDefault)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17899-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|
|`NumberOfFreeConnections`|<span data-ttu-id="17899-121">연결 풀에서 사용할 수 있는 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="17899-122">**참고:**  이 성능 카운터는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="17899-123">이 성능 카운터를 사용 하도록 설정 하려면 [기본적으로 활성화 되지 않은 카운터 활성화](#ActivatingOffByDefault)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17899-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="17899-124">정리하기로 표시된 고유 연결 풀 그룹 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="17899-125">이 카운터는 AppDomain에 있는 고유 연결 문자열 수에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="17899-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="17899-126">최근 활성화되지 않았고 삭제 대기 중인 비활성 연결 풀 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|
|`NumberOfNonPooledConnections`|<span data-ttu-id="17899-127">풀링되지 않은 활성 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-127">The number of active connections that are not pooled.</span></span>|
|`NumberOfPooledConnections`|<span data-ttu-id="17899-128">연결 풀링 인프라에서 관리되는 활성 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|
|`NumberOfReclaimedConnections`|<span data-ttu-id="17899-129">애플리케이션에서 `Close` 또는 `Dispose`를 호출하지 않은 가비지 수집에서 회수된 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="17899-130">연결을 명시적으로 닫거나 삭제하는 것이 성능을 항상 저하시키는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="17899-130">Not explicitly closing or disposing connections hurts performance.</span></span>|
|`NumberOfStasisConnections`|<span data-ttu-id="17899-131">현재 작업 완료 대기 중이어서 사용자 애플리케이션에서 사용할 수 없는 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|
|`SoftConnectsPerSecond`|<span data-ttu-id="17899-132">연결 풀에서 풀링되는 활성 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="17899-133">**참고:**  이 성능 카운터는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="17899-134">이 성능 카운터를 사용 하도록 설정 하려면 [기본적으로 활성화 되지 않은 카운터 활성화](#ActivatingOffByDefault)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17899-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|
|`SoftDisconnectsPerSecond`|<span data-ttu-id="17899-135">연결 풀로 반환되는 활성 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="17899-136">**참고:**  이 성능 카운터는 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="17899-137">이 성능 카운터를 사용 하도록 설정 하려면 [기본적으로 활성화 되지 않은 카운터 활성화](#ActivatingOffByDefault)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="17899-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|

### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="17899-138">연결 풀 그룹 및 연결 풀</span><span class="sxs-lookup"><span data-stu-id="17899-138">Connection Pool Groups and Connection Pools</span></span>

 <span data-ttu-id="17899-139">Windows 인증(통합 보안)을 사용할 때 `NumberOfActiveConnectionPoolGroups` 및 `NumberOfActiveConnectionPools` 성능 카운터를 모두 모니터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17899-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="17899-140">이와 같이 해야 하는 이유는 연결 풀 그룹은 고유 연결 문자열에 매핑되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="17899-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="17899-141">통합 보안이 사용되면 연결 풀이 연결 문자열에 매핑되며 개별 Windows ID에 대한 별도의 풀이 추가적으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="17899-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="17899-142">예를 들어, 동일한 AppDomain 내에서 Fred와 Julie가 모두 연결 문자열 `"Data Source=MySqlServer;Integrated Security=true"`를 사용하는 경우 연결 문자열에 대해 연결 풀 그룹이 만들어지며 Fred와 Julie에 대해 각각 하나씩 두 개의 추가 풀이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="17899-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="17899-143">John과 Martha가 동일한 SQL Server 로그인을 사용 하는 연결 문자열을 사용 하는 경우 `"Data Source=MySqlServer;User Id=lowPrivUser;Password=[PLACEHOLDER]"` **lowPrivUser** id에 대해 하나의 풀만 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="17899-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=[PLACEHOLDER]"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>

<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a><span data-ttu-id="17899-144">기본적으로 활성화되지 않은 카운터 활성화</span><span class="sxs-lookup"><span data-stu-id="17899-144">Activating Off-By-Default Counters</span></span>

 <span data-ttu-id="17899-145">`NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond` 및 `SoftConnectsPerSecond` 성능 카운터는 기본적으로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="17899-146">다음 정보를 애플리케이션의 구성 파일에 추가하여 이러한 성능 카운터를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-146">Add the following information to the application's configuration file to enable them:</span></span>

```xml
<system.diagnostics>
  <switches>
    <add name="ConnectionPoolPerformanceCounterDetail"
         value="4"/>
  </switches>
</system.diagnostics>
```

## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="17899-147">성능 카운터 값 검색</span><span class="sxs-lookup"><span data-stu-id="17899-147">Retrieving Performance Counter Values</span></span>

 <span data-ttu-id="17899-148">다음 콘솔 애플리케이션에서는 사용자 애플리케이션에서 성능 카운터 값을 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17899-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="17899-149">모든 ADO.NET 성능 카운터에서 반환되는 정보에 대해 연결이 열려 있고 활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17899-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>

> [!NOTE]
> <span data-ttu-id="17899-150">이 예에서는 SQL Server에 포함 된 샘플 **AdventureWorks** 데이터베이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17899-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="17899-151">이 샘플 코드에 제공된 연결 문자열에서는 인스턴스 이름이 SqlExpress인 데이터베이스가 로컬 컴퓨터에 설치되어 있고 사용 가능하며 연결 문자열에 제공된 문자열과 일치하는 SQL Server 로그인을 만들었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="17899-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="17899-152">Windows 인증만 허용하는 기본 보안 설정을 사용하여 서버를 구성하는 경우 SQL Server 로그인을 활성화해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17899-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="17899-153">사용자 환경에 맞게 연결 문자열을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="17899-153">Modify the connection strings as necessary to suit your environment.</span></span>

### <a name="example"></a><span data-ttu-id="17899-154">예제</span><span class="sxs-lookup"><span data-stu-id="17899-154">Example</span></span>

```vb
Option Explicit On
Option Strict On

Imports System.Data.SqlClient
Imports System.Diagnostics
Imports System.Runtime.InteropServices

Class Program

    Private PerfCounters(9) As PerformanceCounter
    Private connection As SqlConnection = New SqlConnection

    Public Shared Sub Main()
        Dim prog As Program = New Program
        ' Open a connection and create the performance counters.
        prog.connection.ConnectionString = _
           GetIntegratedSecurityConnectionString()
        prog.SetUpPerformanceCounters()
        Console.WriteLine("Available Performance Counters:")

        ' Create the connections and display the results.
        prog.CreateConnections()
        Console.WriteLine("Press Enter to finish.")
        Console.ReadLine()
    End Sub

    Private Sub CreateConnections()
        ' List the Performance counters.
        WritePerformanceCounters()

        ' Create 4 connections and display counter information.
        Dim connection1 As SqlConnection = New SqlConnection( _
           GetIntegratedSecurityConnectionString)
        connection1.Open()
        Console.WriteLine("Opened the 1st Connection:")
        WritePerformanceCounters()

        Dim connection2 As SqlConnection = New SqlConnection( _
           GetSqlConnectionStringDifferent)
        connection2.Open()
        Console.WriteLine("Opened the 2nd Connection:")
        WritePerformanceCounters()

        Console.WriteLine("Opened the 3rd Connection:")
        Dim connection3 As SqlConnection = New SqlConnection( _
           GetSqlConnectionString)
        connection3.Open()
        WritePerformanceCounters()

        Dim connection4 As SqlConnection = New SqlConnection( _
           GetSqlConnectionString)
        connection4.Open()
        Console.WriteLine("Opened the 4th Connection:")
        WritePerformanceCounters()

        connection1.Close()
        Console.WriteLine("Closed the 1st Connection:")
        WritePerformanceCounters()

        connection2.Close()
        Console.WriteLine("Closed the 2nd Connection:")
        WritePerformanceCounters()

        connection3.Close()
        Console.WriteLine("Closed the 3rd Connection:")
        WritePerformanceCounters()

        connection4.Close()
        Console.WriteLine("Closed the 4th Connection:")
        WritePerformanceCounters()
    End Sub

    Private Enum ADO_Net_Performance_Counters
        NumberOfActiveConnectionPools
        NumberOfReclaimedConnections
        HardConnectsPerSecond
        HardDisconnectsPerSecond
        NumberOfActiveConnectionPoolGroups
        NumberOfInactiveConnectionPoolGroups
        NumberOfInactiveConnectionPools
        NumberOfNonPooledConnections
        NumberOfPooledConnections
        NumberOfStasisConnections
        ' The following performance counters are more expensive to track.
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.
        '     SoftConnectsPerSecond
        '     SoftDisconnectsPerSecond
        '     NumberOfActiveConnections
        '     NumberOfFreeConnections
    End Enum

    Private Sub SetUpPerformanceCounters()
        connection.Close()
        Me.PerfCounters(9) = New PerformanceCounter()

        Dim instanceName As String = GetInstanceName()
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)
        Dim i As Integer = 0
        Dim s As String = ""
        For Each s In [Enum].GetNames(apc)
            Me.PerfCounters(i) = New PerformanceCounter()
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"
            Me.PerfCounters(i).CounterName = s
            Me.PerfCounters(i).InstanceName = instanceName
            i = (i + 1)
        Next
    End Sub

    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer

    Private Function GetInstanceName() As String
        'This works for Winforms apps.
        Dim instanceName As String = _
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name

        ' Must replace special characters like (, ), #, /, \\
        Dim instanceName2 As String = _
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")

        'For ASP.NET applications your instanceName will be your CurrentDomain's
        'FriendlyName. Replace the line above that sets the instanceName with this:
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")

        Dim pid As String = GetCurrentProcessId.ToString
        instanceName = (instanceName + ("[" & (pid & "]")))
        Console.WriteLine("Instance Name: {0}", instanceName)
        Console.WriteLine("---------------------------")
        Return instanceName
    End Function

    Private Sub WritePerformanceCounters()
        Console.WriteLine("---------------------------")
        For Each p As PerformanceCounter In Me.PerfCounters
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)
        Next
        Console.WriteLine("---------------------------")
    End Sub

    Private Shared Function GetIntegratedSecurityConnectionString() As String
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")
    End Function

    Private Shared Function GetSqlConnectionString() As String
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=[PLACEHOLDER];" &
          "Initial Catalog=AdventureWorks")
    End Function

    Private Shared Function GetSqlConnectionStringDifferent() As String
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _
          "User Id=LowPriv;Password=[PLACEHOLDER];")
    End Function
End Class
```

```csharp
using System;
using System.Data.SqlClient;
using System.Diagnostics;
using System.Runtime.InteropServices;

class Program
{
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];
    SqlConnection connection = new SqlConnection();

    static void Main()
    {
        Program prog = new Program();
        // Open a connection and create the performance counters.
        prog.connection.ConnectionString =
           GetIntegratedSecurityConnectionString();
        prog.SetUpPerformanceCounters();
        Console.WriteLine("Available Performance Counters:");

        // Create the connections and display the results.
        prog.CreateConnections();
        Console.WriteLine("Press Enter to finish.");
        Console.ReadLine();
    }

    private void CreateConnections()
    {
        // List the Performance counters.
        WritePerformanceCounters();

        // Create 4 connections and display counter information.
        SqlConnection connection1 = new SqlConnection(
              GetIntegratedSecurityConnectionString());
        connection1.Open();
        Console.WriteLine("Opened the 1st Connection:");
        WritePerformanceCounters();

        SqlConnection connection2 = new SqlConnection(
              GetSqlConnectionStringDifferent());
        connection2.Open();
        Console.WriteLine("Opened the 2nd Connection:");
        WritePerformanceCounters();

        SqlConnection connection3 = new SqlConnection(
              GetSqlConnectionString());
        connection3.Open();
        Console.WriteLine("Opened the 3rd Connection:");
        WritePerformanceCounters();

        SqlConnection connection4 = new SqlConnection(
              GetSqlConnectionString());
        connection4.Open();
        Console.WriteLine("Opened the 4th Connection:");
        WritePerformanceCounters();

        connection1.Close();
        Console.WriteLine("Closed the 1st Connection:");
        WritePerformanceCounters();

        connection2.Close();
        Console.WriteLine("Closed the 2nd Connection:");
        WritePerformanceCounters();

        connection3.Close();
        Console.WriteLine("Closed the 3rd Connection:");
        WritePerformanceCounters();

        connection4.Close();
        Console.WriteLine("Closed the 4th Connection:");
        WritePerformanceCounters();
    }

    private enum ADO_Net_Performance_Counters
    {
        NumberOfActiveConnectionPools,
        NumberOfReclaimedConnections,
        HardConnectsPerSecond,
        HardDisconnectsPerSecond,
        NumberOfActiveConnectionPoolGroups,
        NumberOfInactiveConnectionPoolGroups,
        NumberOfInactiveConnectionPools,
        NumberOfNonPooledConnections,
        NumberOfPooledConnections,
        NumberOfStasisConnections
        // The following performance counters are more expensive to track.
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.
        //     SoftConnectsPerSecond
        //     SoftDisconnectsPerSecond
        //     NumberOfActiveConnections
        //     NumberOfFreeConnections
    }

    private void SetUpPerformanceCounters()
    {
        connection.Close();
        this.PerfCounters = new PerformanceCounter[10];
        string instanceName = GetInstanceName();
        Type apc = typeof(ADO_Net_Performance_Counters);
        int i = 0;
        foreach (string s in Enum.GetNames(apc))
        {
            this.PerfCounters[i] = new PerformanceCounter();
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";
            this.PerfCounters[i].CounterName = s;
            this.PerfCounters[i].InstanceName = instanceName;
            i++;
        }
    }

    [DllImport("kernel32.dll", SetLastError = true)]
    static extern int GetCurrentProcessId();

    private string GetInstanceName()
    {
        //This works for Winforms apps.
        string instanceName =
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;

        // Must replace special characters like (, ), #, /, \\
        string instanceName2 =
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');

        // For ASP.NET applications your instanceName will be your CurrentDomain's
        // FriendlyName. Replace the line above that sets the instanceName with this:
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');

        string pid = GetCurrentProcessId().ToString();
        instanceName = instanceName + "[" + pid + "]";
        Console.WriteLine("Instance Name: {0}", instanceName);
        Console.WriteLine("---------------------------");
        return instanceName;
    }

    private void WritePerformanceCounters()
    {
        Console.WriteLine("---------------------------");
        foreach (PerformanceCounter p in this.PerfCounters)
        {
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());
        }
        Console.WriteLine("---------------------------");
    }

    private static string GetIntegratedSecurityConnectionString()
    {
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +
          "Initial Catalog=AdventureWorks";
    }
    private static string GetSqlConnectionString()
    {
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=[PLACEHOLDER];" +
          "Initial Catalog=AdventureWorks";
    }

    private static string GetSqlConnectionStringDifferent()
    {
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +
          "User Id=LowPriv;Password=[PLACEHOLDER];";
    }
}
```

## <a name="see-also"></a><span data-ttu-id="17899-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17899-155">See also</span></span>

- [<span data-ttu-id="17899-156">데이터 소스에 연결</span><span class="sxs-lookup"><span data-stu-id="17899-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="17899-157">OLE DB, ODBC 및 Oracle 연결 풀링</span><span class="sxs-lookup"><span data-stu-id="17899-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="17899-158">[ASP.NET용 성능 카운터](/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17899-158">[Performance Counters for ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="17899-159">런타임 프로파일링</span><span class="sxs-lookup"><span data-stu-id="17899-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="17899-160">[성능 임계값 모니터링 소개](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="17899-160">[Introduction to Monitoring Performance Thresholds](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="17899-161">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="17899-161">ADO.NET Overview</span></span>](ado-net-overview.md)
