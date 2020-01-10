---
title: _mbclen、mblen、_mblen_l、_mbclen_l
description: 描述 Microsoft C 執行時間程式庫（CRT） _mbclen、mblen、_mblen_l 和 _mbclen_l 函數。
ms.date: 01/08/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: 4676d850448af386a5aface69f616a4ac6f85cbf
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755075"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen、mblen、_mblen_l、_mbclen_l

取得長度，並判斷多位元組字元的有效性。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*c*\
多位元組字元。

*mbstr*\
多位元組字元位元組序列的位址。

*計數*\
要檢查的位元組數目。

*地區*設定\
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbclen**和 **_mbclen_l**會根據多位元組字元*c*的長度傳回1或2。 函式一律會傳回1（針對 UTF-8），不論*c*是否為多位元組。 **_Mbclen**不會傳回錯誤。

如果*mbstr*不是**Null**， **mblen**和 **_mblen_l**會傳回多位元組字元的長度（以位元組為單位）。 **Mblen**和 **_mblen_l**函式會在 utf-8 上正常運作，而且可能會傳回介於1到3之間的值。 當*mbstr*為**null**時（或指向寬字元的 Null 字元）， **mblen**和 **_mblen_l**會傳回0。 *Mbstr*指向的物件必須在第一個*計數*字元內形成有效的多位元組字元，否則**mblen**和 **_mblen_l**會傳回-1。

## <a name="remarks"></a>備註

**_Mbclen**函數會傳回多位元組字元*c*的長度（以位元組為單位）。 如果*c*未指向多位元組字元的前導位元組（由[_ismbblead](ismbblead-ismbblead-l.md)的隱含呼叫所決定），則 **_mbclen**的結果會是無法預測的。

如果**mblen**是有效的多位元組字元，則會傳回*mbstr*的長度（以位元組為單位）。 它也會決定與字碼頁相關聯的多位元組字元有效性。 **mblen**會檢查*mbstr*中包含的*計數*或較少的位元組，但不超過**MB_CUR_MAX**個位元組。

輸出值會受到地區設定的**LC_CTYPE**類別設定影響。 這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定。 **_L**尾碼的版本行為相同，但卻改用傳入的地區設定參數。 如需詳細資訊，請參閱[setlocale](setlocale-wsetlocale.md)和[地區](../../c-runtime-library/locale.md)設定。

**_mbclen**、 **_mblen_l**和 **_mbclen_l**是 Microsoft 特有的，而不是標準 C 程式庫的一部分。 我們不建議您在想要可攜的程式碼的地方使用它們。 針對標準 C 相容性，請改用**mblen**或**mbrlen** 。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|巨集或內嵌函式的對應|**_mbclen**|巨集或內嵌函式的對應|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>請參閱

[字元分類](../../c-runtime-library/character-classification.md)\
[Locale](../../c-runtime-library/locale.md)\
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
