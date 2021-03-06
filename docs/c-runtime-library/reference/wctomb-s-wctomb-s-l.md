---
title: wctomb_s、_wctomb_s_l
ms.date: 4/2/2020
api_name:
- _wctomb_s_l
- wctomb_s
- _o__wctomb_s_l
- _o_wctomb_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 63839f70fa334fadd961eb173343d1b406268cfd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910436"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s、_wctomb_s_l

將寬字元轉換為對應的多位元組字元。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wctomb、_wctomb_l](wctomb-wctomb-l.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*pRetValue*<br/>
位元組數目，或表示結果的代碼。

*mbchar*<br/>
多位元組字元的位址。

*sizeInBytes*<br/>
緩衝區*mbchar*的大小。

*wchar*<br/>
寬字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

錯誤狀況

|*mbchar*|*sizeInBytes*|傳回值|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Null**|>0|**EINVAL**|未修改|
|任意|>**INT_MAX**|**EINVAL**|未修改|
|任意|太小|**EINVAL**|未修改|

如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **wctomb**會傳回**EINVAL** ，並將**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**Wctomb_s**函式會將其*wchar*引數轉換為對應的多位元組字元，並將結果儲存在*mbchar*。 您可以在任何程式的任何點呼叫函式。

如果**wctomb_s**將寬字元轉換為多位元組字元，則會將寬字元中的位元組數目（絕不大於**MB_CUR_MAX**）放入*pRetValue*所指向的整數中。 如果*wchar*是寬字元的 null 字元（L ' \ 0 '）， **Wctomb_s**會將*pRetValue*填入1。 如果目標指標*mbchar*是**Null**， **wctomb_s**會將0放在*pRetValue*中。 如果在目前的地區設定中無法進行轉換， **wctomb_s**會將-1 放在*pRetValue*中。

**wctomb_s**會針對與地區設定相關的資訊，使用目前的地區設定;**_wctomb_s_l**是相同的，不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明**wctomb**函數的行為。

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[語言](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
