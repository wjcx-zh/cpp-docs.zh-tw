---
title: _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
dev_langs:
- C++
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2d8a2f5f80b00eef47d09a8d505f31a42a0fab2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cprintfs-cprintfsl-cwprintfs-cwprintfsl"></a>_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l

格式化並列印至主控台。 這些版本的 [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _cprintf_s(
   const char * format [,
   argument] ...
);
int _cprintf_s_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_s(
   const wchar * format [,
   argument] ...
);
int _cwprintf_s_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式控制字串。

*引數*<br/>
選擇性參數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

已列印的字元數。

## <a name="remarks"></a>備註

這些函式格式化並列印一系列字元和值到主控台，直接使用 **_putch**函式 (**_putwch**如 **_cwprintf_s**) 至輸出字元。 每個*引數*（如果有的話） 會轉換和輸出中的對應格式規格根據*格式*。 此格式具有相同的形式和功能*格式*參數[printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)函式。 不同於**fprintf_s**， **printf_s**，和**sprintf_s**函式，兩者都不 **_cprintf_s**也 **_cwprintf_s**換行字元轉譯為歸位字元-換 (CR-LF) 組合輸出時。

重要的差異在於 **_cwprintf_s**會顯示在 Windows NT 中使用時的 Unicode 字元。 不同於 **_cprintf_s**， **_cwprintf_s**會使用目前的主控台地區設定

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的地區設定的地區設定參數。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

例如不安全的版本 (請參閱[_cprintf、 _cprintf_l、 _cwprintf、 _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md))，這些函式會驗證它們的參數，並叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)，如果*格式*為 null 指標。 這些函式與不安全版本的差異在於也會一併驗證格式字串本身。 如果有任何未知或錯誤格式的格式規範，這些函式會叫用無效的參數處理常式。 在所有情況下，若要繼續，允許執行函式會傳回-1，並設定**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_cprintf_s**， **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**， **_cwprintf_s_l**|\<conio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_cprintf_s.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
   int      i = -16, h = 29;
   unsigned u = 62511;
   char     c = 'A';
   char     s[] = "Test";

   /* Note that console output does not translate \n as
    * standard output does. Use \r\n instead.
    */
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)<br/>
[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
