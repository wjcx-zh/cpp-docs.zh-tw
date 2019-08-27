---
title: vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l
ms.date: 11/04/2016
apiname:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
ms.openlocfilehash: 2e665562f3dd8ee0be70b4e50068955a91233c60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499068"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l

使用引數清單的指標，寫入格式化輸出。 這些函式已有更安全的版本，請參閱 [vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)。

## <a name="syntax"></a>語法

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
輸出的儲存位置。

*計數*<br/>
要寫入的最大字元數。

*格式*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**Vsnprintf**函數會傳回寫入的字元數, 而不會計算結束的 null 字元。 如果*count*指定的緩衝區大小不夠大, 而無法包含*format*和*argptr*所指定的輸出, 則**vsnprintf**的傳回值就是要寫入的字元數, 而不是計算 null如果*count*夠大, 則為字元。 如果傳回值大於*計數*-1, 輸出就會被截斷。 傳回值 -1 表示發生編碼錯誤。

如果要寫入的字元數小於或等於*count*, **_vsnprintf**和 **_vsnwprintf**函數會傳回寫入的字元數。如果要寫入的字元數大於*計數*, 這些函式會傳回-1, 表示輸出已被截斷。

所有這些函式傳回的值都不包含終止的 Null，無論是否寫入。 當*count*為零時, 傳回的值是函式所要寫入的字元數, 不包括任何終止的 null。 您可以使用此結果為字串及其終止的 Null 配置足夠的緩衝區空間，然後再次呼叫函式，以填滿緩衝區。

如果*format*是**null**, 或者*buffer*是**null** , 而*count*不等於零, 則這些函式會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會傳回-1, 並將**errno**設為**EINVAL**。

## <a name="remarks"></a>備註

所有這些函式都會接受引數清單的指標, 然後格式化資料, 並將最多個字元寫入*緩衝區*所指向的記憶體。 **Vsnprintf**函式一律會寫入 null 結束字元, 即使它截斷輸出也一樣。 使用 **_vsnprintf**和 **_vsnwprintf**時, 只有在結尾有空間時, 緩衝區才會以 null 終止 (也就是, 如果要寫入的字元數小於*計數*)。

> [!IMPORTANT]
> 若要避免特定類型的安全性風險, 請確定*格式*不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

> [!NOTE]
> 若要確保在呼叫 **_vsnprintf**、 **_vsnprintf_l**、 **_vsnwprintf**和 **_vsnwprintf_l**時, 終止 null 有足夠空間, 請確定*計數*嚴格小於緩衝區長度, 並將緩衝區初始化為null, 然後再呼叫函式。
>
> 由於**vsnprintf**一律會寫入終止的 null, 因此*count*參數可能會等於緩衝區的大小。

從 Visual Studio 2015 和 Windows 10 的 UCRT 開始, **vsnprintf**不再與 **_vsnprintf**相同。 **Vsnprintf**函數符合 C99 標準; **_vnsprintf**是為了與舊版 Visual Studio 程式碼的回溯相容性而保留。

這些具有 **_l**尾碼的函式版本都相同, 不同之處在于它們會使用傳入的地區設定參數, 而不是目前的執行緒地區設定。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**、 **_vsnprintf**、 **_vsnprintf_l**|\<stdio.h>|\<stdio.h> 或 \<cstdio>|
|**_vsnwprintf**、 **_vsnwprintf_l**|\<stdio.h> 或 \<wchar.h>|\<stdio.h>、\<wchar.h>、\<cstdio> 或 \<cwchar>|

**_Vsnprintf**、 **_vsnprintf_l**、 **_vsnwprintf**和 **_vsnwprintf_l**函式為 Microsoft 特有的功能。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

如果您改用 vsnprintf 加上窄字串參數，行為就會變更。 *Count*參數可以是緩衝區的整個大小, 而傳回值則是當*計數*夠大時, 會寫入的字元數:

## <a name="example"></a>範例

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
