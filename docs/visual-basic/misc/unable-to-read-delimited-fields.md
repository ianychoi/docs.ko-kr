---
description: '자세히 알아보기: EscapeQuotes이 True로 설정 된 경우 큰따옴표는 올바른 구분 기호가 아니기 때문에 구분 된 필드를 읽을 수 없습니다.'
title: EscapeQuotes가 True로 설정되어 있으면 큰따옴표가 올바른 구분 기호가 아니므로 구분된 필드를 읽을 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 066b5110eaddad74b64f1d86683d7ca2a0a619f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474397"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>EscapeQuotes가 True로 설정되어 있으면 큰따옴표가 올바른 구분 기호가 아니므로 구분된 필드를 읽을 수 없습니다.

`TextFieldParser` 는 따옴표(")가 구분 기호로 제공되고 `EscapeQuotes` 가 `True`로 설정되므로 파일에서 읽을 수 없습니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- `EscapeQuotes`를 `False`로 설정합니다.  
  
## <a name="see-also"></a>추가 정보

- [TextFieldParser.SetDelimiters 메서드](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser.Delimiters 속성](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [방법: 쉼표로 구분된 텍스트 파일에서 읽기](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser Object](../language-reference/objects/textfieldparser-object.md)
