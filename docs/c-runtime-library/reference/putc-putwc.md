---
title: putc、putwc
ms.date: 11/04/2016
apiname:
- putwc
- putc
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
- _puttc
- putwc
- putc
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
ms.openlocfilehash: 05bbb5434e6626076aab0d574b04058ec730b77c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444691"
---
# <a name="putc-putwc"></a>putc、putwc

將一個字元寫入資料流。

## <a name="syntax"></a>語法

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*C*<br/>
待寫入字元。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

傳回寫入的字元。 表示錯誤或檔案結尾條件**putc**並**putchar**傳回 * * EOF`; **putwc`並**putwchar**傳回**WEOF**。 針對所有四個常式，使用 [ferror](ferror.md) 或 [feof](feof.md) 可檢查是否有錯誤或檔案是否已結束。 如果是 null 指標傳遞給*資料流*，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則這些函式會傳回**EOF**或是**WEOF**並設定**errno**至**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Putc**常式寫入單一字元*c*輸出*串流*目前的位置。 任何整數都可以傳遞至**putc**，但只會較低的 8 位元會寫入。 **Putchar**常式等同於`putc( c, stdout )`。 針對每個常式，如果發生讀取錯誤，則會設定資料流的錯誤指標。 **putc**和**putchar**類似於**fputc**並 **_fputchar**分別，但會實作為函式和巨集 (請參閱[函式和巨集之間選擇](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md))。 **putwc**並**putwchar**是寬字元版本**putc**並**putchar**分別。 **putwc**並**putc**運作方式完全相同，如果資料流以 ANSI 模式開啟。 **putc**目前不支援輸出至 UNICODE 資料流。

具有 **_nolock** 後置字元的版本與其相同，不同之處在於不受保護，不能免於其他執行緒的干擾。 如需詳細資訊，請參閱 **_putc_nolock、_putwc_nolock**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台中，相關聯的標準資料流控制代碼**stdin**， **stdout**，並**stderr**，必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>輸出

```Output
This is the line of output
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
