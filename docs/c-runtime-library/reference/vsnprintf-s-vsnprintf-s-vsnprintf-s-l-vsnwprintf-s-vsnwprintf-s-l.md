---
title: vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd7c468e516c25e2c2b408b8c1112061eeb5e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l

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

*buffer*<br/>
輸出的儲存位置。

*sizeOfBuffer*<br/>
大小*緩衝區*輸出，以字元計數。

*count*<br/>
要寫入的字元數目上限 (不包括終止的 Null) 或 [_TRUNCATE](../../c-runtime-library/truncate.md)。

*格式*<br/>
格式規格。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**vsnprintf_s**， **_vsnprintf_s**和 **_vsnwprintf_s**傳回寫入的字元數，不包括結束的 null 或負數值，如果發生輸出錯誤。 **vsnprintf_s**等同於 **_vsnprintf_s**。 **vsnprintf_s**是否包含 ANSI 標準的相容性。 **_vnsprintf**保留回溯相容性。

如果儲存的資料和結束的 null 所需的儲存體超過*sizeOfBuffer*、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)，除非*計數*是[_TRUNCATE](../../c-runtime-library/truncate.md)，在此情況下盡量字串做為符合*緩衝區*寫入並傳回-1。 如果無效參數處理常式之後，繼續執行，這些函式會將*緩衝區*為空字串，設定**errno**至**為 ERANGE**，並傳回-1。

如果*緩衝區*或*格式*是**NULL**指標，或如果*計數*小於或等於零，會叫用無效參數處理常式。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回-1。

### <a name="error-conditions"></a>錯誤狀況

|**條件**|Return|**errno**|
|-----------------|------------|-------------|
|*緩衝區*是**NULL**|-1|**EINVAL**|
|*格式*是**NULL**|-1|**EINVAL**|
|*計數*< = 0|-1|**EINVAL**|
|*sizeOfBuffer*太小 (和*計數*！ = **_TRUNCATE**)|-1 (和*緩衝區*設為空字串)|**ERANGE**|

## <a name="remarks"></a>備註

所有這些函式接受引數清單的指標，然後格式化並將最多*計數*所指字元的指定資料的記憶體*緩衝區*並在後面附加結束的 null。

如果*計數*是[_TRUNCATE](../../c-runtime-library/truncate.md)，則這些函式撰寫來做為填滿的字串量*緩衝區*時留出空間給結束的 null。 如果整個字串 （包括結束 null) 適合於*緩衝區*，則這些函式會傳回寫入 （不包括結束的 null） 的字元數; 否則這些函數會傳回 – 1，表示該截斷發生。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的執行緒地區設定的地區設定參數。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

> [!NOTE]
> 若要確定出空間給結束的 null，務必*計數*絕對小於緩衝區長度或使用 **_TRUNCATE**。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**， **_vsnprintf_s_l**|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**， **_vsnwprintf_s_l**|\<stdio.h> 或 \<wchar.h>，以及 \<stdarg.h>|\<varargs.h>*|

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
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](va-arg-va-copy-va-end-va-start.md)<br/>
