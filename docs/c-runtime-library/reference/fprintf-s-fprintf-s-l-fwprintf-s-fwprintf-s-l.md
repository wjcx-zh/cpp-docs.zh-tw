---
title: fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l
ms.date: 11/04/2016
apiname:
- _fprintf_s_l
- fwprintf_s
- fprintf_s
- _fwprintf_s_l
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
apitype: DLLExport
f1_keywords:
- _ftprintf_s
- fprintf_s
- fwprintf_s
helpviewer_keywords:
- ftprintf_s_l function
- ftprintf_s function
- _fprintf_s_l function
- _ftprintf_s function
- _ftprintf_s_l function
- fwprintf_s_l function
- fwprintf_s function
- fprintf_s_l function
- fprintf_s function
- _fwprintf_s_l function
- print formatted data to streams
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
ms.openlocfilehash: 05886dc4ce7de771749f157913a222b6b01a5c5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333153"
---
# <a name="fprintfs-fprintfsl-fwprintfs-fwprintfsl"></a>fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l

將格式化資料列印至資料流。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md) 版本。

## <a name="syntax"></a>語法

```C
int fprintf_s(
   FILE *stream,
   const char *format [,
   argument_list ]
);
int _fprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument_list ]
);
int fwprintf_s(
   FILE *stream,
   const wchar_t *format [,
   argument_list ]
);
int _fwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument_list ]
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

*格式*<br/>
格式控制字串。

*argument_list*<br/>
格式字串的選擇性引數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**fprintf_s**傳回寫入的位元組數目。 **fwprintf_s**傳回寫入的寬字元數目。 發生輸出錯誤時，所有這些函式都會改為傳回負值。

## <a name="remarks"></a>備註

**fprintf_s**格式化並列印一系列的字元和值的輸出*串流*。 在每個引數*argument_list* （如果有的話） 會轉換和輸出中的對應格式規格根據*格式*。 *格式*引數會使用[格式規格語法，printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

**fwprintf_s**是寬字元版本的**fprintf_s**; 在**fwprintf_s**，*格式*是寬字元字串。 如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。 **fprintf_s**目前不支援輸出至 UNICODE 資料流。

使用這些函式的版本 **_l**尾碼都相同，只不過它們而不是目前的地區設定傳入的地區設定參數。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

與不安全版本 (請參閱[fprintf、 _fprintf_l、 fwprintf、 _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md))，這些函式會驗證其參數，並叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)，如果有任一*資料流*或是*格式*為 null 指標。 會一併驗證格式字串本身。 如果有任何未知或錯誤格式的格式規範，則這些函式會產生無效參數例外狀況。 在所有情況下，如果要繼續，請允許執行函式會傳回-1，並設定**errno**要**EINVAL**。 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf_s**|**fprintf_s**|**fprintf_s**|**fwprintf_s**|
|**_ftprintf_s_l**|**_fprintf_s_l**|**_fprintf_s_l**|**_fwprintf_s_l**|

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fprintf_s**， **_fprintf_s_l**|\<stdio.h>|
|**fwprintf_s**， **_fwprintf_s_l**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fprintf_s.c
// This program uses fprintf_s to format various
// data and print it to the file named FPRINTF_S.OUT. It
// then displays FPRINTF_S.OUT on the screen using the system
// function to invoke the operating-system TYPE command.

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf_s.out", "w" );
   fprintf_s( stream, "%s%c", s, c );
   fprintf_s( stream, "%d\n", i );
   fprintf_s( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf_s.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
