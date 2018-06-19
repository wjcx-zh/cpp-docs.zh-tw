---
title: mbrtoc16、mbrtoc323 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- mbrtoc16
- mbrtoc32
apilocation:
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
apitype: DLLExport
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs:
- C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a12e90f9a4bc0cc27df421c27d77a1b9b69334b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405298"
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

*目的地*<br/>
指標**char16_t**或**char32_t**来轉換的多位元組字元的對等。 如果是 null，函式不會儲存值。

*來源*<br/>
要轉換的多位元組字元字串的指標。

*max_bytes*<br/>
中的位元組數目上限*來源*來檢查是否要轉換的字元。 這應該是一個功能，包括任何 null 結束字元中, 剩餘的位元組數目之間的值*來源*。

*state*<br/>
指標**mbstate_t**轉換狀態物件，用來解譯為一或多個輸出字元的多位元組字串。

## <a name="return-value"></a>傳回值

成功時會傳回的第一個值會套用這些條件，提供目前*狀態*值：

|值|條件|
|-----------|---------------|
|0|下一步 *max_bytes*或從較少的字元轉換*來源*對應到 null 寬字元，如果儲存的值*目的地*不是 null。<br /><br /> *狀態*包含初始移位狀態。|
|介於 1 和*max_bytes*(含） 之間|傳回的值是的位元組數*來源*，完成有效多位元組字元。 如果儲存已轉換的寬字元*目的地*不是 null。|
|-3|已儲存在先前的呼叫函式所產生的下一個寬字元*目的地*如果*目的地*不是 null。 從任何位元組*來源*所使用的這個呼叫函式。<br /><br /> 當*來源*指向多位元組字元需要多個寬字元來代表 （例如，surrogate 字組），然後在*狀態*值會更新，讓下一個函式呼叫寫 出額外的字元。|
|-2|下一步 *max_bytes*位元組代表不完整但可能有效的多位元組字元。 沒有值儲存在*目的地*。 如果，可能會發生這個結果*max_bytes*為零。|
|-1|發生了編碼錯誤。 下一步 *max_bytes*或較少位元組不會產生完整且有效的多位元組字元。 沒有值儲存在*目的地*。<br /><br /> **EILSEQ**會儲存在**errno**而轉換狀態*狀態*未指定。|

## <a name="remarks"></a>備註

**Mbrtoc16**函式會讀取最多*max_bytes*位元組從*來源*尋找第一個完整的有效多位元組字元，然後將對等的 utf-16在字元*目的地*。 來源位元組會根據目前執行緒的多位元組地區設定解譯。 如果多位元組字元需要多個 utf-16 輸出字元，例如 surrogate 字組，然後在*狀態*值設為存放區中的下一個 utf-16 字元*目的地*在下一個呼叫**mbrtoc16**。 **Mbrtoc32**函式相同，但輸出儲存為 utf-32 字元。

如果*來源*是的 null，傳回這些函式使用的引數進行呼叫的對等項目**NULL**如*目的地*， **""** 的*來源*，，1 表示*max_bytes*。 傳遞的值*目的地*和*max_bytes*都會被忽略。

如果*來源*是不是 null，函式會從字串的開頭，然後檢查到*max_bytes*來判斷完成下一個多位元組字元中，所需的位元組數目的位元組包括任何移位序列。 如果檢查的位元組包含有效且完整的多位元組字元，函式會將字元轉換成相等的 16 位元或 32 位元寬字元或字元。 如果*目的地*不是 null，在目的地中字元的第一個 （且可能是唯一） 結果的函式存放區。 如果需要其他輸出字元，則設定值*狀態*，以便後續呼叫函式輸出其他字元，並傳回值-3。 如果沒有更多輸出字元是必要的然後*狀態*設為初始移位狀態。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**mbrtoc16**， **mbrtoc32**|\<uchar.h>|\<cuchar>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
