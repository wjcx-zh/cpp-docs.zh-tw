---
title: vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: edb534eb533d63c9298b7b7e9aced1be3e8652d9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502791"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l

使用引數清單的指標，寫入格式化輸出。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 版本。

## <a name="syntax"></a>語法

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
輸出的儲存位置。

*sizeOfBuffer*<br/>
輸出的 *緩衝區* 大小，以字元數表示。

*計數*<br/>
要寫入的字元數目上限 (不包括終止的 Null) 或 [_TRUNCATE](../../c-runtime-library/truncate.md)。

*format*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**vsnprintf_s**、 **_vsnprintf_s** 和 **_vsnwprintf_s** 會傳回寫入的字元數，不包括終止的 null，或如果發生截斷資料或輸出錯誤，則傳回負數值。

* 如果 *count* 小於 *sizeOfBuffer* ，且資料的字元數小於或等於 *count*，或 *count* 是 [_TRUNCATE](../../c-runtime-library/truncate.md) 且資料的字元數小於 *sizeOfBuffer*，則會寫入所有資料，並傳回字元數。

* 如果 *count* 小於 *sizeOfBuffer* ，但資料超過 *計數* 字元，則會寫入第一個 *計數* 字元。 截斷剩餘的資料時會傳回-1，而不會叫用不正確參數處理常式。

* 如果 *count* 是 [_TRUNCATE](../../c-runtime-library/truncate.md) ，且資料的字元數等於或超過 *sizeOfBuffer*，則會寫入 *緩衝區* (中最多的字串，其中包含終止 null) 。 截斷剩餘的資料時會傳回-1，而不會叫用不正確參數處理常式。

* 如果 *count* 等於或超過 *sizeOfBuffer* ，但資料的字元數小於 *sizeOfBuffer*，則會將所有資料寫入 (結束 null) ，並傳回字元數。

* 如果 *count* 和資料的字元數等於或超過 *sizeOfBuffer*，則會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果在不正確參數處理常式之後繼續執行，這些函式會將 *緩衝區* 設定為空字串，將 **Errno** 設定為 **ERANGE**，並傳回-1。

* 如果 *緩衝區* 或 *格式* 為 **Null** 指標，或如果 *count* 小於或等於零，則會叫用不正確參數處理常式。 如果允許繼續執行，這些函式會將 **errno** 設定為 **EINVAL** ，並傳回-1。

### <a name="error-conditions"></a>錯誤狀況

|**Condition**|傳回|**errno**|
|-----------------|------------|-------------|
|*緩衝區* 為 **Null**|-1|**EINVAL**|
|*格式* 為 **Null**|-1|**EINVAL**|
|*計數* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* 太小 (和 *count* ！ = **_TRUNCATE**) |-1 (，並將 *緩衝區* 設定為空字串) |**ERANGE**|

## <a name="remarks"></a>備註

**vsnprintf_s** 與 **_vsnprintf_s**相同。 為了符合 ANSI 標準，已包含**vsnprintf_s** 。 保留 **_vnsprintf**是為了回溯相容性。

這些函式中的每一個都會接受引數清單的指標，然後將所指定資料的 *數目* 和最多寫入至 *緩衝區* 所指向的記憶體，並附加終止 null。

如果 *count* 為 [_TRUNCATE](../../c-runtime-library/truncate.md)，則這些函式會以 *緩衝區* 形式寫入大量的字串，同時保留終止 null 的空間。 如果整個字串 (結束 null) 符合 *緩衝區*，則這些函式會傳回寫入的字元數 (不包含終止的 null) ;否則，這些函式會傳回-1，表示已發生截斷。

這些具有 **_l** 尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

> [!NOTE]
> 若要確定終止的 null 有空間，請確定 *計數* 嚴格小於緩衝區長度，或使用 **_TRUNCATE**。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**， **_vsnprintf_s_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**， **_vsnwprintf_s_l**|\<stdio.h> 或 \<wchar.h> 、和 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 相容性的必要項目。

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
