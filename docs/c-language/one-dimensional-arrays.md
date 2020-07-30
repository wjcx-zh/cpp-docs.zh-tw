---
title: 一維陣列
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: c310d610b4e4cfc5ae5620d38337a5b8fd5243ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226349"
---
# <a name="one-dimensional-arrays"></a>一維陣列

後置運算式 (postfix expression) 後面跟著以方括號 (**[ ]**) 括住的運算式，是以註標方式來表示的陣列物件元素。 當註標運算式如下表示時，代表 *expression* 於 *postfix-expression* 之外的所在位置位址值：

```
postfix-expression [ expression ]
```

通常，*postfix-expression* 所代表的值是指標值，例如陣列識別項，而 *expression* 則是整數值。 不過，在語法上需要的是其中一個指標類型的運算式，另一個則是整數類型。 因此，整數值可以在 *postfix-expression* 位置，而指標值則可以在 *expression* 的括號中，或是在註標位置。 例如，以下這個程式碼是合法的：

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

註標運算式通常用來參考陣列元素，但是您可以將註標套用到任何指標。 無論值的順序為何，*expression* 都必須以方括號 (**[ ]**) 括住。

注標運算式的評估方式是將整數值新增至指標值，然後將間接運算子（ <strong>\*</strong> ）套用至結果。 （如需間接運算子的討論，請參閱[間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)）。實際上，針對一維陣列，下列四個運算式是相等的，假設 `a` 是指標且 `b` 為整數：

```
a[b]
*(a + b)
*(b + a)
b[a]
```

根據加法運算子的轉換規則 (請參閱[加法類運算子](../c-language/c-additive-operators.md))，會藉由將整數值乘以指標定址之類型的長度，將整數值轉換為位址位移。

例如，假設識別碼 `line` 是指值的陣列 **`int`** 。 下列程序用於評估註標運算式 `line[ i ]`：

1. 整數值 `i` 乘以定義為專案長度的位元組數目 **`int`** 。 的轉換值 `i` 表示 `i` **`int`** 位置。

1. 這個轉換後的值會加入至原始指標值（ `line` ），以產生從到位移 `i` **`int`** 個位置的位址 `line` 。

1. 將間接運算子套用至新的位址。 結果是在該位置之陣列元素 (憑直覺是 `line [ i ]`) 的值。

註標運算式 `line[0]` 代表該行第一個元素的值，因為從 `line` 代表的位址位移是 0。 同樣地，運算式 (如 `line[5]`) 會參考從程式行位移五個位置的元素，或是陣列的第六個元素。

## <a name="see-also"></a>另請參閱

[注標運算子：](../cpp/subscript-operator.md)
