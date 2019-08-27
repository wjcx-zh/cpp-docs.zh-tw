---
title: vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l
ms.date: 11/04/2016
apiname:
- vfwprintf_s
- _vfprintf_s_l
- vfprintf_s
- _vfwprintf_s_l
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
- _vftprintf_s
- vfwprintf_s
- vfprintf_s
helpviewer_keywords:
- vfprintf_s_l function
- vfwprintf_s_l function
- vfwprintf_s function
- _vfprintf_s_l function
- _vfwprintf_s_l function
- vftprintf_s_l function
- vfprintf_s function
- _vftprintf_s_l function
- formatted text [C++]
- _vftprintf_s function
ms.assetid: eab6f563-46e2-4806-963f-2b23f339ecdc
ms.openlocfilehash: f512d58ecd6460cdc5df2a07016b36d626ca76dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499227"
---
# <a name="vfprintf_s-_vfprintf_s_l-vfwprintf_s-_vfwprintf_s_l"></a>vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l

使用引數清單的指標，寫入格式化輸出。 這些版本的 [vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
int vfprintf_s(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vfwprintf_s(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

*格式*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**vfprintf_s**和**vfwprintf_s**會傳回寫入的字元數, 不包括結束的 null 字元, 或如果發生輸出錯誤, 則傳回負數值。 如果*資料流程*或*格式*為 null 指標, 或如果格式字串包含不正確格式化字元, 則會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 函式會傳回-1, 並將**errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會接受引數清單的指標, 然後格式化指定的資料, 並將其寫入*資料流程*。

這些函式與不安全版本的差異, 僅在於安全版本會檢查*格式*字串是否包含有效的格式化字元。

**vfwprintf_s**是**vfprintf_s**的寬字元版本;如果資料流程是以 ANSI 模式開啟, 則這兩個函式的行為相同。 **vfprintf_s**目前不支援輸出至 UNICODE 資料流程。

這些具有 **_l**尾碼的函式版本都相同, 不同之處在于它們會使用傳入的地區設定參數, 而不是目前的執行緒地區設定。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_s**|**vfprintf_s**|**vfprintf_s**|**vfwprintf_s**|
|**_vftprintf_s_l**|**_vfprintf_s_l**|**_vfprintf_s_l**|**_vfwprintf_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**vfprintf_s**、 **_vfprintf_s_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**vfwprintf_s**、 **_vfwprintf_s_l**|\<stdio.h> 或 \<wchar.h>，以及 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 相容性的必要項目。

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
