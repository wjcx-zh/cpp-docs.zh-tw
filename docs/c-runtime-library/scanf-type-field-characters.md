---
title: scanf 類型欄位字元 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50db1a8370a43b8b0c43c7c228c7b3acf9dd2c8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082870"
---
# <a name="scanf-type-field-characters"></a>scanf 類型欄位字元

下列資訊適用於任何 `scanf` 系列的函式，包含安全版本，例如 `scanf_s`。

`type` 字元是唯一必要的格式欄位；它會在任何選擇性的格式欄位之後出現。 `type` 字元會決定相關聯的引數是否會解譯為字元、字串或數字。

### <a name="type-characters-for-scanf-functions"></a>scanf 函式的類型字元

|字元|預期輸入類型|引數類型|安全版本中的大小引數為何？|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|字元。 搭配 `scanf` 函式使用時，會指定單一位元組字元；搭配 `wscanf` 函式使用時，會指定全形字元。 指定 `c` 時，會讀取通常會跳過的空白字元。 若要讀取下一個非空白單一位元組字元，請使用 `%1s`；若要讀取下一個非空白寬字元，請使用 `%1ws`。|搭配 `char` 函式使用時會指向 `scanf` ，搭配 `wchar_t` 函式使用時會指向 `wscanf` 。|必要。 大小不包含 null 結束字元的空間。|
|`C`|相反大小字元。 搭配 `scanf` 函式使用時，會指定全形字元；搭配 `wscanf` 函式使用時，會指定單一位元組字元。 指定 `C` 時，會讀取通常會跳過的空白字元。 若要讀取下一個非空白單一位元組字元，請使用 `%1s`；若要讀取下一個非空白寬字元，請使用 `%1ws`。|搭配 `wchar_t` 函式使用時會指向 `scanf` ，搭配 `char` 函式使用時會指向 `wscanf` 。|必要。 大小引數不包含 null 結束字元的空間。|
|`d`|十進位整數。|指向 `int`。|否。|
|`i`|整數。 若輸入的字串開頭為「0x」或「0X」則屬於十六進位，若字串開頭為「0」則屬於八進位，否則為十進位。|指向 `int`。|否。|
|`o`|八進位整數。|指向 `int`。|否。|
|`p`|十六進位數字中的指標位址。 已讀取數字的最大數目取決於指標大小 (32 或 64 位元)，而這取決於電腦架構。 "0x" 或 "0X" 視為前置詞。|指向 `void*`。|否。|
|`u`|不帶正負號的十進位整數。|指向 `unsigned int`。|否。|
|`x`|十六進位整數。|指向 `int`。|否。|
|`e`、 `E`、 `f`、 `F`、 `g`、 `G`|浮點值包含選用正負號 (+ 或 -)、一或多個一系列包含小數點的十進位數字，以及後面接著選擇性帶正負號的整數值之選擇性指數 (「e」或「E」)。|指向 `float`。|否。|
|`a`、 `A`|浮點數值包含一系列一或多個十六進位數字，該類數字包含選擇性小數點，以及後面接著十進位值的指數 ("p" 或 "P")。|指向 `float`。|否。|
|`n`|沒有從資料流或緩衝區輸入讀取。|指向用來成功儲存字元數的 `int`，它會從資料流或緩衝讀取字元數，直到目前呼叫 `scanf` 函式或 `wscanf` 函式為止。|否。|
|`s`|字串，最多至第一個空白字元 (空格、定位字元或新行字元)。 若要讀取未以空白字元分隔的字串，請使用一組方括弧 (`[ ]`)，如 [scanf Width Specification](../c-runtime-library/scanf-width-specification.md)。|搭配 `scanf` 函式使用時，表示單一位元組字元；搭配 `wscanf` 函式使用時，表示全形字元陣列。 在任一情況下，字元陣列必須有足夠大的空間，以便納入輸入欄位以及自動加上之結束的 null 字元。|必要。 大小包含 null 結束字元的空間。|
|`S`|相反大小字串，最多至第一個空白字元 (空格、定位字元或新行字元)。 若要讀取未以空白字元分隔的字串，請使用一組方括弧 (`[ ]`)，如 [scanf 寬度規格](../c-runtime-library/scanf-width-specification.md)中所述。|搭配 `scanf` 函式使用時，表示寬字元陣列；搭配 `wscanf` 函式使用時，表示單一位元組字元陣列。 在任一情況下，字元陣列必須有足夠大的空間，以便納入輸入欄位以及自動加上之結束的 null 字元。|必要。 大小包含 null 結束字元的空間。|


必要時，大小引數應該緊接所套用的引數在參數清單中進行傳遞。 例如，下列程式碼：

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

會將最大長度 10 的字串讀取至 `string1`，並將最大長度 8 的字串讀取至 `string2`。 緩衝區大小應該至少比寬度規格多出一個空間，因為空間必須保留給 null 結束字元。

格式字串可以處理單一位元組或寬字元輸入，無論使用單一位元組字元或寬字元版本的函式。 因此，若要使用 `scanf` 函式和 `wscanf` 函式來讀取單一位元組或寬字元，請使用下列的格式指定名稱。

|若要將字元讀取為|請使用此函式|使用這些格式指定名稱|
|--------------------------|-----------------------|----------------------------------|
|單一位元組|`scanf` 函式|`c`、 `hc`或 `hC`|
|單一位元組|`wscanf` 函式|`C`、 `hc`或 `hC`|
|全形|`wscanf` 函式|`c`、 `lc`或 `lC`|
|全形|`scanf` 函式|`C`、 `lc`或 `lC`|

若要使用與 `scanf` 函式和 `wscanf` 函式掃描字串，請使用上方表格搭配格式型別指定名稱 `s` 和 `S` ，而非 `c` 和 `C`。

## <a name="see-also"></a>請參閱

[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)