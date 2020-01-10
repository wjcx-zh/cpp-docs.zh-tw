---
title: wcsrtombs
ms.date: 11/04/2016
api_name:
- wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: e6640a027b03b7aa0dceaf8e61af6cb43a44d6e0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945057"
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

*mbstr*<br/>
產生的已轉換多位元組字串的位址位置。

*wcstr*<br/>
間接指向要轉換的寬字元字串位置。

*計數*<br/>
要轉換的字元數。

*mbstate*<br/>
**Mbstate_t**轉換狀態物件的指標。

## <a name="return-value"></a>傳回值

傳回成功轉換的位元組數，不含 Null 終止 Null 位元組 (如果有的話)，如果發生錯誤則為 -1。

## <a name="remarks"></a>備註

**Wcsrtombs**函式會將寬字元字串（從*mbstate*中所包含的指定轉換狀態開始，從*wcstr*中間接指向的值）轉換成*mbstr*的位址。 每個字元的轉換會繼續，直到：遇到 null 終止的寬字元、遇到非對應的字元，或下一個字元會超過*計數*中包含的限制為止。 如果**wcsrtombs**在之前或發生*計數*時遇到寬字元的 null 字元（L ' \ 0 '），則會將它轉換成8位0並停止。

因此，只有在**wcsrtombs**在轉換期間遇到寬字元的 null 字元時， *mbstr*中的多位元組字元字串才會以 null 結束。 如果*wcstr*和*mbstr*所指向的序列重迭，則**wcsrtombs**的行為會是未定義的。 **wcsrtombs**會受到目前地區設定的 LC_TYPE 類別目錄所影響。

**Wcsrtombs**函式與[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用了**wcsrtombs**的後續呼叫（而不是**wcstombs**），應用程式會使用**wcsrlen**而非**wcsnlen**。

如果*mbstr*引數為**Null**， **wcsrtombs**會傳回目的字串所需的大小（以位元組為單位）。 如果*mbstate*為 null，則會使用內部**mbstate_t**轉換狀態。 如果字元順序*wchar*沒有對應的多位元組字元標記法，則會傳回-1，並將**Errno**設定為**EILSEQ**。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Wcsrtombs**函數是多執行緒安全，只要目前線程中的函式在執行此函式，而且*mbstate*不是 null 時，就會呼叫**setlocale** 。

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
