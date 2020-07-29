---
title: strstr、wcsstr、_mbsstr、_mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 3ac4df470e40b35257495d51c5d2d0efdb9310af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233986"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr、wcsstr、_mbsstr、_mbsstr_l

傳回字串中第一次出現的搜尋字串指標。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中無法使用 `_mbsstr` 和 `_mbsstr_l`。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*字串*<br/>
以 Null 終止的待搜尋字串。

*strSearch*<br/>
以 Null 終止的待搜尋字串。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回*str*中第一次出現*strSearch*的指標，如果*strSearch*未出現在*str*中，則傳回 Null。 如果*strSearch*指向長度為零的字串，則函數會傳回*str*。

## <a name="remarks"></a>備註

函數會傳回 `strstr` *str*中第一次出現*strSearch*的指標。 搜尋不包含終止的 Null 字元。 `wcsstr` 為 `strstr` 的寬字元版本，而 `_mbsstr` 則為多位元組字元版本。 `wcsstr` 的引數和傳回值是寬字元字串；`_mbsstr` 的引數則是多位元組字元字串。 `_mbsstr` 會驗證其參數。 如果*str*或*strSearch*為 Null，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，會 `_mbsstr` 將設定 `errno` 為 EINVAL，並傳回0。 `strstr` 和 `wcsstr` 不會驗證其參數。 除此之外，這三個函式的行為相同。

> [!IMPORTANT]
> 這些函式可能帶來因緩衝區滿溢問題引發的威脅。 緩衝區滿溢問題可用來攻擊系統，因為它們允許執行任意程式碼，這會造成非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

在 C 中，這些函數會接受 **`const`** 第一個引數的指標。 在 C++ 中，可使用兩個多載。 接受指標的多載會傳回 **`const`** 的指標， **`const`** 接受非指標的版本會傳回 **`const`** 非的指標 **`const`** 。 如果 **`const`** 這些函式的和非版本皆可使用，則會定義宏 _CRT_CONST_CORRECT_OVERLOADS **`const`** 。 如果 **`const`** 這兩個 c + + 多載都需要非行為，請定義符號 _CONST_RETURN。

輸出值會受到 LC_CTYPE 的地區設定類別設定影響;如需詳細資訊，請參閱[setlocale、_wsetlocale](setlocale-wsetlocale.md)。 這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定;具有 **_l**尾碼的版本相同，不同之處在于它們會改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**n/a**|**n/a**|`_mbsstr_l`|**n/a**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> 或 \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的轉譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string：： find](../../standard-library/basic-string-class.md#find)<br/>
