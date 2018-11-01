---
title: _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
ms.date: 11/04/2016
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
apitype: DLLExport
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 6322f9511f0813eeaeb49383f49c73e361048cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573420"
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l

傳回指定計次數內的字元或位元組數目。

> [!IMPORTANT]
> **_mbsnbcnt**， **_mbsnbcnt_l**， **_mbsnccnt**，和 **_mbsnccnt_l**不能在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);

```

### <a name="parameters"></a>參數

*str*<br/>
要檢查的字串。

*count*<br/>
字元或檢查的位元組數目*str*。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsnbcnt**並 **_mbsnbcnt_l**傳回找到的位元組數目在第一個*count*的多位元組字元*str*。 **_mbsnccnt**並 **_mbsnccnt_l**傳回找到的字元數目在第一個*count*的位元組*str*。 Null 字元的檢查就碰到*str*已完成，傳回的 null 字元前找到的字元或位元組數目。 如果*str*組成少於*計數*字元或位元組，它們在字串中傳回的字元或位元組數目。 如果*計數*小於零，它們會傳回 0。 在舊版中，這些函式有傳回值的型別**int**而非**size_t**。

**_strncnt**傳回的字元數，在第一個*計數*個位元組的單一位元組字串*str*。 **_wcsncnt**傳回的字元數，在第一個*計數*寬字元的寬字元字串*str*。

## <a name="remarks"></a>備註

**_mbsnbcnt**並 **_mbsnbcnt_l**計算找到的位元組數目在第一個*計數*的多位元組字元*str*。 **_mbsnbcnt**並 **_mbsnbcnt_l**取代**mtob**應該用於取代**mtob**。

**_mbsnccnt**並 **_mbsnccnt_l**計算找到的字元數目在第一個*count*的位元組*str*。 如果 **_mbsnccnt**並 **_mbsnccnt_l**遇到雙位元組字元的第二個位元組的 null 字元，第一個位元組也視為 null 和未包含在傳回的計數值。 **_mbsnccnt**並 **_mbsnccnt_l**取代**btom**應該用於取代**btom**。

如果*str*是**NULL**指標是否*計數*是 0，則這些函式叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)， **errno**設定為**EINVAL**，且此函式會傳回 0。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|常式傳回的值|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|N/A|
|**_wcsncnt**|N/A|N/A|**_mbsnbcnt**|
|**_wcsncnt**|N/A|N/A|**_mbsnccnt**|
|N/A|N/A|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>輸出

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
