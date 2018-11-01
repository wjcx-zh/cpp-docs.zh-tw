---
title: _fgetchar、_fgetwchar
ms.date: 11/04/2016
apiname:
- _fgetchar
- _fgetwchar
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
ms.openlocfilehash: c74618fa0be5392062d13618ff73e2ef45bf7c2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453781"
---
# <a name="fgetchar-fgetwchar"></a>_fgetchar、_fgetwchar

讀取字元，以從**stdin**。

## <a name="syntax"></a>語法

```C
int _fgetchar( void );
wint_t _fgetwchar( void );
```

## <a name="return-value"></a>傳回值

**\_fgetchar**會傳回做為讀取的字元**int**退貨`EOF`表示錯誤或檔案結尾。 **\_fgetwchar**傳回，作為[wint_t](../../c-runtime-library/standard-types.md)，字元的寬字元對應至讀取的字元，或傳回`WEOF`表示錯誤或檔案結尾。 這兩個函式中，使用**feof**或是**ferror**來區分錯誤與檔案結尾條件。

## <a name="remarks"></a>備註

這些函式會讀取單一字元**stdin**。 此函式接著會增加相關聯的檔案指標 (定義時) 以指向下一個字元。 如果資料流位於檔案結尾，則會設定資料流的檔案結尾指標。

**_fgetchar**相當於`fgetc( stdin )`。 它也相當於**getchar**，但只為函式，而不是函式和巨集來實作。 **_fgetwchar**是寬字元版本 **_fgetchar**。

這些函式與 ANSI 標準不相容。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettchar**|**_fgetchar**|**_fgetchar**|**_fgetwchar**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fgetchar**|\<stdio.h>|
|**_fgetwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台與相關聯的標準資料流控制代碼 —**stdin**， **stdout**，並**stderr**— 必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
