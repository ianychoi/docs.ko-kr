---
description: '자세히 알아보기: PublicKeyBlob Structure'
title: PublicKeyBlob 구조체
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 94c1ea3d5a41bbb8941658e87f97cd6d6336187a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736483"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 구조체

공개/개인 키 쌍의 공개 키를 이진 형식으로 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`SigAlgId`|`ALG_ID`공개 키의 서명 알고리즘 (wincrypt.h에 정의 된 형식)에 대 한 식별자입니다.|  
|`HashAlgId`|`ALG_ID`공개 키의 해시 알고리즘 (wincrypt.h에 정의 된 형식)에 대 한 식별자입니다.|  
|`cbPublicKey`|키의 길이 (바이트)입니다.|  
|`PublicKey`|CryptoAPI에서 반환 된 형식의 키 값을 포함 하는 가변 길이 바이트 배열입니다.|  
  
## <a name="remarks"></a>설명  

 `PublicKeyBlob`구조체는 [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)및 기타 강력한 이름 함수에서 공개/개인 키 쌍의 공개 키를 나타내는 데 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** StrongName  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [StrongNameGetPublicKey 함수](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 함수](strongnamesignaturegeneration-function.md)
