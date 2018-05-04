---
title: _vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vcprintf_p
- _vcwprintf_p_l
- _vcprintf_p_l
- _vcwprintf_p
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
- vcwprintf_p
- vcprintf_p_l
- _vcprintf_p
- _vcprintf_p_l
- vcwprintf_p_l
- vcprintf_p
- _vcwprintf_p
- _vcwprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- _vtcprintf_p_l function
- vcprintf_p_l function
- _vcprintf_p_l function
- vtcprintf_p_l function
- vcprintf_p function
- _vcwprintf_p function
- _vcprintf_p function
- vcwprintf_p function
- vcwprintf_p_l function
- vtcprintf_p function
- _vcwprintf_p_l function
- _vtcprintf_p function
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03251c9f0442ffa3cda6b00b6528e424e1fe9007
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="vcprintfp-vcprintfpl-vcwprintfp-vcwprintfpl"></a>_vcprintf_p、_vcprintf_p_l、_vcwprintf_p、_vcwprintf_p_l

使用引數清單的指標將格式化輸出寫入到主控台，並支援在格式字串中的位置參數。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _vcprintf_p(
   const char* format,
   va_list argptr
);
int _vcprintf_p_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf_p(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_p_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

寫入的字元數，或是當發生輸出錯誤時為負值。 如果*格式*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL** ，則傳回-1。

## <a name="remarks"></a>備註

所有這些函式接受引數清單的指標，然後使用 **_putch**函式格式化和寫入主控台中指定的資料。 (**_vcwprintf_p**使用 **_putwch**而不是 **_putch**。 **_vcwprintf_p**是寬字元版本的 **_vcprintf_p**。 它需要寬字元字串做為引數。)

有這些函式的版本 **_l**尾碼是一樣的不同之處在於它們使用傳入的地區設定參數，而不是目前的地區設定。

每個*引數*（如果有的話） 會轉換和輸出中的對應格式規格根據*格式*。 格式規格支援位置參數，以便讓您可以指定格式字串中使用引數的順序。 如需詳細資訊，請參閱 [printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。

在輸出換行字元時，這些函式不會將其轉譯為歸位字元-換行字元 (CR-LF) 組合。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

這些函式會驗證輸入的指標和格式字串。 如果*格式*或*引數*是**NULL**，或如果格式字串包含無效格式化字元，這些函式會叫用無效參數處理常式，如所述在[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**至**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_vtcprintf_p**|**_vcprintf_p**|**_vcprintf_p**|**_vcwprintf_p**|
|**_vtcprintf_p_l**|**_vcprintf_p_l**|**_vcprintf_p_l**|**_vcwprintf_p_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_vcprintf_p**， **_vcprintf_p_l**|\<conio.h> 和 \<stdarg.h>|
|**_vcwprintf_p**， **_vcwprintf_p_l**|\<conio.h> 和 \<stdarg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_vcprintf_p.c
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function that's used to print to the console.
int eprintf(const char* format, ...)
{
   va_list args;
   va_start(args, format);
   int result = _vcprintf_p(format, args);
   va_end(args);
   return result;
}

int main()
{
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",
      "one", 222);
   _cprintf_s("%d characters printed\r\n");
}
```

```Output
parameter 2 = 222; parameter 1 = one
38 characters printed
```

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
