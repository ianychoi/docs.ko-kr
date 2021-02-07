---
description: '자세히 알아보기: OracleDataReader를 사용 하 여 여러 REF Cursor에서 데이터 검색'
title: OracleDataReader를 사용하여 여러 Multiple REF CURSOR에서 데이터 검색
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 855373bd8307adbdf771ec9caf61c685a82d1108
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663432"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="48eaa-103">OracleDataReader를 사용하여 여러 Multiple REF CURSOR에서 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="48eaa-103">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>

<span data-ttu-id="48eaa-104">이 Microsoft Visual Basic 예제에서는 REF CURSOR 매개 변수 두 개를 반환하는 PL/SQL 저장 프로시저를 실행하고 <xref:System.Data.OracleClient.OracleDataReader>를 사용하여 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="48eaa-104">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

```vb
Private Sub Button1_Click( _
  ByVal sender As Object, ByVal e As System.EventArgs)  _
  Handles Button1.Click

  Dim connString As New String( _
      "Data Source=Oracle9i;User ID=scott;Password=[PLACEHOLDER];")
  Using conn As New OracleConnection(connString)
    Dim cmd As New OracleCommand()
    Dim rdr As OracleDataReader

    conn.Open()
    cmd.Connection = conn
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"
    cmd.CommandType = CommandType.StoredProcedure
    cmd.Parameters.Add(New OracleParameter( _
      "EMPCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output
    cmd.Parameters.Add(New OracleParameter(_
      "DEPTCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output

    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)
    While (rdr.Read())
        REM do something with the values from the EMP table
    End While

    rdr.NextResult()
    While (rdr.Read())
        REM do something with the values from the DEPT table
    End While
    rdr.Close()
  End Using
End Sub
```

## <a name="see-also"></a><span data-ttu-id="48eaa-105">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48eaa-105">See also</span></span>

- [<span data-ttu-id="48eaa-106">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="48eaa-106">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="48eaa-107">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="48eaa-107">ADO.NET Overview</span></span>](ado-net-overview.md)
