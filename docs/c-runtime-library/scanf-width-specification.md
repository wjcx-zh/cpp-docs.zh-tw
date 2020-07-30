---
title: scanf 寬度規格
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 781e292140babd61fbcde77cefcb917736b17cc3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188735"
---
# <a name="scanf-width-specification"></a>`scanf`寬度規格

下列資訊適用於任何 `scanf` 函式系列中的格式字串解譯，包含安全版本，例如 `scanf_s`。 這些函式通常會假設輸入資料流分割成一連串的語彙基元。 標記是以空白字元（空格、定位字元或分行符號）或數數值型別的自然結尾來分隔，如第一個字元無法轉換成數位文字所指示。 不過，寬度規格可能會用來造成輸入剖析在語彙基元自然結束之前停止。

*寬度*規格包含和類型欄位規範之間的字元 `%` ，其中可能包含稱為 [*寬度*] 欄位的正整數，以及一或多個表示欄位大小的字元，這也可能會被視為欄位類型的修飾詞，例如整數類型為或的指示 **`short`** **`long`** 。 此類字元稱為大小前置詞。

## <a name="the-width-field"></a>寬度欄位

[*寬度*] 欄位是一個正十進位整數，可控制要針對該欄位讀取的最大字元數。 不能有超過*寬度*的字元會轉換並儲存在對應的中 `argument` 。 如果空白字元或無法根據指定格式轉換的字元，在到達*寬度*之前，可能會讀取少於*寬度*的字元。

寬度規格是獨立的，而且與這些函式的安全版本所需的緩衝區大小引數不同（例如、、等等 `scanf_s` `wscanf_s` ）。 在下列範例中，寬度規格為 20，表示會從輸入資料流讀取最多 20 個字元。 緩衝區長度為 21，其中包含可能的 20 個字元再加上 null 結束字元的空間：

```C
char str[21];
scanf_s("%20s", str, 21);
```

如果未使用 [*寬度*] 欄位， `scanf_s` 會嘗試將整個標記讀取至字串。 如果指定的大小不足以容納整個 token，則不會將任何內容寫入目的地字串。 如果指定 [*寬度*] 欄位，則權杖中的第一個*寬度*字元會與 null 結束字元一併寫入至目的地字串。

## <a name="the-size-prefix"></a>大小前置詞

選擇性的前置詞**h**、 **hh**、 **l**、 **ll**、 **I64**和**l**會指出的大小 `argument` （視其修改的類型字元而定的長或短、單一位元組字元或寬字元）。 這些格式規格字元會搭配 `scanf` 或 `wscanf` 函式中的型別字元使用，以便指定引數的解譯，如下方表格所示。 類型前置詞**I64**是 Microsoft 擴充功能，與標準 C 不相容。類型字元和其意義在[ `scanf` 類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)的 "type 字元 for scanf 函數" 資料表中有所描述。

> [!NOTE]
> 當搭配類型的資料使用時， **h**、 **l**和**l**前置詞是 Microsoft 擴充功能 **`char`** 。

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>`scanf`和 `wscanf` 格式類型規範的大小前置詞

|若要指定|使用前置詞|類型規範為|
|----------------|----------------|-------------------------|
|**`double`**|**l**|**e**、**E**、**f**、**g** 或 **G**|
|**`long double`**（與相同 **`double`** ）|**L**|**e**、**E**、**f**、**g** 或 **G**|
|**`long int`**|**l**|**d**、**i**、**o**、**x** 或 **X**|
|**`long unsigned int`**|**l**|**u**|
|**`long long`**|**馬上**|**d**、**i**、**o**、**x** 或 **X**|
|**`short int`**|**h**|**d**、**i**、**o**、**x** 或 **X**|
|**`short unsigned int`**|**h**|**u**|
|**`char`**|**hh**|**d**、**i**、**o**、**x** 或 **X**|
|**`unsigned char`**|**hh**|**u**|
|**`int64`**|**I64**|**d**、**i**、**o**、**u**、**x** 或 **X**|
|使用 `scanf` 的單一位元組字元|**h**|**c**或**c**|
|使用 `wscanf` 的單一位元組字元|**h**|**c**或**c**|
|使用 `scanf` 的寬字元|**l**|**c**或**c**|
|使用 `wscanf` 的寬字元|**l**|**c** 或 **C**|
|使用的單一位元組字元字串`scanf`|**h**|**s** 或 **S**|
|使用的單一位元組字元字串`wscanf`|**h**|**s** 或 **S**|
|具有的寬字元字串`scanf`|**l**|**s** 或 **S**|
|具有的寬字元字串`wscanf`|**l**|**s** 或 **S**|

下列範例會使用 **h** 和 **l** 搭配 `scanf_s` 函式和 `wscanf_s` 函式：

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

如果使用 `scanf` 系列中的不安全函式，則會省略指出先前引數緩衝區長度的大小參數。

## <a name="reading-undelimited-strings"></a>讀取未分隔字串

若要讀取未以空白字元分隔的字串，以方括弧（）括住的一組字元 **`[ ]`** 可以替代**s** （字串）類型字元。 方括弧中的一組字元稱為「*控制字元串*」。 對應的輸入欄位會讀取至不會出現在控制項字串中的第一個字元。 如果集合中的第一個字元是插入號（ **`^`** ），則會反轉效果：輸入欄位會讀取到出現在字元集其餘部分的第一個字元。

**% [A-z]** 和 **% [z-a]** 都會解讀為等同于 **% [abcde .。。z]**。 這是常見的 `scanf` 功能延伸，但不是標準 C 的必要項。

## <a name="reading-unterminated-strings"></a>讀取未結束的字串

若要儲存字串而不儲存終止的 null 字元（' \ 0 '），請使用規格 `%Nc` ，其中*N*是十進位整數。 在此情況下，**c** 類型字元表示引數是字元陣列的指標。 下一個*N*字元會從輸入資料流程讀取至指定的位置，而且不會附加 null 字元（' \ 0 '）。 如果未指定*N* ，則其預設值為1。

## <a name="when-scanf-stops-reading-a-field"></a>當 `scanf` 停止讀取欄位時

`scanf` 函式會逐個字元掃描每個輸入欄位。 它可能會在因下列幾個原因之一而到達空白字元之前，停止讀取特定輸入欄位：

- 已達到指定的寬度。

- 下一個字元無法依照指定的方式轉換。

- 下一個字元與控制項字串中應符合的字元衝突。

- 下一個字元無法顯示在指定的字元集。

無論基於任何原因，當 `scanf` 函式停止讀取輸入欄位時，下一個輸入欄位會視為以未讀取的第一個字元開始。 衝突的字元（如果有的話）會視為未讀取。 這是下一個輸入欄位的第一個字元，或輸入資料流程後續讀取作業中的第一個字元。

## <a name="see-also"></a>另請參閱

[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[格式規格欄位： `scanf` 和函式 `wscanf`](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[`scanf`類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)<br/>
