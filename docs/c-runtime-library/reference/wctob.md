---
title: wctob | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wctob
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
- wctob
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb45aec4b337a7b0aed1a51c50903ad76d2f916
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="wctob"></a>wctob

判斷寬字元是否對應至多位元組字元，並傳回其多位元組字元表示法。

## <a name="syntax"></a>語法

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>參數

*wchar*<br/>
要轉譯的值。

## <a name="return-value"></a>傳回值

如果**wctob**成功轉換的寬字元，它會傳回其多位元組字元表示法中，只有多位元組字元是剛好有一個位元組長度。 如果**wctob**遇到多位元組字元或多位元組字元不能轉換的寬字元不是正好一個位元組長，則傳回-1。

## <a name="remarks"></a>備註

**Wctob**函式將轉換的寬字元包含在*wchar*傳遞所傳回的對應多位元組字元**int**值，如果多位元組字元是剛好有一個位元組長度。

如果**wctob**不成功，而沒有對應的多位元組字元找不到，函式設定**errno**至**EILSEQ**並傳回-1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明的行為**wcstombs**函式。

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}

```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
