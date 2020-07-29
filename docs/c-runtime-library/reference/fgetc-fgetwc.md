---
title: fgetc、fgetwc
ms.date: 4/2/2020
api_name:
- fgetwc
- fgetc
- _o_fgetc
- _o_fgetwc
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
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: 5f8d4b1fcdc2d4d4de712ee79742025db74b6452
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189281"
---
# <a name="fgetc-fgetwc"></a>fgetc、fgetwc

從資料流讀取字元。

## <a name="syntax"></a>語法

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流程*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fgetc**會傳回讀取為的字元， **`int`** 或傳回**EOF**以表示錯誤或檔案結尾。 **fgetwc**會以[wint_t](../../c-runtime-library/standard-types.md)的形式傳回對應至讀取字元的寬字元，或傳回**WEOF**以表示錯誤或檔案結尾。 對於這兩個函式，請使用**feof**或**ferror**來區別錯誤和檔案結尾條件。 如果發生讀取錯誤，表示已設定資料流錯誤指標。 如果*stream*為**Null**，則**fgetc**和**fgetwc**會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回**EOF**。

## <a name="remarks"></a>備註

這些函式中的每一個都會從與*stream*相關聯之檔案的目前位置讀取單一字元。 此函式接著會增加相關聯的檔案指標 (定義時) 以指向下一個字元。 如果資料流位於檔案結尾，則會設定資料流的檔案結尾指標。

**fgetc**相當於**getc**，但僅實作為函式，而不是函式和宏。

**fgetwc**是**fgetc**的寬字元版本;它會根據以文字模式還是二進位模式開啟*資料流程*，將**c**當做多位元組字元或寬字元來讀取。

具有 **_nolock** 後置字元的版本與其相同，不同之處在於不受保護，不能免於其他執行緒的干擾。

如需在文字和二進位模式中處理寬字元和多位元組字元的詳細資訊，請參閱[文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetctxt"></a>輸入：crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Line one.
Line two.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
