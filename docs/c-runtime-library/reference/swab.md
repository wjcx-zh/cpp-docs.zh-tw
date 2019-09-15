---
title: _swab
ms.date: 11/04/2016
api_name:
- _swab
- stdlib/_swab
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: b0faba55c42023f4d66adae68de6be2c1ab009a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946281"
---
# <a name="_swab"></a>_swab

交換位元組。

## <a name="syntax"></a>語法

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>參數

*src*<br/>
要複製並交換的資料。

*dest*<br/>
交換資料的儲存位置。

*n*<br/>
要複製並交換的位元組數目。

## <a name="return-value"></a>傳回值

**Swab**函數不會傳回值。 函式會將**errno**設定為**EINVAL** （*如果 src*或*dest*指標為 null 或*n*小於零），並叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。

如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

如果*n*是偶數，則 **_swab**函數會從*src*複製*n*個位元組，交換每一對連續的位元組，並將結果儲存在*dest*。 如果*n*是奇數，則 **_swab**會複製並交換*src*的前*n*-1 個位元組，而不會複製最後一個位元組。 **_Swab**函數通常用來準備要傳送至使用不同位元組順序之電腦的二進位資料。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> 或 \<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>另請參閱

[緩衝區操作](../../c-runtime-library/buffer-manipulation.md)<br/>
