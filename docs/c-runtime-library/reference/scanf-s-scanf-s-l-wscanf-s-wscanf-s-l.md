---
title: scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 8811bd0b6e4009cd6aba570e65d0687fab465614
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231360"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l

從標準輸入資料流讀取格式化資料。 這些版本的 [scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>參數

*format*<br/>
格式控制字串。

*引數*<br/>
選擇性引數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回成功轉換和指派的欄位數。 傳回值不包含已讀取但未指派的欄位。 傳回值為0表示未指派任何欄位。 傳回值為**EOF**表示發生錯誤，或如果在第一次嘗試讀取字元時找到檔案結尾字元或字串結尾字元，則為。 如果*format*是**Null**指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **scanf_s**和**Wscanf_s**會傳回**EOF** ，並將**errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Scanf_s**函式會從標準輸入資料流程（ **stdin**）讀取資料，並將其寫入*引數*中。 每個*自*變數都必須是對應至類型規範（*格式*為）之變數類型的指標。 如果在重疊的字串之間進行複製，則行為是未定義的。

**wscanf_s**是寬字元版本的**scanf_s**;**wscanf_s**的*格式*引數是寬字元字串。 如果資料流程是以 ANSI 模式開啟， **wscanf_s**和**scanf_s**的行為會相同。 **scanf_s**目前不支援來自 UNICODE 資料流程的輸入。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們使用*地區*設定參數，而不是目前的執行緒地區設定。

不同于**scanf**和**wscanf**， **scanf_s**和**wscanf_s**會要求您指定某些參數的緩衝區大小。 指定所有**c**、 **c**、 **s**、 **s**或 string 控制項 set **[]** 參數的大小。 以字元為單位的緩衝區大小會當做額外參數傳遞。 它會緊接在緩衝區或變數的指標後面。 例如，如果您要讀取字串，該字串的緩衝區大小會以下列方式傳遞：

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

緩衝區大小包含終端機 null。 您可以使用 [寬度規格] 欄位，確保讀入的權杖會納入緩衝區中。 當令牌太大而無法容納時，除非有寬度規格，否則不會寫入任何內容。

> [!NOTE]
> Size 參數的類型為 **`unsigned`** ，而不是**size_t**。 使用靜態轉換，將64位組建設定的**size_t**值轉換為 **`unsigned`** 。

[緩衝區大小] 參數描述最大字元數，而不是位元組。 在此範例中，緩衝區類型的寬度不符合格式規範的寬度。

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S**格式規範表示使用「相反」的字元寬度，這是函式所支援的預設寬度。 字元寬度是單一位元組，但函數支援雙位元組字元。 這個範例會讀取最多9個單位元組寬字元的字串，並將它們放在雙位元組寬字元緩衝區中。 字元會視為單一位元組值；前兩個字元會儲存在 `ws[0]` 中，而後兩個會儲存在 `ws[1]` 中，依此類推。

這個範例會讀取單一字元：

```C
char c;
scanf_s("%c", &c, 1);
```

當讀取非 null 終止字串的多個字元時，整數會同時用於寬度規格和緩衝區大小。

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

如需詳細資訊，請參閱 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**scanf_s**， **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**， **_wscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺（UWP）應用程式中不支援此主控台。 標準串流處理**stdin**、 **stdout**和**Stderr**必須重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

此程式會在提供此輸入時產生下列輸出：

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、 \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
