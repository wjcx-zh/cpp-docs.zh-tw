---
title: mbstowcs、_mbstowcs_l
ms.date: 11/04/2016
apiname:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: b9178f64dd698ff517ea5b376ed19e97981c511d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156651"
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs、_mbstowcs_l

將多位元組字元序列轉換成對應的寬字元序列。 這些函式已有更安全的版本可用，請參閱 [mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)。

## <a name="syntax"></a>語法

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*wcstr*<br/>
寬字元序列的位址。

*mbstr*<br/>
以 Null 結束之多位元組字元序列的位址。

*count*<br/>
要轉換的多位元組字元數上限。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果**mbstowcs**成功轉換來源字串中，它會傳回已轉換的多位元組字元數。 如果*wcstr*引數是**NULL**，函式會傳回目的字串所需的大小 （以寬字元為單位）。 如果**mbstowcs**遇到無效的多位元組字元，則傳回-1。 如果傳回的值是*計數*，寬字元字串不是以 null 終止。

> [!IMPORTANT]
> 請確認*wcstr*並*mbstr*未重疊時，且*計數*正確反映要轉換的多位元組字元數。

## <a name="remarks"></a>備註

**Mbstowcs**函數會將最大數目*計數*多位元組字元所指向*mbstr*為對應寬字元字串取決於目前的地區設定。 它會儲存產生的寬字元字串所代表的位址*wcstr*。 結果是一連串的呼叫相似[mbtowc](mbtowc-mbtowc-l.md)。 如果**mbstowcs**之前或期間遇到單一位元組的 null 字元 ('\0')*計數*發生時，它會將轉換為寬字元 null 字元 (L '\0') 的 null 字元並停止。 因此在寬字元字串*wcstr*是以 null 終止才轉換期間遇到 null 字元。 如果指向的序列所*wcstr*並*mbstr*重疊，則行為是未定義。

如果*wcstr*引數是**NULL**， **mbstowcs**傳回轉換，不包括 null 結束字元所產生的寬字元數目。 來源字串必須以 Null 結束，才能傳回正確的值。 如果您需要產生的寬字元字串以 Null 結束，請將一個 Null 新增至傳回的值。

如果*mbstr*引數是**NULL**，或如果*計數*是 > **INT_MAX**，無效參數處理常式會叫用，中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，errno 會設定為**EINVAL**和函式會傳回-1。

**mbstowcs**針對任何地區設定相關行為; 會使用目前的地區設定 **_mbstowcs_l**完全相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
