---
title: strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l
ms.date: 11/04/2016
apiname:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
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
ms.openlocfilehash: 059b0659a8088783c6d169288de486b41a6e8d82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468961"
---
# <a name="strpbrk-wcspbrk-mbspbrk-mbspbrkl"></a>strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l

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

*str*<br/>
以 Null 終止的搜尋字串。

*strCharSet*<br/>
以 Null 結束的字元集。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

讓指標回到第一個出現的任何字元*strCharSet*中*str*，或為 NULL 指標，如果兩個字串引數的任何字元的共通。

## <a name="remarks"></a>備註

`strpbrk`函式會傳回第一個出現的字元指標*str*屬於中的字元組*strCharSet*。 搜尋不包含終止的 Null 字元。

`wcspbrk` 和 `_mbspbrk` 是寬字元和多位元組字元版本的 `strpbrk`。 `wcspbrk` 的引數和傳回值是寬字元字串；`_mbspbrk` 的引數則是多位元組字元字串。

`_mbspbrk` 會驗證其參數。 如果*str*或是*strCharSet*是 NULL 時，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行`_mbspbrk`會傳回 NULL，而且設定`errno`EINVAL 到。 `strpbrk` 和 `wcspbrk` 不會驗證其參數。 除此之外，這三個函式的行為相同。

`_mbspbrk` 類似於 `_mbscspn`，不同之處在於 `_mbspbrk` 會傳回指標，而不是 [size_t](../../c-runtime-library/standard-types.md) 類型的值。

在 C 中，這些函式接受**const**第一個引數的指標。 在 C++ 中，可使用兩個多載。 取得指標的多載**const**傳回的指標**const**; 版本，採用的指標，非**const**將指標傳回至非**const**. 如果兩個使用者定義巨集 _CRT_CONST_CORRECT_OVERLOADS **const**和非位**const**這些函式的版本可供使用。 如果您需要非**const**兩個 c + + 多載，行為定義符號 _CONST_RETURN。

輸出值會受到地區設定; LC_CTYPE 分類設定的設定如需詳細資訊，請參閱 < [setlocale](setlocale-wsetlocale.md)。 這些功能，但不包含新版 **_l**後置字元在針對此與地區設定相關行為使用目前的地區設定; 具有版本 **_l**尾碼是完全相同，不同之處在於它會使用地區設定參數改為傳入。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**n/a**|**不適用**|`_mbspbrk_l`|**n/a**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`strpbrk`|\<string.h>|
|`wcspbrk`|\<string.h> 或 \<wchar.h>|
|`_mbspbrk`、 `_mbspbrk_l`|\<mbstring.h>|

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

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr、wcschr、_mbschr、_mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
