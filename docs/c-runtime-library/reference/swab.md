---
title: _swab
ms.date: 11/04/2016
apiname:
- _swab
- stdlib/_swab
apilocation:
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
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: 64753383bcb94947e6b413b5f55ac6e2d9c7dbca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245500"
---
# <a name="swab"></a>_swab

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

**Swab**函式不會傳回值。 函式集合**errno**要**EINVAL**如果*src*或*dest*指標為 null 或*n*小於零，且不正確的參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。

如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

如果*n*是奇數， **_swab**函式複製*n*位元組*src*、 交換每一對相鄰的位元組，並將儲存在結果*dest*。 如果*n*是奇數， **_swab**複製並交換的第一個*n*-1 位元組*src*，而不會複製最後一個位元組。 **_Swab**函式通常用來準備要傳輸到使用不同位元組順序的機器的二進位資料。

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
