---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: ee25b18bfbb86b34e46c8c6776e8ab83157613e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328174"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

將寬字元轉換為其多位元組字元表示法。 這是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcrtomb](wcrtomb.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*p 傳回值*<br/>
傳回寫入的位元組數目，如果發生錯誤則為 -1。

*姆布查爾*<br/>
產生的多位元組轉換字元。

*大小Ofmbchar*<br/>
*mbchar*變數的大小(以位元組為單位)。

*瓦查爾*<br/>
要轉換的寬字元。

*mbstate*<br/>
指向**mbstate_t**物件的指標。

## <a name="return-value"></a>傳回值

如果發生錯誤,則返回零或**errno**值。

## <a name="remarks"></a>備註

**wcrtomb_s**函數將寬字元(從*mbstate*中包含的指定轉換狀態開始)從*wchar*中包含的值轉換為*mbchar*表示的位址。 *pReturnValue*值將是轉換的位元組數,但如果發生錯誤,則不超過**MB_CUR_MAX**位元組數或 -1。

如果*mbstate*為 null,則使用內部**mbstate_t**轉換狀態。 如果*wchar*中包含的字元沒有對多位元位元,*則 pReturnValue*的值為 -1,並且函數會傳回**EILSEQ**的**errno**值 。

**wcrtomb_s**功能不同於[wctomb_s,_wctomb_s_l](wctomb-s-wctomb-s-l.md)它的可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如,如果使用後續對**wcsrtombs_s**的調用而不是**wcstombs_s**,則應用程式將使用**wcsrlen**而不是**wcslen。**

C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

只要當前線程調用中沒有函數在執行任務時**設置局部性**,*並且 mbstate*為空 **,wcrtomb_s**函數是多線程安全的。

## <a name="example"></a>範例

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
