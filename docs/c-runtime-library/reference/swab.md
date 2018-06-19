---
title: _swab | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeedb217466262d8643a851b5f93cb9ac26fb0a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408436"
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

*src*複製及交換資料。

*目的地*交換資料的儲存位置。

*n*複製及交換的位元組數目。

## <a name="return-value"></a>傳回值

**Swab**函式不會傳回值。 函式集合**errno**至**EINVAL**如果*src*或*目的地*指標是 null 或*n*較少者為比零 」 和 「 無效的參數叫用處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

如需這個傳回碼及其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

如果*n*是奇數， **_swab**函式複製*n*位元組從*src*，交換的相鄰的位元組，每個配對，並將在結果*目的地*。 如果*n*數值是奇數， **_swab**複製，並將第一個交換*n*-1 個位元組的*src*，而不會複製的最後一個位元組。 **_Swab**函式通常用來準備要傳輸到的機器使用不同的位元組順序的二進位資料。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
