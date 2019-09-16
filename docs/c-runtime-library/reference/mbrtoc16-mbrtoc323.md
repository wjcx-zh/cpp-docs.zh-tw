---
title: mbrtoc16、mbrtoc323
ms.date: 11/04/2016
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
ms.openlocfilehash: 52bcec5911fdc2ecbb073ae0042777aa4eb2b963
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952453"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

將窄字串的第一個多位元組字元轉譯為對等的 UTF-16 或 UTF-32 字元。

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

*位置*<br/>
要轉換之多位元組字元的**char16_t**或**char32_t**的指標。 如果是 null，函式不會儲存值。

*source*<br/>
要轉換的多位元組字元字串的指標。

*max_bytes*<br/>
[*來源*] 中要檢查是否有要轉換之字元的最大位元組數目。 這應該是介於一個和多個位元組數目之間的值，包括任何 null 結束字元，以及*來源*中剩餘的。

*state*<br/>
**Mbstate_t**轉換狀態物件的指標，用來將多位元組字元串轉譯成一或多個輸出字元。

## <a name="return-value"></a>傳回值

成功時，會根據目前的*狀態*值，傳回適用下列條件的第一個值：

|值|條件|
|-----------|---------------|
|0|從*來源*轉換的下一個*max_bytes*或較少字元會對應至 null 寬字元，這是*目的地*不是 null 時所儲存的值。<br /><br /> *狀態*包含初始移位狀態。|
|介於1和*max_bytes*之間（含）|傳回的值是完成有效多位元組字元之*來源*的位元組數目。 如果*目的地*不是 null，則會儲存已轉換的寬字元。|
|-3|如果*目的地*不是 null，則先前對函式的呼叫所產生的下一個寬字元就已儲存在*目的地*中。 這個函式呼叫不會耗用任何來自*來源*的位元組。<br /><br /> 當*來源*指向需要多個寬字元來表示的多位元組字元時（例如，代理配對），則會更新*狀態值*，讓下一個函式呼叫寫出額外的字元。|
|-2|下一個*max_bytes*的位元組代表不完整但可能是有效的多位元組字元。 *目的地*中未儲存任何值。 如果*max_bytes*為零，就會發生這個結果。|
|-1|發生了編碼錯誤。 下一個*max_bytes*或較少的位元組不會參與完整且有效的多位元組字元。 *目的地*中未儲存任何值。<br /><br /> **EILSEQ**儲存在**errno**中，而且轉換狀態*狀態*為未指定。|

## <a name="remarks"></a>備註

**Mbrtoc16**函數會從*來源*讀取最多*max_bytes*個位元組，以尋找第一個完整且有效的多位元組字元，然後將對等的 utf-16 字元儲存在*目的地*中。 來源位元組會根據目前執行緒的多位元組地區設定解譯。 如果多位元組字元需要多個 UTF-16 輸出字元，例如代理配對，則在下一次呼叫**mbrtoc16**時，會將*state*值設定為將下一個 utf-16 字元儲存在*目的地*。 **Mbrtoc32**函式完全相同，但輸出會儲存為 UTF-32 字元。

如果*source*是 null，這些函式會傳回對等的呼叫使用**null**的引數 *（* *來源*為 **""** ）和1（用於*max_bytes*）。 *目的地*和*max_bytes*的傳遞值會被忽略。

如果*source*不是 null，函式會從字串的開頭開始，並檢查最多*max_bytes*個位元組，以判斷完成下一個多位元組字元所需的位元組數目，包括任何移位序列。 如果檢查的位元組包含有效且完整的多位元組字元，函式會將字元轉換成相等的 16 位元或 32 位元寬字元或字元。 如果*目的地*不是 null，則函式會將第一個（且可能只有）結果字元儲存在目的地中。 如果需要其他輸出字元，會在 [*狀態*] 中設定值，讓後續呼叫函式輸出其他字元，並傳回值-3。 如果不需要更多輸出字元，則 [*狀態*] 會設定為初始移位狀態。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**mbrtoc16**、 **mbrtoc32**|\<uchar.h>|\<cuchar>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
