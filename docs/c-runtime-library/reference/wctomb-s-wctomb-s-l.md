---
title: wctomb_s、_wctomb_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
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
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7812eeb234676b84d9f6e8077c895e958dd45281
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="wctombs-wctombsl"></a>wctomb_s、_wctomb_s_l

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
緩衝區的大小*mbchar*。

*wchar*<br/>
寬字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功則為零，失敗則為錯誤碼。

錯誤狀況

|*mbchar*|*sizeInBytes*|傳回值|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|未修改|
|任何|>**INT_MAX**|**EINVAL**|未修改|
|任何|太小|**EINVAL**|未修改|

如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若要繼續，允許執行**wctomb**傳回**EINVAL**並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

**Wctomb_s**函式將其*wchar*對應的多位元組字元的引數，並將儲存在結果*mbchar*。 您可以在任何程式的任何點呼叫函式。

如果**wctomb_s**將轉換的寬字元的多位元組字元，它會將放置的位元組數 (不大於**MB_CUR_MAX**) 中成為整數所指向的寬字元*pRetValue*。 如果*wchar*是寬字元的 null 字元 (L '\0')， **wctomb_s**填滿*pRetValue* 1。 如果目標指標*mbchar*是 NULL， **wctomb_s**置於 0 *pRetValue*。 如果轉換不可能在目前的地區設定， **wctomb_s** -1 會置於*pRetValue*。

**wctomb_s**使用目前的地區設定進行地區設定相關資訊。**_wctomb_s_l**是完全相同，不同之處在於它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明的行為**wctomb**函式。

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
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
