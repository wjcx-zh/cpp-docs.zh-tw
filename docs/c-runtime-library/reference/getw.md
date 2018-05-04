---
title: getw | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getw
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
- _getw
dev_langs:
- C++
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3caffb90252780b833b80e3e5d1cd6d5ef6b0fcb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getw"></a>_getw

從資料流中取得的整數。

## <a name="syntax"></a>語法

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**_getw**傳回讀取的整數值。 傳回值為**EOF**表示錯誤或檔案結尾。 不過，因為**EOF**值也是合法的整數值，請使用**feof**或**ferror**驗證檔案結尾或錯誤狀況。 如果*資料流*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**EOF**。

## <a name="remarks"></a>備註

**_Getw**函式會讀取下一個二進位值型別的**int**與相關聯的檔案從*資料流*並遞增指向相關聯的檔案指標 （如果有的話）下一個未讀取的字元。 **_getw**不採用任何特殊的對齊方式的資料流中的項目。 移轉的問題可能會發生 **_getw**因為大小**int**類型和順序內的位元組**int**類型在系統之間會有所不同。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crtgetwtxt"></a>輸入︰crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
