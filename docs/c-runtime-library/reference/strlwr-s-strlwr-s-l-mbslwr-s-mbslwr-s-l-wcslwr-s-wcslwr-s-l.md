---
title: _strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l
ms.date: 11/04/2016
api_name:
- _strlwr_s_l
- _mbslwr_s_l
- _mbslwr_s
- _wcslwr_s
- _strlwr_s
- _wcslwr_s_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strlwr_s_l
- _strlwr_s
- mbslwr_s_l
- strlwr_s_l
- _wcslwr_s
- strlwr_s
- mbslwr_s
- _wcslwr_s_l
- wcslwr_s_l
- _tcslwr_s
- _tcslwr_s_l
- _mbslwr_s_l
- wcslwr_s
- _mbslwr_s
helpviewer_keywords:
- _tcslwr_s function
- wcslwr_s function
- _mbslwr_s function
- _wcslwr_s function
- strlwr_s_l function
- mbslwr_s_l function
- _strlwr_s function
- string conversion [C++], case
- strlwr_s function
- wcslwr_s_l function
- _tcslwr_s_l function
- mbslwr_s function
- strings [C++], case
- _wcslwr_s_l function
- converting case, CRT functions
- _strlwr_s_l function
- _mbslwr_s_l function
- case, converting
- tcslwr_s function
- tcslwr_s_l function
- strings [C++], converting case
ms.assetid: 4883d31b-bdac-4049-83a1-91dfdeceee79
ms.openlocfilehash: 70009f1d7d0230b37c6a59da20996842f976d02f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947581"
---
# <a name="_strlwr_s-_strlwr_s_l-_mbslwr_s-_mbslwr_s_l-_wcslwr_s-_wcslwr_s_l"></a>_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l

使用目前的地區設定或傳入的地區設定物件，將字串轉換成小寫。 這些版本的 [_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbslwr_s**和 **_mbslwr_s_l**不能在 Windows 執行階段中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _strlwr_s(
   char *str,
   size_t numberOfElements
);
errno_t _strlwr_s_l(
   char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _mbslwr_s(
   unsigned char *str,
   size_t numberOfElements
);
errno_t _mbslwr_s_l(
   unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _wcslwr_s(
   wchar_t *str,
   size_t numberOfElements
);
errno_t _wcslwr_s_l(
   wchar_t *str,
   size_t numberOfElements,
   _locale_t locale
);
template <size_t size>
errno_t _strlwr_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _strlwr_s_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbslwr_s(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
errno_t _mbslwr_s_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _wcslwr_s(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
errno_t _wcslwr_s_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*str*<br/>
要轉換為小寫的以 Null 終止的字串。

*numberOfElements*<br/>
緩衝區的大小。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則傳回零；如果失敗，則傳回非零的錯誤碼。

這些函式會驗證它們的參數。 如果*str*不是有效的以 null 終止的字串，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回**EINVAL** ，並將**Errno**設定為**EINVAL**。 如果*numberOfElements*小於字串的長度，函數也會傳回**EINVAL** ，並將**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Strlwr_s**函式會就地將*str*中的任何大寫字母轉換成小寫字母。 **_mbslwr_s**是 **_strlwr_s**的多位元組字元版本。 **_wcslwr_s**是 **_strlwr_s**的寬字元版本。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr_s**|**_strlwr_s**|**_mbslwr_s**|**_wcslwr_s**|
|**_tcslwr_s_l**|**_strlwr_s_l**|**_mbslwr_s_l**|**_wcslwr_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strlwr_s**、 **_strlwr_s_l**|\<string.h>|
|**_mbslwr_s**、 **_mbslwr_s_l**|\<mbstring.h>|
|**_wcslwr_s**、 **_wcslwr_s_l**|\<string.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_strlwr_s.cpp
// This program uses _strlwr_s and _strupr_s to create
// uppercase and lowercase copies of a mixed-case string.
//

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
   char str[] = "The String to End All Strings!";
   char *copy1, *copy2;
   errno_t err;

   err = _strlwr_s( copy1 = _strdup(str), strlen(str) + 1);
   err = _strupr_s( copy2 = _strdup(str), strlen(str) + 1);

   printf( "Mixed: %s\n", str );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );

   return 0;
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)<br/>
