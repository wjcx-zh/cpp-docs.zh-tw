---
title: 從浮點數類型的轉換
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: 72d0f95a6e48dcf0a5e8fea3757e85f9a03bf7e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227890"
---
# <a name="conversions-from-floating-point-types"></a>從浮點數類型的轉換

轉換成另一個浮點類型的浮點值，如果原始值完全在結果類型中，則不會變更值。 如果原始值是數值，但無法完全表示，則結果會是下一個較大或下一個較低的可顯示值。 如需浮點類型的範圍，請參閱[浮點常數的限制](../c-language/limits-on-floating-point-constants.md)。

轉換成整數類資料類型的浮點值，會先捨棄任何小數值來截斷。 如果在結果型別中可顯示這個截斷的值，則結果必須是該值。 當無法顯示時，會產生未定義的結果值。

**Microsoft 特定的**

Microsoft 編譯器會針對值使用 IEEE-754 binary32 標記法 **`float`** ，並針對和 binary64 標記法 **`long double`** **`double`** 。 由於 **`long double`** 和 **`double`** 使用相同的標記法，因此它們具有相同的範圍和有效位數。

當編譯器將 **`double`** 或 **`long double`** 浮點數轉換成時 **`float`** ，它會根據浮點環境控制項來四捨五入結果，預設為「四捨五入到最接近的位置」，甚至是。 如果數值太高或太低而無法表示為數值 **`float`** ，則轉換結果會根據原始值的正負號而是正數或負無限大，而如果啟用，則會引發溢位例外狀況。

轉換成整數類型時，轉換成小於的類型的結果 **`long`** 是將值轉換成 **`long`** ，然後轉換成結果類型的結果。

若要轉換成整數類資料類型，且其大小至少要等於 **`long`** ，在結果類型中，值過高或太低的轉換可能會傳回下列任何值：

- 結果可能是*sentinel 值*，這是最遠為零的可顯示值。 對於帶正負號的類型，這是最小的可顯示值（0x800 .。。0）。 對於不帶正負號的類型，這是最高的可顯示值（0xFF .。。F）。

- 結果可能會*飽和*，其中的值太高而無法表示會轉換成最大的可顯示值，而值太低而無法表示會轉換成最小的可顯示值。 這兩個值的其中一個也會當做 sentinel 值使用。

- 若要轉換為 **`unsigned long`** 或 **`unsigned long long`** ，轉換超出範圍值的結果可能是最高或最低可顯示值以外的值。 結果是 sentinel 或飽和值，而不是取決於編譯器選項和目標架構。 未來的編譯器版本可能會改為傳回飽和或 sentinel 值。

**結束 Microsoft 專有**

下表摘要說明從浮點類型進行轉換。

## <a name="table-of-conversions-from-floating-point-types"></a>從浮點類型轉換的資料表

|寄件者|收件者|方法|
|----------|--------|------------|
|**`float`**|**`char`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`char`**|
|**`float`**|**`short`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`short`**|
|**`float`**|**`int`**|於小數點截斷。 如果結果太大，而無法表示為 **`int`** ，則結果會是未定義的。|
|**`float`**|**`long`**|於小數點截斷。 如果結果太大，而無法表示為 **`long`** ，則結果會是未定義的。|
|**`float`**|**`long long`**|於小數點截斷。 如果結果太大，而無法表示為 **`long long`** ，則結果會是未定義的。|
|**`float`**|**`unsigned char`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`unsigned char`**|
|**`float`**|**`unsigned short`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`unsigned short`**|
|**`float`**|**`unsigned`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned`** ，則結果會是未定義的。|
|**`float`**|**`unsigned long`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned long`** ，則結果會是未定義的。|
|**`float`**|**`unsigned long long`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned long long`** ，則結果會是未定義的。|
|**`float`**|**`double`**|表示為 **`double`** 。|
|**`float`**|**`long double`**|表示為 **`long double`** 。|
|**`double`**|**`char`**|轉換成 **`float`** ; 將轉換 **`float`** 成**`char`**|
|**`double`**|**`short`**|轉換成 **`float`** ; 將轉換 **`float`** 成**`short`**|
|**`double`**|**`int`**|於小數點截斷。 如果結果太大，而無法表示為 **`int`** ，則結果會是未定義的。|
|**`double`**|**`long`**|於小數點截斷。 如果結果太大，而無法表示為 **`long`** ，則結果會是未定義的。|
|**`double`**|**`unsigned char`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`unsigned char`**|
|**`double`**|**`unsigned short`**|轉換成 **`long`** ; 將轉換 **`long`** 成**`unsigned short`**|
|**`double`**|**`unsigned`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned`** ，則結果會是未定義的。|
|**`double`**|**`unsigned long`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned long`** ，則結果會是未定義的。|
|**`double`**|**`unsigned long long`**|於小數點截斷。 如果結果太大，而無法表示為 **`unsigned long long`** ，則結果會是未定義的。|
|**`double`**|**`float`**|表示為 **`float`** 。 如果 **`double`** 值無法完全表示為 **`float`** ，則會遺失有效位數。 如果值太大而無法表示為 **`float`** ，則結果會是未定義的。|
|**`double`**|**`long double`**|此 **`long double`** 值會視為 **`double`** 。|

的轉換會 **`long double`** 遵循與從轉換相同的方法 **`double`** 。

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)
