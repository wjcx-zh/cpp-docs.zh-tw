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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 06fb79ac050f4e1c357a76a782730cd72cbdadec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316928"
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

*Str*<br/>
以 Null 終止的待搜尋字串。

*strSearch*<br/>
以 Null 終止的待搜尋字串。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回指向*str*中第一次出現的*strSearch*的指標,如果*strSearch*未出現在 str 中,則傳回指向 NULL 的*指標*。 如果*strSearch*指向長度為零的字串,則函數將傳回*str*。

## <a name="remarks"></a>備註

函數`strstr`傳回指向 str*搜尋*第一次出現的*指標*。 搜尋不包含終止的 Null 字元。 `wcsstr` 為 `strstr` 的寬字元版本，而 `_mbsstr` 則為多位元組字元版本。 `wcsstr` 的引數和傳回值是寬字元字串；`_mbsstr` 的引數則是多位元組字元字串。 `_mbsstr` 會驗證其參數。 如果*str*或*strSearch*為 NULL,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則`_mbsstr`設置`errno`為 EINVAL 並返回 0。 `strstr` 和 `wcsstr` 不會驗證其參數。 除此之外，這三個函式的行為相同。

> [!IMPORTANT]
> 這些函式可能帶來因緩衝區滿溢問題引發的威脅。 緩衝區滿溢問題可用來攻擊系統，因為它們允許執行任意程式碼，這會造成非預期的提高權限。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

在 C 中,這些函數為第一個參數採用**const**指標。 在 C++ 中，可使用兩個多載。 將指標指向**const**的重載返回指向**const 的**指標。將指標指向非**const**的版本傳回指向非**const 的**指標。 如果這些函數的**const**版本和非**const**版本都可用,則定義宏_CRT_CONST_CORRECT_OVERLOADS。 如果兩C++重載都需要非**const**行為,請定義符號_CONST_RETURN。

輸出值受LC_CTYPE區域設置的影響;有關詳細資訊,請參閱[設定區域設置,_wsetlocale](setlocale-wsetlocale.md)。 這些函數的版本沒有 **_l**後綴使用此與區域設置相關的行為的當前區域設置;具有 **_l**後綴的版本是相同的,只是它們使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**不要適用**|**不要適用**|`_mbsstr_l`|**不要適用**|

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

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string:找到](../../standard-library/basic-string-class.md#find)<br/>
