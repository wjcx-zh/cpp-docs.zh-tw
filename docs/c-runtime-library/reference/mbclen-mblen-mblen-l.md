---
title: _mbclen、 mblen、 _mblen_l、 _mbclen_l
ms.date: 01/22/2019
apiname:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
ms.openlocfilehash: b7888b0b8c87a632dcbb63f54ade11080c7a309a
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702956"
---
# <a name="mbclen-mblen-mblenl-mbclenl"></a>_mbclen、 mblen、 _mblen_l、 _mbclen_l

取得長度，並判斷多位元組字元的有效性。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*C*<br/>
多位元組字元。

*mbstr*<br/>
多位元組字元位元組序列的位址。

*count*<br/>
要檢查的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbclen**傳回 1 或 2，根據多位元組字元*c*為 1 或 2 個位元組長。 不沒有傳回任何錯誤 **_mbclen**。 如果*mbstr*不**NULL**， **mblen**傳回長度，以位元組為單位的多位元組字元。 如果*mbstr*是**NULL**或是指向寬字元的 null 字元**mblen**會傳回 0。 當物件的*mbstr*點不會形成有效的多位元組字元，在第一個*計數*字元， **mblen**會傳回-1。

## <a name="remarks"></a>備註

**_Mbclen**函式會傳回長度，以位元組為單位的多位元組字元*c*。 如果*c*未指向隱含呼叫所決定之多位元組字元的前導位元組 **_ismbblead**，結果 **_mbclen**無法預期。

**mblen**傳回長度以位元組為單位*mbstr*如果它是有效的多位元組字元，並判斷多位元組字元的字碼頁相關聯的有效性。 **mblen**會檢查*計數*或更少個位元組內*mbstr*，但不是能超過**MB_CUR_MAX**位元組。

輸出值會受到**LC_CTYPE**地區設定分類設定; 請參閱[setlocale](setlocale-wsetlocale.md)如需詳細資訊。 這些功能，但不包含新版 **_l**尾碼針對此與地區設定相關行為使用目前的地區設定。 **_L**後面加上的版本的行為相同，但是它們使用改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

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

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
