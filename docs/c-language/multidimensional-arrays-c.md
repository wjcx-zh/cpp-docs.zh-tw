---
title: 多維陣列 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: f94cdff03763f689edbdedffad4ac56abec5ee53
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218828"
---
# <a name="multidimensional-arrays-c"></a>多維陣列 (C)

註標運算式也可以擁有多個註標，如下所示：

```
expression1 [ expression2 ] [ expression3 ] ...
```

註標運算式的關聯是由左至右。 最左邊的注標*運算式（運算式* **1 [** *運算式*2 **]**）會先進行評估。 *expression1* 和 *expression2* 相加所產生的位址會形成指標運算式，然後 *expression3* 會加入這個指標運算式形成新的指標運算式，依此類推，直到加入最後一個註標運算式為止。 <strong>\*</strong>除非最後一個指標值會定址陣列類型（請參閱下面的範例），否則間接運算子（）會在評估最後一個下標運算式之後套用。

具有多個註標的運算式會參考「多維陣列」的元素。 所謂的多維陣列是指其中所包含的元素也是一種陣列。 例如，三維陣列的第一個元素是具有兩個維度的陣列。

## <a name="examples"></a>範例

在下列範例中，名為的陣列 `prop` 是以三個元素宣告，其中每個專案都是4到6個 **`int`** 值陣列。

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

`prop` 陣列參考的外觀如下：

```
i = prop[0][0][1];
```

上述範例顯示如何參考的第二個個別 **`int`** 元素 `prop` 。 陣列會依資料列儲存，因此最後一個註標變化的速度更快，而 `prop[0][0][2]` 運算式會參考陣列的下一個 (第三個) 元素，依此類推。

```
i = prop[2][1][3];
```

這個陳述式對於 `prop` 的個別元素來說是更為複雜的參考。 運算式評估如下：

1. 第一個注標 `2` 會乘以4到6陣列的大小， **`int`** 並加入至指標值 `prop` 。 結果會指向 `prop` 的第三個 4x6 陣列。

1. 第二個注標 `1` 會乘以6個元素陣列的大小， **`int`** 並加入至所代表的位址 `prop[2]` 。

1. 6個元素陣列的每個元素都是 **`int`** 值，因此最後一個注標會 `3` 乘以的大小， **`int`** 再將其加入 `prop[2][1]` 。 產生的指標會定址 6 個元素陣列的第四個元素。

1. 間接運算子會套用至指標值。 結果是 **`int`** 該位址的元素。

接下來的兩個範例將示範未套用間接運算子的案例。

```
ip = prop[2][1];

ipp = prop[2];
```

在第一個陳述式中，運算式 `prop[2][1]` 為三維陣列 `prop` 的有效參考，它會參考 6 個元素的陣列 (上面所宣告)。 由於指標值會定址陣列，因此不會套用間接運算子。

同樣地，第二個陳述式 `prop[2]` 中 `ipp = prop[2];` 運算式的結果是定址二維陣列的指標值。

## <a name="see-also"></a>另請參閱

[注標運算子：](../cpp/subscript-operator.md)
