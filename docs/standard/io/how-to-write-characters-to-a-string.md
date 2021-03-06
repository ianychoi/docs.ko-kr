---
title: '방법: 문자열에 문자 쓰기'
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: 21661a858cff9fc8bc84d497b4af8bedb1393f0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734532"
---
# <a name="how-to-write-characters-to-a-string"></a>방법: 문자열에 문자 쓰기

다음 코드 예제는 동기식 또는 비동기식으로 문자 배열에서 문자열로 문자를 씁니다.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>예: 콘솔 앱에서 동기식으로 문자 쓰기  

 다음 예제에서는 <xref:System.IO.StringWriter>를 사용하여 동기식으로 <xref:System.Text.StringBuilder> 개체에 문자 5개를 씁니다.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>예: WPF 앱에서 문자를 비동기식으로 쓰기

 다음 예제는 WPF 앱의 코드입니다. 창 로드 시, 이 예제는 <xref:System.Windows.Controls.TextBox> 컨트롤에서 모든 문자를 비동기식으로 읽고 배열에 저장합니다. 그런 다음, 각 문자 또는 공백 문자를 <xref:System.Windows.Controls.TextBlock> 컨트롤의 별도 라인에 비동기식으로 씁니다.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>참조

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [파일 및 스트림 I/O](index.md)  
- [비동기 파일 I/O](asynchronous-file-i-o.md)  
- [방법: 디렉터리 및 파일 열거](how-to-enumerate-directories-and-files.md)  
- [방법: 새로 만든 데이터 파일 읽기 및 쓰기](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [방법: 로그 파일 열기 및 추가](how-to-open-and-append-to-a-log-file.md)  
- [방법: 파일에서 텍스트 읽기](how-to-read-text-from-a-file.md)  
- [방법: 파일에 텍스트 쓰기](how-to-write-text-to-a-file.md)  
- [방법: 문자열에서 문자 읽기](how-to-read-characters-from-a-string.md)
