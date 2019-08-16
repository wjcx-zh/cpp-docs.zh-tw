---
title: wctomb、_wctomb_l
ms.date: 11/04/2016
apiname:
- _wctomb_l
- wctomb
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
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 6902ff925e49d894f70b0d7083b99388d5271d1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500736"
---
# <a name="wctomb-_wctomb_l"></a>wctomb、_wctomb_l

將寬字元轉換為對應的多位元組字元。 這些函式已有更安全的版本，請參閱 [wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)。

## <a name="syntax"></a>語法

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*mbchar*<br/>
多位元組字元的位址。

*wchar*<br/>
寬字元。

## <a name="return-value"></a>傳回值

如果**wctomb**將寬字元轉換為多位元組字元, 則會傳回寬字元中的位元組數目 (絕不大於**MB_CUR_MAX**)。 如果*wchar*是寬字元的 null 字元 (L ' \ 0 '), **wctomb**會傳回1。 如果目標指標*mbchar*是**Null**, **wctomb**會傳回0。 如果在目前的地區設定中無法進行轉換, **wctomb**會傳回-1, 而**errno**會設定為**EILSEQ**。

## <a name="remarks"></a>備註

**Wctomb**函數會將其*wchar*引數轉換為對應的多位元組字元, 並將結果儲存在*mbchar*。 您可以在任何程式的任何點呼叫函式。 **wctomb**會針對任何與地區設定相關的行為使用目前的地區設定; **_wctomb_l**與**wctomb**相同, 不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**wctomb**會驗證其參數。 如果*mbchar*為**Null**, 則會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, **errno**會設為**EINVAL** , 而函式會傳回-1。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明 wctomb 函式的行為。

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
