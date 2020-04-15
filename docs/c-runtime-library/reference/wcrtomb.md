---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: eda857b80404aebe46b090741e0b56d4fe692f34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328102"
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

*姆布查爾*<br/>
產生的多位元組轉換字元。

*瓦查爾*<br/>
要轉換的寬字元。

*mbstate*<br/>
指向**mbstate_t**物件的指標。

## <a name="return-value"></a>傳回值

傳回代表已轉換多位元組字元的必要位元組數，如果發生錯誤則為 -1。

## <a name="remarks"></a>備註

**wcrtomb**函數將寬字元(從*mbstate*中包含的指定轉換狀態開始)從*wchar*中包含的值轉換為*mbchar*表示的位址。 返回值是表示相應多位元位元元所需的位元組數,但不會返回超過**MB_CUR_MAX**位元組。

如果*mbstate*為 null,則使用包含*mbchar*轉換狀態的內部**mbstate_t**物件。 如果字元序列*wchar*沒有相應的多位元位元表示形式,則傳回 -1 並將**errno**設定為**EILSEQ**。

**wcrtomb**函數不同於[wctomb,_wctomb_l](wctomb-wctomb-l.md)其可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如,如果使用隨後對**wcsrtombs**的調用而不是**wcstombs,** 則應用程式將使用**wcsrlen**而不是**wcsnlen。**

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

**wcrtomb**函數是多線程安全的,只要此函數執行時當前線程呼叫中沒有函數**設置局部性**,並且*mbstate*為null。

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
