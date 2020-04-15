---
title: strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l
ms.date: 4/2/2020
api_name:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
- _o__mbspbrk
- _o__mbspbrk_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
helpviewer_keywords:
- fstrpbrk function
- _ftcspbrk function
- _mbspbrk_l function
- strpbrk function
- _fstrpbrk function
- mbspbrk function
- characters [C++], scanning strings
- _tcspbrk function
- wcspbrk function
- ftcspbrk function
- character sets [C++], scanning strings for characters
- strings [C++], scanning
- tcspbrk function
- _mbspbrk function
- mbspbrk_l function
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
ms.openlocfilehash: ecdf896587096f0370351aac07cbd6be57257305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322175"
---
# <a name="strpbrk-wcspbrk-_mbspbrk-_mbspbrk_l"></a>strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l

掃描字串是否有指定字元集的字元。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中無法使用 `_mbspbrk` 和 `_mbspbrk_l`。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *strpbrk(
   const char *str,
   const char *strCharSet
); // C only
char *strpbrk(
   char *str,
   const char *strCharSet
); // C++ only
const char *strpbrk(
   const char *str,
   const char *strCharSet
); // C++ only
wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C only
wchar_t *wcspbrk(
   wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
const wchar_t *wcspbrk(
   const wchar_t *str,
   const wchar_t *strCharSet
); // C++ only
unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C only
unsigned char *_mbspbrk(
   unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
const unsigned char *_mbspbrk(
   const unsigned char *str,
   const unsigned char *strCharSet
); // C++ only
unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C only
unsigned char *_mbspbrk_l(
   unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
); // C++ only
const unsigned char *_mbspbrk_l(
   const unsigned char *str,
   const unsigned char* strCharSet,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*Str*<br/>
以 Null 終止的搜尋字串。

*斯特查塞特*<br/>
以 Null 結束的字元集。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果兩個字串參數沒有共同字元,則返回指向*strCharSet*中任何字元的第一個出現的指標,或NULL指標。 *str*

## <a name="remarks"></a>備註

函數`strpbrk`傳回指向*str*中屬於*strCharSet*中字元集的字元的第一次出現的指標。 搜尋不包含終止的 Null 字元。

`wcspbrk` 和 `_mbspbrk` 是寬字元和多位元組字元版本的 `strpbrk`。 `wcspbrk` 的引數和傳回值是寬字元字串；`_mbspbrk` 的引數則是多位元組字元字串。

`_mbspbrk` 會驗證其參數。 如果*str*或*strCharSet*為 NULL,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,`_mbspbrk`則傳回`errno`NULL 並設定到 EINVAL。 `strpbrk` 和 `wcspbrk` 不會驗證其參數。 除此之外，這三個函式的行為相同。

`_mbspbrk` 類似於 `_mbscspn`，不同之處在於 `_mbspbrk` 會傳回指標，而不是 [size_t](../../c-runtime-library/standard-types.md) 類型的值。

在 C 中,這些函數為第一個參數採用**const**指標。 在 C++ 中，可使用兩個多載。 帶指標到**const**的重載返回指向**const 的**指標。將指標指向非**const**的版本傳回指向非**const 的**指標。 如果這些函數的**const**版本和非**const**版本都可用,則定義宏_CRT_CONST_CORRECT_OVERLOADS。 如果兩C++重載都需要非**const**行為,請定義符號_CONST_RETURN。

輸出值受區域設置LC_CTYPE類別設置的影響;有關詳細資訊,請參閱[設定區域設定](setlocale-wsetlocale.md)。 沒有 **_l**後綴的這些函數的版本使用此與區域設置相關的行為的當前區域設置;具有 **_l**後綴的版本是相同的,只不過它使用傳入區域設置參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**不要適用**|**不要適用**|`_mbspbrk_l`|**不要適用**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`strpbrk`|\<string.h>|
|`wcspbrk`|\<string.h> 或 \<wchar.h>|
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strpbrk.c

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";
   char *result = NULL;

   // Return pointer to first digit in "string".
   printf( "1: %s\n", string );
   result = strpbrk( string, "0123456789" );
   printf( "2: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "3: %s\n", result++ );
   result = strpbrk( result, "0123456789" );
   printf( "4: %s\n", result );
}
```

```Output
1: The 3 men and 2 boys ate 5 pigs

2: 3 men and 2 boys ate 5 pigs

3: 2 boys ate 5 pigs

4: 5 pigs
```

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
