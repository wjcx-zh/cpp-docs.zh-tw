---
title: wctomb、_wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 162585ea866b4fb26cfaae3bc94345dadaba0baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367406"
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

*姆布查爾*<br/>
多位元組字元的位址。

*瓦查爾*<br/>
寬字元。

## <a name="return-value"></a>傳回值

如果**wctomb**將寬字元轉換為多位元組位元,它將返回寬字元中的位元組數(永遠不會大於**MB_CUR_MAX)。** 如果*wchar*是寬字元 null 字元 (L'\0'),**則 wctomb**返回 1。 如果目標指標*mbchar*為**NULL,****則 wctomb**返回 0。 如果轉換在目前區域設定中無法進行 **,wctomb**傳回 -1,errno 設定為**errno****EILSEQ**。

## <a name="remarks"></a>備註

**wctomb**函數將其*wchar*參數轉換為相應的多位元組位元,並將結果儲存在*mbchar*。 您可以在任何程式的任何點呼叫函式。 **wctomb**使用當前區域設置進行任何與區域設置相關的行為;**_wctomb_l**與**wctomb**相同,只是它使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**wctomb**驗證其參數。 如果*mbchar*為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則**errno**設置為**EINVAL,** 函數傳回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
