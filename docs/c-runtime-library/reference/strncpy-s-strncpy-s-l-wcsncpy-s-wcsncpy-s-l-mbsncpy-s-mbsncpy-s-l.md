---
title: strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l
ms.date: 11/04/2016
apiname:
- _mbsncpy_s_l
- wcsncpy_s
- _strncpy_s_l
- strncpy_s
- _mbsncpy_s
- _wcsncpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsncpy_s
- _wcsncpy_s_l
- strncpy_s
- _strncpy_s_l
- wcsncpy_s
- _tcsncpy_s_l
helpviewer_keywords:
- _wcsncpy_s_l function
- _mbsnbcpy_s function
- _tcsncpy_s_l function
- mbsncpy_s function
- strncpy_s_l function
- _strncpy_s_l function
- strncpy_s function
- mbsncpy_s_l function
- wcsncpy_s function
- copying strings
- strings [C++], copying
- _mbsnbcpy_s_l function
- _tcsncpy_s function
- wcsncpy_s_l function
ms.assetid: a971c800-94d1-4d88-92f3-a2fe236a4546
ms.openlocfilehash: 8a6fc997ed874ba976e96f87df377e6fafd84a6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430065"
---
# <a name="strncpys-strncpysl-wcsncpys-wcsncpysl-mbsncpys-mbsncpysl"></a>strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l

