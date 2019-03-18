---
title: scanf 寬度規格
ms.date: 11/04/2016
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 1431002a7e7d0054ac20c05c76b05cabc96177c5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743257"
---
# <a name="scanf-width-specification"></a>scanf 寬度規格

下列資訊適用於任何 `scanf` 函式系列中的格式字串解譯，包含安全版本，例如 `scanf_s`。 這些函式通常會假設輸入資料流分割成一連串的語彙基元。 語彙基元會以空白字元 (空格、定位字元或新行字元) 分隔，若為數字型別，根據第一個字元無法轉換成數字文字的指示，則以數字資料類型的自然結束分隔。 不過，寬度規格可能會用來造成輸入剖析在語彙基元自然結束之前停止。

「寬度」規格包含 `%` 與類型欄位指定名稱之間的字元，其中可能包含稱為「寬度」欄位的正整數，和一或多個表示欄位大小的字元，這可能也會視為欄位類型的修飾詞，例如整數類型為 **short** 或 **long** 的指示。 此類字元稱為大小前置詞。

## <a name="the-width-field"></a>寬度欄位

「寬度」欄位是十進位正整數，用來控制針對該欄位可讀取的最大字元數。 在對應的 `argument` 中無法轉換和儲存超過「寬度」的字元。 在達到「寬度」之前，若發生空白字元 (空格、定位字元或新行字元) 或無法根據指定格式轉換的字元，則可能會讀取少於「寬度」的字元。

寬度規格與這些安全版本函式所需的緩衝區大小引數截然不同 (例如 `scanf_s` 和 `wscanf_s` 等)。 在下列範例中，寬度規格為 20，表示會從輸入資料流讀取最多 20 個字元。 緩衝區長度為 21，其中包含可能的 20 個字元再加上 null 結束字元的空間：

```C
char str[21];
scanf_s("%20s", str, 21);
```

如果未使用「寬度」欄位，則 `scanf_s` 會嘗試將整個語彙基元讀取至字串。 如果指定的大小不足以容納整個語彙基元，則不會寫入任何內容至目的地字串。 如果指定「寬度」欄位，然後語彙基元中的第一個「寬度」字元會與 null 結束字元一併寫入至目的地字串。

## <a name="the-size-prefix"></a>大小前置詞

選擇性的前置詞 **h**、**l**、**ll**、**I64** 和 **L** 會指出 `argument` 的大小 (取決於它們修改的類型字元，可能是 long 或 short、單一位元組字元或寬字元)。 這些格式規格字元會搭配 `scanf` 或 `wscanf` 函式中的型別字元使用，以便指定引數的解譯，如下方表格所示。 類型前置詞 **I64** 是 Microsoft 延伸模組且與 ANSI 不相容。 類型字元和其意義如同 [scanf 類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)中的「scanf 函式的類型字元」資料表所述。

> [!NOTE]
> 搭配類型 `char` 的資料使用時，**h**、**l** 和 **L** 前置詞是 Microsoft 延伸模組。

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>scanf 和 wscanf 格式型別指定名稱的大小前置詞

|若要指定|使用前置詞|類型規範為|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**、**E**、**f**、**g** 或 **G**|
|**long double** (與 double 相同)|**L**|**e**、**E**、**f**、**g** 或 **G**|
|**long int**|**l**|**d**、**i**、**o**、**x** 或 **X**|
|**long unsigned int**|**l**|**u**|
|**long long**|**ll**|**d**、**i**、**o**、**x** 或 **X**|
|`short int`|**h**|**d**、**i**、**o**、**x** 或 **X**|
|**short unsigned int**|**h**|**u**|
|__**int64**|**I64**|**d**、**i**、**o**、**u**、**x** 或 **X**|
|使用 `scanf` 的單一位元組字元|**h**|**c** 或 **C**|
|使用 `wscanf` 的單一位元組字元|**h**|**c** 或 **C**|
|使用 `scanf` 的寬字元|**l**|**c** 或 **C**|
|使用 `wscanf` 的寬字元|**l**|**c** 或 **C**|
|使用 `scanf` 的單一位元組字元字串|**h**|**s** 或 **S**|
|使用 `wscanf` 的單一位元組字元字串|**h**|**s** 或 **S**|
|使用 `scanf` 的寬字元字串|**l**|**s** 或 **S**|
|使用 `wscanf` 的寬字元字串|**l**|**s** 或 **S**|

下列範例會使用 **h** 和 **l** 搭配 `scanf_s` 函式和 `wscanf_s` 函式：

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

如果使用 `scanf` 系列中的不安全函式，則會省略指出先前引數緩衝區長度的大小參數。

## <a name="reading-undelimited-strings"></a>讀取未分隔字串

若要讀取未以空白字元分隔的字串，則一組以方括弧 (**[ ]**) 括住的字元可以使用 **s** (字串) 類型字元來替代。 方括號中的的字元集稱為控制項字串。 對應的輸入欄位會讀取至控制項字串中並未出現的第一個字元。 若字元集中的第一個字元是插入號 (**^**)，其效果會相反：輸入欄位會讀取到第一個確實出現在字元集剩餘部分中的字元。

請注意，**%[a-z]** 和 **%[z-a]** 解譯為相當於 **%[abcde...z]**。 這是一般 `scanf` 函式延伸模組，但請注意 ANSI 標準不需要它。

## <a name="reading-unterminated-strings"></a>讀取未結束的字串。

若要儲存字串而不儲存結束的 null 字元 ('\0')，請使用規格 **%**<em>n</em>**c**，其中 *n* 是十進位整數。 在此情況下，**c** 類型字元表示引數是字元陣列的指標。 下一個 *n* 字元會從輸入資料流讀取至指定的位置，且不附加任何 null 字元 ('\0')。 如果未指定 *n*，則其預設值為 1。

## <a name="when-scanf-stops-reading-a-field"></a>當 scanf 停止讀取欄位時

`scanf` 函式會逐個字元掃描每個輸入欄位。 它可能會在基於各種原因停止到達空白字元之前讀取特定的輸入欄位：

- 已達到指定的寬度。

- 下一個字元無法轉換為指定字元。

- 下一個字元與控制項字串中應該符合的字元相衝突。

- 下一個字元無法顯示在指定的字元集。

無論基於任何原因，當 `scanf` 函式停止讀取輸入欄位時，下一個輸入欄位會視為以未讀取的第一個字元開始。 如果有衝突字元，則會視為未讀取，且是下一個輸入欄位的第一個字元，或輸入資料流上後續讀取作業的第一個字元。

## <a name="see-also"></a>另請參閱

[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[格式規格欄位：scanf 和 wscanf 函式](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf 類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)<br/>
