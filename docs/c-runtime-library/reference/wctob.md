---
title: wctob
ms.date: 4/2/2020
api_name:
- wctob
- _o_wctob
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 420071680c3dc273f6df637cf44273f2c24bd64c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320434"
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

*瓦查爾*<br/>
要轉譯的值。

## <a name="return-value"></a>傳回值

如果**wctob**成功轉換寬字元,則僅當多位元位元元正好是一個字節長時,它才會返回其多位元組字元表示形式。 如果**wctob**遇到寬字元,它不能轉換為多位元組位元元,或者多位元組位元符不完全是一個字節長,它將返回 -1。

## <a name="remarks"></a>備註

如果多位元元元正好是一個字節長,**則 wctob**函數將*wchar*中包含的寬字元轉換為返回**int**值傳遞的相應多位元字元。

如果**wctob**不成功,並且未找到相應的多位元組位元,則函數將**errno**設置到**EILSEQ**並返回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明瞭**wcstombs**函數的行為。

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
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
