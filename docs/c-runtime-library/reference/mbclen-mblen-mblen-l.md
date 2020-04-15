---
title: _mbclen、mblen、_mblen_l、_mbclen_l
description: 描述 Microsoft C 執行時庫 (CRT) _mbclen、mblen、_mblen_l 和_mbclen_l功能。
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341114"
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

*C*\
多位元組字元。

*姆布斯特*\
多位元組字元位元組序列的位址。

*計數*\
要檢查的位元組數目。

*現場*\
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbclen**和 **_mbclen_l**返回 1 或 2,根據多位元組位元*符符 c*的長度。 無論*c*是否為多位元組,函數始終返回 1 表示 UTF-8。 **_mbclen**沒有錯誤返回。

如果*mbstr*不是**NULL,****則 mblen**和 **_mblen_l**返回多位元組位元符元的長度(以位元組為單位)。 **mblen**和 **_mblen_l**函數在 UTF-8 上正常工作,並且可能返回介於 1 和 3 之間的值。 當*mbstr*為**NULL(** 或指向寬字元空字元)時 **,mblen**和 **_mblen_l**返回 0。 *mbstr*指向的物件必須在第一個*計數*字元中形成有效的多位元組字元,或**mblen**和 **_mblen_l**返回 -1。

## <a name="remarks"></a>備註

**_mbclen**函數返回多位元位元*元符元 c*的長度(以位元組為單位)。 如果*c*不指向多位位位位元元的引線位元組(由對[_ismbblead](ismbblead-ismbblead-l.md)的隱式呼叫確定,**則_mbclen**的結果是不可預知的。

**如果長度**為*mbstr,* 則返回長度(mbstr)。如果長度是有效的多位元組字元。 它還確定與代碼頁關聯的多位元組字元有效性。 **mblen**檢查*mbstr*中包含的*計數*或更少位元組,但不超過**MB_CUR_MAX**位元組。

輸出值受區域設置**LC_CTYPE**類別設置的影響。 沒有 **_l**後綴的這些函數的版本使用此與區域設置相關的行為的當前區域設置。 **_l**後綴版本具有相同的行為,但它們使用傳入區域設置參數。 關於詳細資訊,請參考[設定區域設定](setlocale-wsetlocale.md)[與區域設定](../../c-runtime-library/locale.md)。

**_mbclen、_mblen_l**和 **_mbclen_l**是特定於 Microsoft 的,而不是標準 **_mblen_l**C 庫的一部分。 我們不建議您在需要便攜式代碼的地方使用它們。 對於標準 C 相容性,請使用**mblen**或**mbrlen。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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

## <a name="see-also"></a>另請參閱

[字元類別](../../c-runtime-library/character-classification.md)\
[現場](../../c-runtime-library/locale.md)\
[多位元組字串序列的解釋](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy,_mbccpy_l](mbccpy-mbccpy-l.md)\
[姆布倫](mbrlen.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
