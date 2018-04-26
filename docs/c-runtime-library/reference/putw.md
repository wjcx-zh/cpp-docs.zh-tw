---
title: _putw | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _putw
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putw
- putw
dev_langs:
- C++
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f57ca7d619005ed8a4f67626dd5349bd4f8bc18
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="putw"></a>_putw

將一個整數寫入資料流。

## <a name="syntax"></a>語法

```C
int _putw(
   int binint,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*binint*<br/>
要輸出的二進位整數。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

傳回寫入的值。 傳回值為**EOF**可能表示發生錯誤。 因為**EOF**也是合法的整數值，使用**ferror**驗證錯誤。 如果*資料流*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**EOF**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Putw**函式會寫入類型的二進位值**int**的目前位置*資料流。* **_putw**不會影響的資料流中的項目對齊方式，也不會假設任何特殊的對齊方式。 **_putw**是主要是為了與先前的程式庫的相容性。 可移植性問題時可能發生之 **_putw**因為大小**int**中位元組的順序和**int**在系統之間會有所不同。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_putw**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_putw.c
/* This program uses _putw to write a
* word to a stream, then performs an error check.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   unsigned u;
   if( fopen_s( &stream, "data.out", "wb" ) )
      exit( 1 );
   for( u = 0; u < 10; u++ )
   {
      _putw( u + 0x2132, stream );   /* Write word to stream. */
      if( ferror( stream ) )         /* Make error check. */
      {
         printf( "_putw failed" );
         clearerr_s( stream );
         exit( 1 );
      }
   }
   printf( "Wrote ten words\n" );
   fclose( stream );
}
```

### <a name="output"></a>輸出

```Output
Wrote ten words
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
