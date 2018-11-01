---
title: _cprintf、_cprintf_l、_cwprintf、_cwprintf_l
ms.date: 11/04/2016
apiname:
- _cwprintf_l
- _cprintf_l
- _cwprintf
- _cprintf
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
- _cwprintf
- cwprintf
- tcprintf
- _tcprintf
- _cprintf
- cwprintf_l
- tcprintf_l
- _tcprintf_l
- cprintf_l
- _cprintf_l
- _cwprintf_l
helpviewer_keywords:
- _cprintf_l function
- _cwprintf_l function
- cwprintf function
- cprintf_l function
- characters, printing to console
- printing characters to console
- _tcprintf_l function
- tcprintf function
- _tcprintf function
- tcprintf_l function
- _cwprintf function
- cwprintf_l function
- _cprintf function
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
ms.openlocfilehash: ce1913012ee37b19e15602daaa4eea042a69a3de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534039"
---
# <a name="cprintf-cprintfl-cwprintf-cwprintfl"></a>_cprintf、_cprintf_l、_cwprintf、_cwprintf_l

格式化並列印至主控台。 已有更安全的版本可用；請參閱 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _cprintf(
   const char * format [, argument_list]
);
int _cprintf_l(
   const char * format,
   locale_t locale [, argument_list]
);
int _cwprintf(
   const wchar * format [, argument_list]
);
int _cwprintf_l(
   const wchar * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式控制字串。

*argument_list*<br/>
格式字串的選擇性參數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

已列印的字元數。

## <a name="remarks"></a>備註

這些函式格式化並列印一系列的字元和值到主控台，直接使用 **_putch**函式 (**_putwch** for **_cwprintf**) 來輸出字元. 在每個引數*argument_list* （如果有的話） 會轉換和輸出中的對應格式規格根據*格式*。 *格式*引數會使用[格式規格語法，printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。 不同於**fprintf**， **printf**，並**sprintf**函式，都不 **_cprintf**也 **_cwprintf**會將換行字元轉譯為歸位字元傳回換行字元 (CR-LF) 組合時輸出。

重要的差異在於 **_cwprintf**會顯示在 Windows 中使用時的 Unicode 字元。 不同於 **_cprintf**， **_cwprintf**會使用目前的主控台地區設定。

使用這些函式的版本 **_l**尾碼都相同，只不過它們而不是目前的地區設定傳入的地區設定參數。

**_cprintf**驗證*格式*參數。 如果*格式*為 null 指標，函式會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1 和集執行**errno**要**EINVAL**。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf**|**_cprintf**|**_cprintf**|**_cwprintf**|
|**_tcprintf_l**|**_cprintf_l**|**_cprintf_l**|**_cwprintf_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cprintf**， **_cprintf_l**|\<conio.h>|
|**_cwprintf**， **_cwprintf_l**|\<conio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cprintf.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
    int         i = -16,
                h = 29;
    unsigned    u = 62511;
    char        c = 'A';
    char        s[] = "Test";

    // Note that console output does not translate \n as
    // standard output does. Use \r\n instead.
    //
    _cprintf( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)<br/>
[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