將某個字串的字元複製到另一個字串。  這些版本的 [strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> **_mbsncpy_s**並 **_mbsncpy_s_l**不能在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t strncpy_s(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count
);
errno_t _strncpy_s_l(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count,
   _locale_t locale
);
errno_t wcsncpy_s(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count
);
errno_t _wcsncpy_s_l(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
errno_t _mbsncpy_s(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count
);
errno_t _mbsncpy_s_l(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count,
   locale_t locale
);
template <size_t size>
errno_t strncpy_s(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _strncpy_s_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t wcsncpy_s(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _wcsncpy_s_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbsncpy_s(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsncpy_s_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*strDest*<br/>
目的字串。

*numberOfElements*<br/>
目的地字串的大小 (以字元計)。

*strSource*<br/>
來源字串。

*count*<br/>
要複製的字元數，或 [_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零**STRUNCATE**如果發生截斷，否則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*strDest*|*numberOfElements*|*strSource*|傳回值|內容*strDest*|
|---------------|------------------------|-----------------|------------------|---------------------------|
|**NULL**|any|any|**EINVAL**|未修改|
|any|any|**NULL**|**EINVAL**|*strDest*[0] 設為 0|
|any|0|any|**EINVAL**|未修改|
|不**NULL**|太小|any|**ERANGE**|*strDest*[0] 設為 0|

## <a name="remarks"></a>備註

這些函式嘗試將第一個*D*個字元*strSource*來*strDest*，其中*D*是較小的*計數*和長度*strSource*。 如果有這些*D*字元適合*strDest* (其大小指定為*numberOfElements*) 和仍留出空間給 null 結束字元，則會將這些字元會複製並附加終止 null;否則，請*strDest*[0] 會設定 null 字元並不正確的參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。

上述段落有一個例外狀況。 如果*計數*是 **_TRUNCATE**，然後盡可能*strSource*做為可納入*strDest*複製同時仍留出空間給終止一律會附加 null。

例如，套用至物件的

```C
char dst[5];
strncpy_s(dst, 5, "a long string", 5);
```

表示我們要求**strncpy_s**來複製五個字元的緩衝區長度的五個位元組，這不會留下任何空間給 null 結束字元，因此**strncpy_s**歸零字串，並呼叫無效參數處理常式。

如果需要截斷行為，使用 **_TRUNCATE**或 (*大小*-1):

```C
strncpy_s(dst, 5, "a long string", _TRUNCATE);
strncpy_s(dst, 5, "a long string", 4);
```

請注意，不同於**strncpy**，如果*計數*的長度大於*strSource*，不長度null字元填補目的字串*計數*。

行為**strncpy_s**是未定義的如果來源和目的字串重疊。

如果*strDest*或是*strSource*會**NULL**，或*numberOfElements*是 0，則會叫用無效參數處理常式。 如果允許繼續執行，則函數會傳回**EINVAL**並設定**errno**來**EINVAL**。

**wcsncpy_s**並 **_mbsncpy_s**是寬字元和多位元組字元版本的**strncpy_s**。 引數和傳回值**wcsncpy_s**並**mbsncpy_s**執行會隨之改變。 除此之外，這六個函式的行為相同。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncpy_s**|**strncpy_s**|**_mbsnbcpy_s**|**wcsncpy_s**|
|**_tcsncpy_s_l**|**_strncpy_s_l**|**_mbsnbcpy_s_l**|**_wcsncpy_s_l**|

> [!NOTE]
> **_strncpy_s_l**， **_wcsncpy_s_l**並 **_mbsncpy_s_l**沒有任何地區設定相依性，並只針對所提供 **_tcsncpy_s_l**並不是要直接呼叫。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strncpy_s**， **_strncpy_s_l**|\<string.h>|
|**wcsncpy_s**， **_wcsncpy_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbsncpy_s**， **_mbsncpy_s_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_strncpy_s_1.cpp
// compile with: /MTd

// these #defines enable secure template overloads
// (see last part of Examples() below)
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <crtdbg.h>  // For _CrtSetReportMode
#include <errno.h>

// This example uses a 10-byte destination buffer.

errno_t strncpy_s_tester( const char * src,
                          int count )
{
   char dest[10];

   printf( "\n" );

   if ( count == _TRUNCATE )
      printf( "Copying '%s' to %d-byte buffer dest with truncation semantics\n",
               src, _countof(dest) );
   else
      printf( "Copying %d chars of '%s' to %d-byte buffer dest\n",
              count, src, _countof(dest) );

   errno_t err = strncpy_s( dest, _countof(dest), src, count );

   printf( "    new contents of dest: '%s'\n", dest );

   return err;
}

void Examples()
{
   strncpy_s_tester( "howdy", 4 );
   strncpy_s_tester( "howdy", 5 );
   strncpy_s_tester( "howdy", 6 );

   printf( "\nDestination buffer too small:\n" );
   strncpy_s_tester( "Hi there!!", 10 );

   printf( "\nTruncation examples:\n" );

   errno_t err = strncpy_s_tester( "How do you do?", _TRUNCATE );
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   err = strncpy_s_tester( "Howdy.", _TRUNCATE );
   printf( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   printf( "\nSecure template overload example:\n" );

   char dest[10];
   strncpy( dest, "very very very long", 15 );
   // With secure template overloads enabled (see #defines at
   // top of file), the preceding line is replaced by
   //    strncpy_s( dest, _countof(dest), "very very very long", 15 );
   // Instead of causing a buffer overrun, strncpy_s invokes
   // the invalid parameter handler.
   // If secure template overloads were disabled, strncpy would
   // copy 15 characters and overrun the dest buffer.
   printf( "    new contents of dest: '%s'\n", dest );
}

void myInvalidParameterHandler(
   const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);
}

int main( void )
{
   _invalid_parameter_handler oldHandler, newHandler;

   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);
   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   Examples();
}
```

```Output
Copying 4 chars of 'howdy' to 10-byte buffer dest
    new contents of dest: 'howd'

Copying 5 chars of 'howdy' to 10-byte buffer dest
    new contents of dest: 'howdy'

Copying 6 chars of 'howdy' to 10-byte buffer dest
    new contents of dest: 'howdy'

Destination buffer too small:

Copying 10 chars of 'Hi there!!' to 10-byte buffer dest
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''

Truncation examples:

Copying 'How do you do?' to 10-byte buffer dest with truncation semantics
    new contents of dest: 'How do yo'
    truncation did occur

Copying 'Howdy.' to 10-byte buffer dest with truncation semantics
    new contents of dest: 'Howdy.'
    truncation did not occur

Secure template overload example:
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''
```

## <a name="example"></a>範例

```C
// crt_strncpy_s_2.c
// contrasts strncpy and strncpy_s

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char a[20] = "test";
   char s[20];

   // simple strncpy usage:

   strcpy_s( s, 20, "dogs like cats" );
   printf( "Original string:\n   '%s'\n", s );

   // Here we can't use strncpy_s since we don't
   // want null termination
   strncpy( s, "mice", 4 );
   printf( "After strncpy (no null-termination):\n   '%s'\n", s );
   strncpy( s+5, "love", 4 );
   printf( "After strncpy into middle of string:\n   '%s'\n", s );

   // If we use strncpy_s, the string is terminated
   strncpy_s( s, _countof(s), "mice", 4 );
   printf( "After strncpy_s (with null-termination):\n   '%s'\n", s );

}
```

```Output
Original string:
   'dogs like cats'
After strncpy (no null-termination):
   'mice like cats'
After strncpy into middle of string:
   'mice love cats'
After strncpy_s (with null-termination):
   'mice'
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[strcat_s、wcscat_s、_mbscat_s](strcat-s-wcscat-s-mbscat-s.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
