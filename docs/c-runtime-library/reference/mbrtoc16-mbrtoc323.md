---
title: mbrtoc16、mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340971"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

將字串中的第一個 UTF-8 多位元組位元轉換為等效的 UTF-16 或 UTF-32 字元。

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
指向要轉換的uTF-8的**char16_t**或**等效**char32_t個。 如果為 null,則函數不儲存值。

*源*\
指向要轉換的 UTF-8 多位元組位元串。

*max_bytes*\
要檢查要轉換的字元的*來源*中的最大位元組數。 此參數應該是一個介於 1 和位元組數之間的值,包括任何空終止符,保留在*源*中。

*狀態*\
指向用於將 UTF-8 多位元組字串解釋為一個或多個輸出字元**的mbstate_t**轉換狀態物件的指標。

## <a name="return-value"></a>傳回值

成功時,傳回應用這些條件中的第一個條件的值,給定當前*狀態*值:

|值|條件|
|-----------|---------------|
|0|從*來源*轉換的下一*個max_bytes*或更少的字元對應於空寬字元,即*目標*不為空時儲存的值。<br /><br /> *狀態*包含初始移位狀態。|
|1 至*max_bytes*之間, 包括|返回的值是完成有效多位元位元元的*原始碼*位數。 如果*目標*不是 null,則儲存轉換的寬字元。|
|-3|如果*目標*不是 null,則以前呼叫函數產生的下一個寬字元已儲存在*目標*中。 此函數調用不會使用*源*中的位元組。<br /><br /> 當*源*指向需要多個寬字元來表示的 UTF-8 多位元組位元(例如,代理項對)時,將更新*狀態*值,以便下一個函數調用寫入附加字元。|
|-2|下一*個max_bytes*位元組表示不完整但可能有效的 UTF-8 多位元組位元元。 *目標*中未存儲任何值。 如果*max_bytes*為零,則可能發生此結果。|
|-1|發生了編碼錯誤。 下一*個max_bytes*或更少的位元組不會有助於完整和有效的 UTF-8 多位元組位元元。 *目標*中未存儲任何值。<br /><br /> **EILSEQ**儲存在**errno 中**,並且轉換狀態值*狀態*未指定。|

## <a name="remarks"></a>備註

**mbrtoc16**函數從*源*讀取最多*max_bytes*個字節,以查找第一個完整、有效的 UTF-8 多位元組字元,然後在*目標*中存儲等效的 UTF-16 字元。 如果字元需要多個 UTF-16 輸出字元(如代理項對),則*狀態*值設置為在下一次調用**mbrtoc16**時將下一個 UTF-16 字元儲存在*目標*中。 **mbrtoc32**函數相同,但輸出存儲為 UTF-32 字元。

如果*來源*為 null,這些函數傳回使用**NULL**參數為*來源*`""`(空,空終止字串)*進行的呼叫*的等效項,以及*max_bytes*的 1。 將忽略*目標*值和*max_bytes。*

如果*源*不為空,則函數從字串的開頭開始,並最多檢查*max_bytes*個字節以確定完成下一個 UTF-8 多字節字元(包括任何移位序列)所需的位元組數。 如果檢查的位元組包含有效且完整的 UTF-8 多位元組位元元,則該函數將該字元轉換為等效的 16 位元或 32 位元寬字元或字元。 如果*目標*不為空,則函數在目標中存儲第一個(可能也是唯一)結果字元。 如果需要其他輸出字元,則以*狀態*設置值,以便隨後對函數的調用輸出附加字元並返回值 -3。 如果不需要更多的輸出字元,則*狀態*設置為初始移位狀態。

要將非 UTF-8 多位元組字元轉換為 UTF-16 LE 字元,請使用[mbrtowc、mbtowc](mbrtowc.md)[或_mbtowc_l](mbtowc-mbtowc-l.md)函數。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**姆布托茨16** **,mbrtoc32**|\<uchar.h>|\<cuchar>|

如需其他相容性資訊，請參閱 [相容性](../compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../data-conversion.md)\
[現場](../locale.md)\
[多位元組字串序列的解釋](../interpretation-of-multibyte-character-sequences.md)\
[c16r墓,c32r墓](c16rtomb-c32rtomb1.md)\
[姆布爾托萬](mbrtowc.md)\
[姆布斯爾托茨](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
