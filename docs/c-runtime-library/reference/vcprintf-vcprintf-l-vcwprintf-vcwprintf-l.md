---
title: _vcprintf、_vcprintf_l、_vcwprintf、_vcwprintf_l
ms.date: 11/04/2016
api_name:
- _vcwprintf
- _vcprintf_l
- _vcwprintf_l
- _vcprintf
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
- _vcwprintf_l
- _vtcprintf
- vcwprintf
- _vcwprintf
- vcprintf_l
- _vcprintf_l
- _vcprintf
- vcprintf
- vcwprintf_l
helpviewer_keywords:
- vcwprintf function
- _vcwprintf_l function
- _vcprintf function
- _vcprintf_l function
- vtcprintf_l function
- vcprintf function
- vcprintf_l function
- _vtcprintf function
- _vcwprintf function
- _vtcprintf_l function
- vcwprintf_l function
- vtcprintf function
- formatted text [C++]
ms.assetid: 4ef8d237-6200-4b66-8731-8c57e5624bb1
ms.openlocfilehash: 2f2aa3dafc730b060e84558dfa03de5328e52893
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945639"
---
# <a name="_vcprintf-_vcprintf_l-_vcwprintf-_vcwprintf_l"></a>_vcprintf、_vcprintf_l、_vcwprintf、_vcwprintf_l

使用引數清單的指標，將格式化輸出寫入主控台。 這些函式已有更安全的版本可供使用，請參閱 [_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l](vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _vcprintf(
   const char* format,
   va_list argptr
);
int _vcprintf_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_l(
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

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

寫入的字元數，或是當發生輸出錯誤時為負值。 如果*format*是 null 指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，並傳回-1。

## <a name="remarks"></a>備註

所有這些函式都會接受引數清單的指標，然後格式化指定的資料，並將其寫入主控台。 **_vcwprintf**是 **_vcprintf**的寬字元版本。 它接受寬字元字串作為引數。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的地區設定。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf**|**_vcprintf**|**_vcprintf**|**_vcwprintf**|
|**_vtcprintf_l**|**_vcprintf_l**|**_vcprintf_l**|**_vcwprintf_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_vcprintf**、 **_vcprintf_l**|\<conio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vcwprintf**、 **_vcwprintf_l**|\<conio.h> 或 \<wchar.h> 和 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 相容性的必要項目。

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_vcprintf.cpp
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function used to print to the console.
int eprintf(const char* format, ...)
{
    va_list args;
    va_start(args, format);
    int result = _vcprintf(format, args);
    va_end(args);
    return result;
}

int main()
{
    eprintf("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
           "<some error text>");
    eprintf("    (Related to symbol '%s' defined on line %d).\n",
            "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
