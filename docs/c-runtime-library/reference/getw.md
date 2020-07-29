---
title: _getw
ms.date: 4/2/2020
api_name:
- _getw
- _o__getw
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 786246afbb8ce4f733f733af75af3a70ce33006d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226212"
---
# <a name="_getw"></a>_getw

從資料流中取得的整數。

## <a name="syntax"></a>語法

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流程*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**_getw**會傳回讀取的整數值。 **EOF**的傳回值表示錯誤或檔案結尾。 不過，因為**EOF**值也是合法的整數值，所以請使用**feof**或**ferror**來驗證檔案結尾或錯誤狀況。 如果*stream*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**EOF**。

## <a name="remarks"></a>備註

**_Getw**函式會從與資料流程相關聯的檔案讀取類型的下一個二進位值 **`int`** ，並遞增相關聯的檔案指標（如果有的話），以指向下一個未讀取的字元。 *stream* **_getw**不會假設資料流程中的專案有任何特殊的對齊方式。 **_Getw**可能發生移植問題，因為類型的大小 **`int`** 和類型內的位元組順序在 **`int`** 不同的系統之間有所不同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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

### <a name="input-crt_getwtxt"></a>輸入︰crt_getw.txt

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
