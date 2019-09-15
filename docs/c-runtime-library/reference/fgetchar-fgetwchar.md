---
title: _fgetchar、_fgetwchar
ms.date: 11/04/2016
api_name:
- _fgetchar
- _fgetwchar
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fgetwchar
- _fgettchar
- _fgetchar
- _fgetwchar
- fgettchar
helpviewer_keywords:
- fgetwchar function
- _fgetchar function
- fgettchar function
- _fgetwchar function
- _fgettchar function
- standard input, reading from
- fgetchar function
ms.assetid: 8bce874c-701a-41a3-b1b2-feff266fb5b9
ms.openlocfilehash: 90a97308b8c60776d52e58feb84c5398456f26d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940868"
---
# <a name="_fgetchar-_fgetwchar"></a>_fgetchar、_fgetwchar

從**stdin**讀取字元。

## <a name="syntax"></a>語法

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>傳回值

fgetchar 會傳回讀取為**int**的字元，或`EOF`傳回表示錯誤或檔案結尾。 **\_** fgetwchar 會以[wint_t](../../c-runtime-library/standard-types.md)的形式傳回對應`WEOF`于讀取或傳回字元的寬字元，以表示錯誤或檔案結尾。 **\_** 對於這兩個函式，請使用**feof**或**ferror**來區別錯誤和檔案結尾條件。

## <a name="remarks"></a>備註

這些函式會從**stdin**讀取單一字元。 此函式接著會增加相關聯的檔案指標 (定義時) 以指向下一個字元。 如果資料流位於檔案結尾，則會設定資料流的檔案結尾指標。

**_fgetchar**相當於`fgetc( stdin )`。 它也相當於**getchar**，但只實作為函式，而不是函式和宏。 **_fgetwchar**是 **_fgetchar**的寬字元版本。

這些函式與 ANSI 標準不相容。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台相關聯的標準資料流程控制碼（**stdin**、 **stdout**和**stderr**）必須先重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fgetchar.c
// This program uses _fgetchar to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char buffer[81];
   int  i, ch;

   // Read in first 80 characters and place them in "buffer":
   ch = _fgetchar();
   for( i=0; (i < 80 ) && ( feof( stdin ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetchar();
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
}
```

```Output

      Line one.
Line two.Line one.
Line two.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
