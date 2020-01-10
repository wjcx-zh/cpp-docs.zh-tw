---
title: mbrtoc16、mbrtoc323
ms.date: 10/22/2019
api_name:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 793eadf433f3117d89b4f0dc7c8397762405406b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811130"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

將字串中的第一個 UTF-8 多位元組字元轉換為對等的 UTF-16 或 UTF-32 字元。

## <a name="syntax"></a>語法

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>參數

*目的地*\
**Char16_t**或**char32_t**的指標，相當於要轉換的 utf-8 多位元組字元。 如果是 null，函數不會儲存值。

*來源*\
要轉換之 UTF-8 多位元組字元字串的指標。

*max_bytes*\
[*來源*] 中要檢查是否有要轉換之字元的最大位元組數目。 這個引數應該是介於一個和多個位元組數目之間的值，包括任何 null 結束字元，以及*來源*中剩餘的。

*狀態*\
**Mbstate_t**轉換狀態物件的指標，用來將 utf-8 多位元組字元串轉譯成一或多個輸出字元。

## <a name="return-value"></a>傳回值

成功時，會根據目前的*狀態*值，傳回適用下列條件的第一個值：

|值|條件|
|-----------|---------------|
|0|從*來源*轉換的下一個*max_bytes*或較少字元會對應至 null 寬字元，這是*目的地*不是 null 時所儲存的值。<br /><br /> *狀態*包含初始移位狀態。|
|介於1和*max_bytes*之間（含）|傳回的值是完成有效多位元組字元之*來源*的位元組數目。 如果*目的地*不是 null，則會儲存已轉換的寬字元。|
|-3|如果*目的地*不是 null，則先前對函式的呼叫所產生的下一個寬字元就已儲存在*目的地*中。 這個函式呼叫不會耗用任何來自*來源*的位元組。<br /><br /> 當*來源*指向需要多個寬字元來表示的 utf-8 多位元組字元時（例如，代理配對），會更新*狀態值*，讓下一個函式呼叫寫出額外的字元。|
|-2|下一個*max_bytes*的位元組代表不完整但可能是有效的 utf-8 多位元組字元。 *目的地*中未儲存任何值。 如果*max_bytes*為零，就會發生這個結果。|
|-1|發生了編碼錯誤。 下一個*max_bytes*或較少的位元組不會對完整且有效的 utf-8 多位元組字元造成影響。 *目的地*中未儲存任何值。<br /><br /> **EILSEQ**儲存在**errno**中，而且轉換狀態值的*狀態*為未指定。|

## <a name="remarks"></a>備註

**Mbrtoc16**函數會從*來源*讀取最多*max_bytes*個位元組，以尋找第一個完整且有效的 utf-8 多位元組字元，然後將對等的 utf-16 字元儲存在*目的地*中。 如果字元需要多個 UTF-16 輸出字元，例如代理配對，則在下一次呼叫**mbrtoc16**時，會將*state*值設定為將下一個 utf-16 字元儲存在*目的地*。 **Mbrtoc32**函式完全相同，但輸出會儲存為 UTF-32 字元。

如果*source*是 null，這些函式會傳回對來源使用**null**的引數、`""` （空的、以 null 結束的字串）做為*source*的*呼叫，以及*1 *max_bytes*的對等。 *目的地*和*max_bytes*的傳遞值會被忽略。

如果*source*不是 null，函式會從字串的開頭開始，並檢查最多*max_bytes*個位元組，以判斷完成下一個 utf-8 多位元組字元所需的位元組數目，包括任何移位序列。 如果檢查的位元組包含有效且完整的 UTF-8 多位元組字元，則函式會將字元轉換為相等的16位或32位寬字元或字元。 如果*目的地*不是 null，則函式會將第一個（且可能只有）的結果字元儲存在目的地中。 如果需要其他輸出字元，會在 [*狀態*] 中設定值，讓後續呼叫函式輸出其他字元，並傳回值-3。 如果不需要更多輸出字元，則 [*狀態*] 會設定為初始移位狀態。

若要將非 UTF-8 多位元組字元轉換成 UTF-16 LE 字元，請使用[解譯 mbrtowc](mbrtowc.md)、 [mbtowc 或 _mbtowc_l](mbtowc-mbtowc-l.md)函式。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**mbrtoc16**、 **mbrtoc32**|\<uchar.h>|\<cuchar>|

如需相容性的詳細資訊，請參閱[相容性](../compatibility.md)。

## <a name="see-also"></a>請參閱

[資料轉換](../data-conversion.md)\
[Locale](../locale.md)\
[多位元組字元序列的解讀](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
