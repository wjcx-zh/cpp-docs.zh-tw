---
title: _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l
ms.date: 11/04/2016
api_name:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
ms.openlocfilehash: c14da7158a3e15a74a01630a8a1b475d3e496de9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938974"
---
# <a name="_cprintf_s-_cprintf_s_l-_cwprintf_s-_cwprintf_s_l"></a>_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l

格式化並列印至主控台。 這些版本的 [_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

這些函式會使用 **_putch**函式（ **_putwch** for **_cwprintf_s**）來輸出字元，將一連串的字元和值直接格式化並列印到主控台。 每個*引數*（如果有的話）都會根據*格式*的對應格式規格進行轉換和輸出。 格式與[printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)函式的*格式*參數具有相同的形式和功能。 不同于**fprintf_s**、 **printf_s**和**sprintf_s**函式，當輸出時， **_cprintf_s**或 **_cwprintf_s**都不會將換行字元轉譯成換行回車（CR-LF）組合。

重要的差異在於， **_cwprintf_s**會在 Windows NT 中使用時顯示 Unicode 字元。 不同于 **_cprintf_s**， **_cwprintf_s**會使用目前的主控台地區設定

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的地區設定。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

與不安全版本相同（請參閱[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)），這些函式會驗證其參數，並叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述（如果*格式*為 null）。滑鼠. 這些函式與不安全版本的差異在於也會一併驗證格式字串本身。 如果有任何未知或錯誤格式的格式規範，這些函式會叫用無效的參數處理常式。 在所有情況下，如果允許繼續執行，則函式會傳回-1，並將**errno**設為**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cprintf_s**、 **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**、 **_cwprintf_s_l**|\<conio.h>|

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
