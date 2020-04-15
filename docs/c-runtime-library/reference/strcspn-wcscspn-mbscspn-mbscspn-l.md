---
title: strcspn、wcscspn、_mbscspn、_mbscspn_l
ms.date: 4/2/2020
api_name:
- _mbscspn_l
- wcscspn
- _mbscspn
- strcspn
- _o__mbscspn
- _o__mbscspn_l
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
- strcspn
- _mbscspn
- wcscspn
- _ftcscspn
- _tcscspn
helpviewer_keywords:
- strings [C++], searching
- ftcscspn function
- strcspn function
- _mbscspn function
- mbscspn_l function
- wcscspn function
- tcscspn function
- _ftcscspn function
- _mbscspn_l function
- mbscspn function
- _tcscspn function
ms.assetid: f73f51dd-b533-4e46-ba29-d05c553708a6
ms.openlocfilehash: 2ba3c2941736d185ad93c7c6e44cb83c82ebb478
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358881"
---
# <a name="strcspn-wcscspn-_mbscspn-_mbscspn_l"></a>strcspn、wcscspn、_mbscspn、_mbscspn_l

傳回字串中屬於字元集之第一個出現的字元索引。

> [!IMPORTANT]
> **_mbschr**和 **_mbschr_l**不能在 Windows 運行時中執行的應用程式中使用。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
size_t strcspn(
   const char *str,
   const char *strCharSet
);
size_t wcscspn(
   const wchar_t *str,
   const wchar_t *strCharSet
);
size_t _mbscspn(
   const unsigned char *str,
   const unsigned char *strCharSet
);
size_t _mbscspn_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*Str*<br/>
以 Null 結束的搜尋字串。

*斯特查塞特*<br/>
以 Null 結束的字元集。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

這些函數返回*str*中第一個字元的索引,該字元位於*strCharSet*中。 如果*str*中的字元中沒有一個在*strCharSet*中,則返回值是*str*的長度。

未保留表示錯誤的傳回值。

## <a name="remarks"></a>備註

**wcscspn**和 **_mbscspn**是寬字元和多位元組位元版本的**strcspn。** **wcscspn**的參數是寬字元字串;**_mbscspn**字串是多位元位元串。

**_mbscspn**驗證其參數。 如果*str*或*strCharSet*是空指標,則調用無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回 0 並將**errno**設定到**EINVAL**。 **strcspn**和**wcscspn**不驗證其參數。 除此之外，這三個函式的行為相同。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscspn**|**strcspn**|**_mbscspn**|**wcscspn**|
|n/a|n/a|**_mbscspn_l**|n/a|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**strcspn**|\<string.h>|
|**wcscspn**|\<string.h> 或 \<wchar.h>|
|**_mbscspn**, **_mbscspn_l**|\<mbstring.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_strcspn.c

#include <string.h>
#include <stdio.h>

void test( const char * str, const char * strCharSet )
{
   int pos = strcspn( str, strCharSet );
   printf( "strcspn( \"%s\", \"%s\" ) = %d\n", str, strCharSet, pos );
}

int main( void )
{
   test( "xyzbxz", "abc" );
   test( "xyzbxz", "xyz" );
   test( "xyzbxz", "no match" );
   test( "xyzbxz", "" );
   test( "", "abc" );
   test( "", "" );
}
```

```Output
strcspn( "xyzbxz", "abc" ) = 3
strcspn( "xyzbxz", "xyz" ) = 0
strcspn( "xyzbxz", "no match" ) = 6
strcspn( "xyzbxz", "" ) = 6
strcspn( "", "abc" ) = 0
strcspn( "", "" ) = 0
```

## <a name="see-also"></a>另請參閱

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
