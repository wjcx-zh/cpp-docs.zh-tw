---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328064"
---
# <a name="wcsrtombs"></a>wcsrtombs

將寬字元字串轉換為其多位元組字元字串表示法。 此函式已有更安全的版本，請參閱 [wcsrtombs_s](wcsrtombs-s.md)。

## <a name="syntax"></a>語法

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*姆布斯特*<br/>
產生的已轉換多位元組字串的位址位置。

*wc斯特*<br/>
間接指向要轉換的寬字元字串位置。

*count*<br/>
要轉換的字元數。

*mbstate*<br/>
指向**mbstate_t**轉換狀態物件的指標。

## <a name="return-value"></a>傳回值

傳回成功轉換的位元組數，不含 Null 終止 Null 位元組 (如果有的話)，如果發生錯誤則為 -1。

## <a name="remarks"></a>備註

**wcsrtombs**函數將一串寬字元(從*mbstate*中包含的指定轉換狀態開始)從間接指向*wcstr*的值轉換為*mbstr*的位址。 每個字元的轉換將繼續,直到:遇到空終止寬字元後,遇到非對應字元或下一個字元將超過*計數*中包含的限制。 如果**wcsrtombs**在*計數*發生之前或發生計數時遇到寬字元 null 字元 (L』_0'),它將轉換為 8 位 0 並停止。

因此 *,mbstr*處的多位元組字串僅在**wcsrtombs**在轉換期間遇到寬字元 null 字元時才為 null 終止。 如果*wcstr*和*mbstr*指向的序列重疊,則**wcsrtombs**的行為未定義。 **wcsrtombs**受當前區域設置LC_TYPE類別的影響。

**wcsrtombs**函數不同於[wcstombs,_wcstombs_l](wcstombs-wcstombs-l.md)它的可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如,如果使用隨後對**wcsrtombs**的調用而不是**wcstombs,** 則應用程式將使用**wcsrlen**而不是**wcsnlen。**

如果*mbstr*參數為**NULL,****則 wcsrtombs**返回目標字串的所需大小(以位元組為單位)。 如果*mbstate*為 null,則使用內部**mbstate_t**轉換狀態。 如果字元序列*wchar*沒有相應的多位元位元表示形式,則傳回 -1 並將**errno**設定為**EILSEQ**。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

**wcsrtombs**函數是多線程安全的,只要當前線程呼叫中沒有函數在執行任務時**設置局部性**,*並且mbstate*不為null。

## <a name="example"></a>範例

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

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
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
