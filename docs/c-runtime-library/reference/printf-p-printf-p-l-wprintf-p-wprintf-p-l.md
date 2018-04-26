---
title: _printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _printf_p
- _wprintf_p
- _printf_p_l
- _wprintf_p_l
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
- wprintf_p
- _wprintf_p
- printf_p_l
- _printf_p
- printf_p
- _wprintf_p_l
- _printf_p_l
- wprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- printf_p function
- printf_p_l function
- wprintf_p function
- wprintf_p_l function
- _tprintf_p_l function
- _wprintf_p function
- _wprintf_p_l function
- _printf_p function
- tprintf_p_l function
- _printf_p_l function
ms.assetid: 1b7e9ef9-a069-45db-af9d-c2730168322e
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7698181ba23ececc251196702cb76a3b912788e4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="printfp-printfpl-wprintfp-wprintfpl"></a>_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l

將格式化的輸出列印至標準輸出資料流，並啟用在格式字串中使用參數的順序規格。

## <a name="syntax"></a>語法

```C
int _printf_p(
   const char *format [,
   argument]...
);
int _printf_p_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int _wprintf_p(
   const wchar_t *format [,
   argument]...
);
int _wprintf_p_l(
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

**_Printf_p**函式格式化並列印一系列字元和值寫入標準輸出資料流**stdout**。 如果引數會遵循*格式*字串*格式*字串必須包含決定輸出格式的引數的規格 (請參閱[printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)).

之間的差異 **_printf_p**和**printf_s**在於 **_printf_p**支援位置參數，可讓您指定的引數順序格式字串中使用。 如需詳細資訊，請參閱 [printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。

**_wprintf_p**是寬字元版本的 **_printf_p**; 它們的行為即會相同資料流在 ANSI 模式中開啟。 **_printf_p**目前不支援 UNICODE 資料流輸出。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的執行緒地區設定的地區設定參數。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

如果*格式*或*引數*是**NULL**，此格式字串包含無效格式化字元，或 **_printf_p**和 **_wprintf_p**函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1 以及設定執行**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf_p**|**_printf_p**|**_printf_p**|**_wprintf_p**|
|**_tprintf_p_l**|**_printf_p_l**|**_printf_p_l**|**_wprintf_p_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_printf_p**， **_printf_p_l**|\<stdio.h>|
|**_wprintf_p**， **_wprintf_p_l**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_printf_p.c
// This program uses the _printf_p and _wprintf_p
// functions to choose the order in which parameters
// are used.

#include <stdio.h>

int main( void )
{
   // Positional arguments
   _printf_p( "Specifying the order: %2$s %3$s %1$s %4$s %5$s.\n",
              "little", "I'm", "a", "tea", "pot");

   // Resume arguments
   _wprintf_p( L"Reusing arguments: %1$d %1$d %1$d %1$d\n", 10);

   // Width argument
   _printf_p("Width specifiers: %1$*2$s", "Hello\n", 10);
}
```

```Output
Specifying the order: I'm a little tea pot.
Reusing arguments: 10 10 10 10
Width specifiers:     Hello
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
