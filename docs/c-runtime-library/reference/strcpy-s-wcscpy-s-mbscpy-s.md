---
title: strcpy_s、wcscpy_s、_mbscpy_s、_mbscpy_s_l
ms.date: 4/2/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: ac68d2fb86a43d7114b3b0e7651f5ae4367aa44b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358713"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>strcpy_s、wcscpy_s、_mbscpy_s、_mbscpy_s_l

複製字串。 這些是 [strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbscpy_s**和 **_mbscpy_s_l**不能在 Windows 運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*dest*<br/>
目的地字串緩衝區的位置。

*dest_size*<br/>
目標字串緩衝區的大小(以**字元**為單位),用於窄和多位元組函數 **,wchar_t**寬函數的單位。 此值必須大於零且不能大於**RSIZE_MAX**。

*src*<br/>
以 null 結束的來源字串緩衝區。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功則為零，否則為錯誤。

### <a name="error-conditions"></a>錯誤狀況

|*dest*|*dest_size*|*src*|傳回值|*dest*的內容|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**空**|任意|任意|**埃因瓦爾**|未修改|
|任意|任意|**空**|**埃因瓦爾**|*dest*[0] 設定為 0|
|任意|0 或太小|任意|**ERANGE**|*dest*[0] 設定為 0|

## <a name="remarks"></a>備註

**strcpy_s**函數將*src*位址中的內容(包括終止空字元)複製到*dest*指定的位置。 目的字串必須大到足以保留來源字串及其結束的 null 字元。 如果原始字串和目標字串重疊,則**strcpy_s**的行為未定義。

**wcscpy_s**是**strcpy_s**的寬字元版本 **,_mbscpy_s**是多位元組位元版本。 **wcscpy_s**的參數是寬字元字串;**_mbscpy_s**和 **_mbscpy_s_l**字串是多位元位元串。 除此之外，這些函式的行為相同。 **_mbscpy_s_l**與 **_mbscpy_s**相同,只是它使用傳入區域設置參數而不是當前區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*dest*或*src*是空指標,或者如果目標字串大小*dest_size*太小,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將返回**EINVAL**並將**errno**設定為**EINVAL,** 當*dest*或*src*是空指標時,它們傳回**ERANGE**並在目標字串太小時將**errno**設定為**ERANGE。**

成功執行後，目的字串永遠是以 null 終止的。

在 C++ 中，樣板多載簡化了這些函式的使用方式，樣板多載可自動推斷緩衝區長度 (因而您不須指定大小引數)，也可以自動將較舊且較不安全的函式取代成其較新且較安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<string.h> 或 \<wchar.h>|
|**_mbscpy_s**|\<mbstring.h>|

這些功能特定於Microsoft。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

與生產質量代碼不同,此示例呼叫安全字串函式而不檢查錯誤:

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

生成C++代碼時,範本版本可能更易於使用。

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[斯特卡特, wcscat, _mbscat, _mbscat_l](strcat-wcscat-mbscat.md) <br/>
[strcmp、wcscmp、_mbscmp、_mbscmp_l](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
