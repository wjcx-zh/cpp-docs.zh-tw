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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340995"
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

*Str*<br/>
多位元組字元字串中要檢查的下一個位元組指標。

*count*<br/>
要檢查的最大位元組數目。

*mbstate*<br/>
指向 str 的初始位元位元的*指標*。

## <a name="return-value"></a>傳回值

下列其中一個值：

|||
|-|-|
0|下一*個計數*或更少位元組完成表示寬空字元的多位元組位元元。
1*計數*, 包括|下一*個計數*或更少位元組完成有效的多位元組位元元。 傳回的值是完成多位元組字元的位元組數目。
(size_t)(-2)|下一個*計數*位元組有助於不完整但可能有效的多位元組位元元,並且所有*計數*位元組都已處理。
(size_t)(-1)|發生編碼錯誤。 下一個*計數*或更少的位元組不會貢獻為完整且有效的多位元組位元元。 在這種情況下 **,errno**設置為 EILSEQ,並且未指定*mbstate*中的轉換狀態。

## <a name="remarks"></a>備註

**mbrlen**函數最多檢查*計數*位元組,以*str*指向的位元組開頭,以確定完成下一個多位元元元(包括任何移位序列)所需的位元組數。 它等效於`mbrtowc(NULL, str, count, &mbstate)`*mbstate*是使用者提供的**mbstate_t**物件的調用,或者庫提供的靜態內部物件。

**mbrlen**函數保存並使用*mbstate*參數中不完整的多位元組位元符元的移位狀態。 這使**mbrlen**能夠在需要時在多位元元元中間重新啟動,檢查最多*計數*位元組。 如果*mbstate*是空指標,**則 mbrlen**使用內部靜態**mbstate_t**物件來存儲移位狀態。 由於內部**mbstate_t**物件不是線程安全的,因此我們建議您始終分配並傳遞自己的*mbstate*參數。

**mbrlen**函數不同於[_mbclen,mblen,_mblen_l](mbclen-mblen-mblen-l.md)它的可重新啟動性。 移位狀態以*mbstate*存儲,以便隨後調用相同或其他可重新啟動函數。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如,如果使用後續對**wcsrtombs**的調用而不是**wcstombs,** 則應用程式應使用**wcsrlen**而不是**wcslen。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|不適用|不適用|**mbrlen**|不適用|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此示例演示如何對多位元位元元的解釋依賴於當前代碼頁,並演示**了mbrlen**的復原功能。

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

[字串動作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
