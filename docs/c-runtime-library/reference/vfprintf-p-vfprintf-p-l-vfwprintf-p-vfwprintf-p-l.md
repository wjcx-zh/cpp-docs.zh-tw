---
title: _vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vfprintf_p
- _vfwprintf_p
- _vfprintf_p_l
- _vfwprintf_p_l
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
- _vfwprintf_p_l
- _vfprintf_p
- vfwprintf_p_l
- vfwprintf_p
- vfprintf_p_l
- _vfwprintf_p
- _vftprintf_p
- _vfprintf_p_l
- vfprintf_p
dev_langs:
- C++
helpviewer_keywords:
- vfprintf_p_l function
- _vftprintf_p_l function
- _vfprintf_p function
- vfprintf_p function
- vftprintf_p_l function
- _vfprintf_p_l function
- _vftprintf_p function
- _vfwprintf_p_l function
- vfwprintf_p_l function
- _vfwprintf_p function
- vftprintf_p function
- formatted text [C++]
- vfwprintf_p function
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd54c27f4208dce317d9c09720cb63b65af4a54b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="vfprintfp-vfprintfpl-vfwprintfp-vfwprintfpl"></a>_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l

使用引數清單的指標將格式化輸出，而且可以指定在格式字串中使用引數的順序。

## <a name="syntax"></a>語法

```C
int _vfprintf_p(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vfwprintf_p(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

*格式*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**_vfprintf_p**和 **_vfwprintf_p**傳回寫入的字元數，不包括結束的 null 字元或負數值，如果發生輸出錯誤。

## <a name="remarks"></a>備註

所有這些函式接受的指標引數清單，然後格式化並寫入至指定的資料*資料流*。 這些函式的不同 **_vfprint_s**和 **_vfwprint_s**版本僅在於它們支援位置參數。 如需詳細資訊，請參閱 [printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。

**_vfwprintf_p**是寬字元版本的 **_vprintf_p**; 兩個函式的資料流在 ANSI 模式中開啟時即會相同行為。 **_vprintf_p**目前不支援 UNICODE 資料流輸出。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的執行緒地區設定的地區設定參數。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

如果有任一個*資料流*或*格式*為 null 指標，或如果格式字串包含無效格式化字元，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1，並設定**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_p**|**_vfprintf_p**|**_vfprintf_p**|**_vfwprintf_p**|
|**_vftprintf_p_l**|**_vfprintf_p_l**|**_vfprintf_p_l**|**_vfwprintf_p_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_vfprintf_p**， **_vfprintf_p_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vfwprintf_p**， **_vfwprintf_p_l**|\<stdio.h> 或 \<wchar.h>，以及 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 相容性的必要項目。

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)<br/>
[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
