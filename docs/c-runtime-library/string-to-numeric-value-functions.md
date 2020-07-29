---
title: 字串轉換為數值函式
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b4936e09de5ee26356b71b66154071a93e252b6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213459"
---
# <a name="string-to-numeric-value-functions"></a>字串轉換為數值函式

- [strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>備註

**strtod** 系列中的每個函式都會將以 null 終止的字串轉換為數值。 下表列出可用的函式。

|函式|說明|
|--------------|-----------------|
|`strtod`|將字串轉換為雙精確度浮點值|
|`strtol`|將字串轉換為 long 整數|
|`strtoul`|將字串轉換為不帶正負號的 long 整數|
|`_strtoi64`|將字串轉換為64位 **`__int64`** 整數|
|`_strtoui64`|將字串轉換為不帶正負號的64位 **`__int64`** 整數|

`wcstod`、`wcstol`、`wcstoul` 和 `_wcstoi64` 分別是寬字元版本的 `strtod`、`strtol`、`strtoul` 和 `_strtoi64`。 所有這些寬字元函式的字串引數都是寬字元字串；否則，每個函式與其單一位元組字元對應項目的行為完全相同。

`strtod` 函式採用兩個引數︰第一個是輸入字串，而第二個字元是結束轉換程序之字元的指標。 `strtol`、`strtoul`、**_strtoi64** 和 **_strtoui64** 採用第三個引數作為用於轉換程序的數字基底。

輸入字串是一串字元，可解譯為所指定類型的數值。 每個函式都會在它無法辨識為數字一部分的第一個字元處停止讀取字串。 這可能是終止的 Null 字元。 針對 `strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64`，此終止字元也可以是第一個大於或等於使用者所提供數字基底的數值字元。

如果在呼叫期間未將使用者所提供的轉換結束字元指標設定為 **NULL**，則會改為將停止掃描之字元的指標儲存在那裡。 如果無法執行任何轉換 (找不到任何有效的數字或指定無效的基底)，則字串指標的值會儲存在該位址。

`strtod` 需要格式如下的字串︰

[*空格*][*sign*][`digits`] [**.**`digits`][{**d** &#124; **d** &#124; **e** &#124; **e**} [*sign*] `digits` ]

*whitespace* 包含可忽略的空白或定位字元；*sign* 是加號 (**+**) 或減號 (**-**)；而且 `digits` 是一或多個十進位數字。 如果基底字元前沒有任何數字，則在基底字元後至少必須要有一個數字。 小數位數的後面會接著包含簡介字母 (**d**、**D**、**e** 或 **E**) 的指數以及選擇性的帶正負號整數。 如果沒有出現指數部分也沒有出現基底字元，基底字元假設會跟在字串的最後一位數的後面。 不符合此格式的第一個字元會停止掃描。

`strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64` 函式預期會有下列形式的字串︰

[*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [ `digits` ]

如果 base 引數介於 2 到 36 之間，則會作為數字的基底。 如果為 0，則會使用轉換結束指標所參考的起始字元來判斷基底。 如果第一個字元為 0，而第二個字元不是 'x' 或 X'，則字串會解譯為八進位整數；否則會解譯為十進位數字。 如果第一個字元為 '0'，而第二個字元是 'x' 或 X'，則字串會解譯為十六進位整數。 如果第一個字元為 '1' 到 '9'，則字串會解譯為十進位整數。 字母 'a' 到 'z' (或 'A' 到 'Z') 被指派值 10 到 35，只允許指派值小於 *base* 的字母。 `strtoul`和 `_strtoui64` 允許加號（ **+** ）或減號（ **-** ）正負號前置詞，前置減號表示傳回值為否定。

輸出值會受到地區設定的 `LC_NUMERIC` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。

這些函式所傳回的值造成溢位或反向溢位時，或不可能轉換時，會如所示傳回特殊大小寫值︰

|函式|條件|傳回的值|
|--------------|---------------|--------------------|
|`strtod`|溢位|+/- `HUGE_VAL`|
|`strtod`|反向溢位或未轉換|0|
|`strtol`|+ 溢位|**LONG_MAX**|
|`strtol`|- 溢位|**LONG_MIN**|
|`strtol`|反向溢位或未轉換|0|
|`_strtoi64`|+ 溢位|**_I64_MAX**|
|`_strtoi64`|- 溢位|**_I64_MIN**|
|`_strtoi64`|未轉換|0|
|`_strtoui64`|溢位|**_UI64_MAX**|
|`_strtoui64`|未轉換|0|

**_I64_MAX**、_**I64_MIN** 和 **_UI64_MAX** 定義於 LIMITS.H 內。

`wcstod`、`wcstol`、`wcstoul`、`_wcstoi64` 和 `_wcstoui64` 分別是寬字元版本的 `strtod`、`strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64`；所有這些寬字元函式之轉換結束引數的指標是寬字元字串。 否則，所有這些寬字元函式與其單一位元組字元對應項目的行為完全相同。

## <a name="see-also"></a>另請參閱

[資料轉換](../c-runtime-library/data-conversion.md)<br/>
[地區設定](../c-runtime-library/locale.md)<br/>
[多位元組字元序列的轉譯](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[浮點支援](../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
