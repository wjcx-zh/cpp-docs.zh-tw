---
title: printf_s、_printf_s_l、wprintf_s、_wprintf_s_l
ms.date: 11/04/2016
api_name:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wprintf_s
- printf_s
helpviewer_keywords:
- wprintf_s function
- tprintf_s function
- _tprintf_s function
- printf_s_l function
- printf_s function
- _printf_s_l function
- printf function, format specification fields
- printf function, using
- _tprintf_s_l function
- wprintf_s_l function
- formatted text [C++]
- tprintf_s_l function
- _wprintf_s_l function
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
ms.openlocfilehash: f8b324b5f3c23b324bdcd43e3529ad3a3d4d6847
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950189"
---
# <a name="printf_s-_printf_s_l-wprintf_s-_wprintf_s_l"></a>printf_s、_printf_s_l、wprintf_s、_wprintf_s_l

將格式化輸出列印至標準輸出資料流。 這些是 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
int printf_s(
   const char *format [,
   argument]...
);
int _printf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf_s(
   const wchar_t *format [,
   argument]...
);
int _wprintf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>參數

*格式*<br/>
控制項格式。

*引數*<br/>
選擇性引數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回列印的字元數；如果發生錯誤，則為負值。

## <a name="remarks"></a>備註

**Printf_s**函式會格式化一系列的字元和值，並將其列印至標準輸出資料流程（ **stdout**）。 如果引數遵循*格式*字串，*格式*字串必須包含決定引數輸出格式的規格。

**Printf_s**和**printf**的主要差異在於， **printf_s**會檢查格式字串是否有有效的格式設定字元，而**printf**只會檢查格式字串是否為 null 指標。 如果其中一個檢查失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回-1，並將**errno**設定為**EINVAL**。

如需**errno**和錯誤碼的詳細資訊，請參閱[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**printf_s**和**fprintf_s**的行為相同，不同之處在于**printf_s**會將輸出寫入至**stdout** ，而不是**FILE**類型的目的地。 如需詳細資訊，請參閱 [fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)。

**wprintf_s**是寬字元版本的**printf_s**;*format*是寬字元字串。 如果資料流程是以 ANSI 模式開啟，則**wprintf_s**和**printf_s**的行為相同。 **printf_s**目前不支援輸出至 UNICODE 資料流程。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_unicode 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

*Format*引數是由一般字元、escape 序列和（如果引數遵循*格式*）格式規格所組成。 一般字元和 escape 序列會依照其外觀的順序複製到**stdout** 。 例如，下面這行

```C
printf_s("Line one\n\t\tLine two\n");
```

產生下列輸出

```Output
Line one
        Line two
```

[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)一律以百分比符號（ **%** ）開頭，並由左至右讀取。 當**printf_s**遇到第一個格式規格（如果有的話）時，它會將第一個引數的值轉換成*格式*，並據以輸出。 第二個格式規格會轉換及輸出第二個引數，依此類推。 如果引數的數目大於格式規格的數目，則會略過額外的引數。 如果提供給所有格式規格的引數不足，則結果為未定義。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**printf_s**、 **_printf_s_l**|\<stdio.h>|
|**wprintf_s**、 **_wprintf_s_l**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向, C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_printf_s.c
/* This program uses the printf_s and wprintf_s functions
* to produce formatted output.
*/

#include <stdio.h>

int main( void )
{
   char   ch = 'h', *string = "computer";
   int    count = -9234;
   double fp = 251.7366;
   wchar_t wch = L'w', *wstring = L"Unicode";

   /* Display integers. */
   printf_s( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",
           count, count, count );

   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   /* Display in different radixes. */
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   /* Display characters. */

   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);

   /* Display strings. */

   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",
   string, string, wstring, wstring);
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",
       string, string, wstring, wstring);

   /* Display real numbers. */
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );

   /* Display pointer. */
   printf_s( "\nAddress as:   %p\n", &count);

}
```

### <a name="sample-output"></a>範例輸出

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF78
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
