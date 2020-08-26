---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 2e0e0ec9d92744fc904bae5ac7f91db8049de4cd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842113"
---
# <a name="mbrlen"></a>mbrlen

判斷完成目前地區設定的多位元組字元所需的位元組數目，並提供在多位元組字元中間重新啟動的功能。

## <a name="syntax"></a>語法

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>參數

*str*<br/>
多位元組字元字串中要檢查的下一個位元組指標。

*計數*<br/>
要檢查的最大位元組數目。

*mbstate*<br/>
*Str*初始位元組之目前移位狀態的指標。

## <a name="return-value"></a>傳回值

下列其中一個值：

| 值 | 描述 |
|--|--|
| 0 | 下一個 *計數* 或較少的位元組會完成代表寬 null 字元的多位元組字元。 |
| 1到 *計數*（含） | 下一個 *計數* 或較少的位元組會完成有效的多位元組字元。 傳回的值是完成多位元組字元的位元組數目。 |
| (size_t)(-2) | 下一個 *計數* 位元組會導致不完整但可能有效的多位元組字元，而且所有的 *計數* 位元組都已處理。 |
| (size_t)(-1) | 發生編碼錯誤。 下一個 *計數* 或較少的位元組不會構成完整且有效的多位元組字元。 在此情況下， **errno** 會設為 EILSEQ，而且不會指定 *mbstate* 中的轉換狀態。 |

## <a name="remarks"></a>備註

**Mbrlen**函式會檢查最多從*str*所指向位元組開始的*計數*位元組，以判斷完成下一個多位元組字元所需的位元組數目，包括任何移位序列。 這相當於呼叫， `mbrtowc(NULL, str, count, &mbstate)` 其中 *mbstate* 是使用者提供的 **mbstate_t** 物件，或程式庫所提供的靜態內建物件。

**Mbrlen**函式會儲存並使用*mbstate*參數中不完整多位元組字元的移位狀態。 如此一來， **mbrlen** 就能夠在多位元組字元中間重新開機（如果需要的話），並檢查最多 *計數* 的位元組。 如果 *mbstate* 為 null 指標，則 **mbrlen** 會使用內部靜態 **mbstate_t** 物件來儲存移位狀態。 由於內部 **mbstate_t** 物件不是安全線程，因此建議您一律配置並傳遞您自己的 *mbstate* 參數。

**Mbrlen**函式與可重新開機的[_mbclen、mblen 和 _mblen_l](mbclen-mblen-mblen-l.md)不同。 對相同或其他可重新開機函式的後續呼叫，移位狀態會儲存在 *mbstate* 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，應用程式應該使用 **wcsrlen** ，而不是使用 **wcslen** （如果使用 **wcsrtombs** 的後續呼叫，而不是 **wcstombs**）。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|不適用|不適用|**mbrlen**|不適用|

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此範例顯示多位元組字元的解讀如何取決於目前的字碼頁，並示範 **mbrlen**的繼續功能。

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
