---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328113"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

將寬字元字串轉換為其多位元組字元字串表示法。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcsrtombs](wcsrtombs.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*p 傳回值*<br/>
轉換的字串(包括空終止符)的大小(以位元組為單位)。

*姆布斯特*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*大小位元組*<br/>
*mbstr*緩衝區的大小(以位元組為單位)。

*wc斯特*<br/>
指向要轉換的寬字元字串。

*count*<br/>
要存儲在*mbstr*緩衝區或[_TRUNCATE](../../c-runtime-library/truncate.md)的最大位元組數。

*mbstate*<br/>
指向**mbstate_t**轉換狀態物件的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值與**差錯**|
|---------------------|------------------------------|
|*mbstr*為**NULL,***大小為*> 0|**埃因瓦爾**|
|*wcstr*為**NULL**|**埃因瓦爾**|
|目標緩衝區太小,無法包含轉換後的字串(除非*計數***_TRUNCATE;** 請參閱下面的備註 )|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將返回錯誤代碼並設置表中指示的**errno。**

## <a name="remarks"></a>備註

**wcsrtombs_s**函數將*wcstr*指向的寬字元字串轉換為儲存在*mbstr*指向的緩衝區中的多位元元符,使用*mbstate*中包含的轉換狀態。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在*mbstr*緩衝區中的位元組數等於*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值,則**wcsrtombs_s**轉換與目標緩衝區中一樣多的字串,同時仍為空終止符留出空間。

如果**wcsrtombs_s**成功轉換源字串,它將轉換後的字串(包括空終止符)的大小放入 *&#42;pReturnValue(* 前提是*pReturnValue*不是**NULL)。** 即使*mbstr*參數為**NULL,** 並提供一種確定所需緩衝區大小的方法,也會發生這種情況。 注意,如果*mbstr*為**NULL,** 則忽略*計數*。

如果**wcsrtombs_s**遇到寬字元,它不能轉換為多位元組位元,它會在*\*pReturnValue*中放置 -1,將目標緩衝區設定為空字串,將**errno**設定到**EILSEQ,** 並傳回**EILSEQ**。

如果*wcstr*和*mbstr*指向的序列重疊,則**wcsrtombs_s**的行為未定義。 **wcsrtombs_s**受當前區域設置的LC_TYPE類別的影響。

> [!IMPORTANT]
> 確保*wcstr*和*mbstr*不重疊,並且*該計數*正確反映要轉換的寬字元數。

**wcsrtombs_s**函數不同於[wcstombs_s,_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)其可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如,如果使用後續對**wcsrtombs_s**的調用而不是**wcstombs_s**,則應用程式將使用**wcsrlen**而不是**wcslen。**

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

只要執行此函數時當前線程呼叫中沒有函數**設置局部性**,*並且 mbstate*為空 **,wcsrtombs_s**函數是多線程安全的。

## <a name="example"></a>範例

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
