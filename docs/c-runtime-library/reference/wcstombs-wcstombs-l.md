---
title: wcstombs、_wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: b5ee2a0e5636e9c1d1f3fc204b2b6cbf8b733d45
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498988"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs、_wcstombs_l

將一連串的寬字元轉換為對應的一連串多位元組字元。 這些函式已有更安全的版本，請參閱 [wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)。

## <a name="syntax"></a>語法

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*mbstr*<br/>
多位元組字元序列的位址。

*wcstr*<br/>
寬字元序列的位址。

*計數*<br/>
可以儲存在多位元組輸出字串的最大位元組數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果**wcstombs**成功轉換多位元組字元串, 它會傳回寫入多位元組輸出字串中的位元組數目, 不包括終止的 null (如果有的話)。 如果*mbstr*引數為**Null**, **wcstombs**會傳回目的字串所需的大小 (以位元組為單位)。 如果**wcstombs**遇到無法轉換成多位元組字元的寬字元, 則會傳回-1 轉換成**size_t**類型, 並將**errno**設定為**EILSEQ**。

## <a name="remarks"></a>備註

**Wcstombs**函數會將*wcstr*所指向的寬字元字串轉換為對應的多位元組字元, 並將結果儲存在*mbstr*陣列中。 *Count*參數表示可儲存在多位元組輸出字串中的最大位元組數目 (也就是*mbstr*的大小)。 轉換寬字元字串時通常不知道需要多少個位元組。 某些寬字元只需要輸出字串的一個位元組，有些則需要兩個。 如果輸入字串中每個寬字元的多位元組輸出字串中有兩個位元組 (包括寬字元 null), 則結果會保證符合。

如果**wcstombs**在之前或發生*計數*時遇到寬字元的 null 字元 (L ' \ 0 '), 則會將它轉換成8位0並停止。 因此, 只有在**wcstombs**在轉換期間遇到寬字元的 null 字元時, *mbstr*中的多位元組字元字串才會以 null 結束。 如果*wcstr*和*mbstr*所指向的序列重迭, 則**wcstombs**的行為會是未定義的。

如果*mbstr*引數為**Null**, **wcstombs**會傳回目的字串所需的大小 (以位元組為單位)。

**wcstombs**會驗證其參數。 如果*wcstr*為**Null**, 或*count*大於**INT_MAX**, 則此函式會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 函式會將**errno**設定為**EINVAL** , 並傳回-1。

**wcstombs**會針對任何與地區設定相關的行為使用目前的地區設定; **_wcstombs_l**相同, 不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明**wcstombs**函數的行為。

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
