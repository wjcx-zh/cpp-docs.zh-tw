---
title: wcrtomb
ms.date: 11/04/2016
api_name:
- wcrtomb
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 8d2108b90f6884113f0bd974bf7aa634544adf5f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945227"
---
# <a name="wcrtomb"></a>wcrtomb

將寬字元轉換為其多位元組字元表示法。 此函式已有更安全的版本，請參閱 [wcrtomb_s](wcrtomb-s.md)。

## <a name="syntax"></a>語法

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*mbchar*<br/>
產生的多位元組轉換字元。

*wchar*<br/>
要轉換的寬字元。

*mbstate*<br/>
**Mbstate_t**物件的指標。

## <a name="return-value"></a>傳回值

傳回代表已轉換多位元組字元的必要位元組數，如果發生錯誤則為 -1。

## <a name="remarks"></a>備註

**Wcrtomb**函式會將寬字元（從包含在*mbstate*中的指定轉換狀態開始，從*wchar*中包含的值）轉換成*mbchar*所代表的位址。 傳回值是表示對應的多位元組字元所需的位元組數目，但不會傳回超過**MB_CUR_MAX**個位元組。

如果*mbstate*為 null，則會使用包含*mbchar*轉換狀態的內部**mbstate_t**物件。 如果字元順序*wchar*沒有對應的多位元組字元標記法，則會傳回-1，並將**Errno**設定為**EILSEQ**。

**Wcrtomb**函式與[wctomb、_wctomb_l](wctomb-wctomb-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用了**wcsrtombs**的後續呼叫（而不是**wcstombs**），應用程式會使用**wcsrlen**而非**wcsnlen**。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

只要目前線程中的函式在執行中且*mbstate*為**null 時，** **wcrtomb**函式就是多執行緒安全。

## <a name="example"></a>範例

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
