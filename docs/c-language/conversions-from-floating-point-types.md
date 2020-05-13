---
title: 從浮點數類型的轉換
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998710"
---
# <a name="conversions-from-floating-point-types"></a>從浮點數類型的轉換

轉換成另一個浮點類型的浮點值，如果原始值完全在結果類型中，則不會變更值。 如果原始值是數值，但無法完全表示，則結果會是下一個較大或下一個較低的可顯示值。 如需浮點類型的範圍，請參閱[浮點常數的限制](../c-language/limits-on-floating-point-constants.md)。

轉換成整數類資料類型的浮點值，會先捨棄任何小數值來截斷。 如果在結果型別中可顯示這個截斷的值，則結果必須是該值。 當無法顯示時，會產生未定義的結果值。

**Microsoft 特定的**

Microsoft 編譯器會針對**float**值使用 IEEE-754 binary32 標記法，並將**long double**和**double**的 binary64 標記法。 因為**long double**和**double**使用相同的標記法，所以它們具有相同的範圍和精確度。

當編譯器將**double**或**long double**浮點數轉換成**float**時，它會根據浮點環境控制項（預設為「四捨五入到最接近），甚至會系結」）來舍入結果。 如果數值太高或太低而無法表示為數值**浮點**值，則轉換結果會根據原始值的正負號而是正數或負無限大，而如果啟用，則會引發溢位例外狀況。

轉換成整數類型時，轉換成小於**long**的類型的結果是將值轉換成**long**，然後轉換成結果類型的結果。

若要轉換成整數類資料類型至少為**long**，在結果類型中，值過高或太低的轉換可能會傳回下列任何值：

- 結果可能是*sentinel 值*，這是最遠為零的可顯示值。 對於帶正負號的類型，這是最小的可顯示值（0x800 .。。0）。 對於不帶正負號的類型，這是最高的可顯示值（0xFF .。。F）。

- 結果可能會*飽和*，其中的值太高而無法表示會轉換成最大的可顯示值，而值太低而無法表示會轉換成最小的可顯示值。 這兩個值的其中一個也會當做 sentinel 值使用。

- 若要轉換成不**帶正負**號的長整數或不**帶正負號的 long long**，轉換超出範圍值的結果可能是最高或最低可顯示值以外的值。 結果是 sentinel 或飽和值，而不是取決於編譯器選項和目標架構。 未來的編譯器版本可能會改為傳回飽和或 sentinel 值。

**結束 Microsoft 專有**

下表摘要說明從浮點類型進行轉換。

## <a name="table-of-conversions-from-floating-point-types"></a>從浮點類型轉換的資料表

|從|至|方法|
|----------|--------|------------|
|**float**|**char**|轉換成 **long**；將 **long** 轉換成 **char**|
|**float**|**short**|轉換為 **long**，將 **long** 轉換為 **short**|
|**float**|**int**|於小數點截斷。 如果結果太大，而無法以**int**表示，則結果會是未定義的。|
|**float**|**前提**|於小數點截斷。 如果結果太大而無法以 **long** 表示，則結果會是未定義。|
|**float**|**long long**|於小數點截斷。 如果結果太大而無法以**long**表示，則結果會是未定義的。|
|**float**|**unsigned char**|轉換成**long**;將**long**轉換成不**帶正負**號的字元|
|**float**|**unsigned short**|轉換為 **long**，將 **long** 轉換為 **unsigned short**|
|**float**|**unsigned**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負**號，則結果為未定義。|
|**float**|**unsigned long**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負號的長整數**，則會產生未定義的結果。|
|**float**|**unsigned long long**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負號的長長**整數，則會產生未定義的結果。|
|**float**|**double**|表示為**雙精度浮點數**。|
|**float**|**long double**|表示為**長雙精度浮點數**。|
|**double**|**char**|轉換成 **float**；將 **float** 轉換成 **char**|
|**double**|**short**|轉換為 **float**，將 **float** 轉換為 **short**|
|**double**|**int**|於小數點截斷。 如果結果太大，而無法以**int**表示，則結果會是未定義的。|
|**double**|**前提**|於小數點截斷。 如果結果太大而無法以 **long** 表示，則結果會是未定義。|
|**double**|**unsigned char**|轉換成**long**;將**long**轉換成不**帶正負**號的字元|
|**double**|**unsigned short**|轉換為 **long**，將 **long** 轉換為 **unsigned short**|
|**double**|**unsigned**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負**號，則結果為未定義。|
|**double**|**unsigned long**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負號的長整數**，則會產生未定義的結果。|
|**double**|**unsigned long long**|於小數點截斷。 如果結果太大，而無法表示為不**帶正負號的長長**整數，則會產生未定義的結果。|
|**double**|**float**|表示為 **float**。 如果**double**值無法完全表示為**float**，則會遺失有效位數。 如果值太大而無法以 **float** 表示，則結果會是未定義。|
|**double**|**long double**|**long double** 值會被視為 **double**。|

**Long double**的轉換會遵循與**double**轉換相同的方法。

## <a name="see-also"></a>請參閱

[指派轉換](../c-language/assignment-conversions.md)
