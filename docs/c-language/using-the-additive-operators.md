---
title: 使用加法類運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 06d71f3ad1944976a8d415be9487cb5ea365fa26
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213680"
---
# <a name="using-the-additive-operators"></a>使用加法類運算子

下列範例 (其中說明加法和減法運算子) 使用這些宣告：

```
int i = 4, j;
float x[10];
float *px;
```

這些陳述式是相同的：

```
px = &x[4 + i];
px = &x[4] + i;
```

的值 `i` 會乘以的長度 **`float`** ，並加入至 `&x[4]` 。 產生的指標值為 `x[8]` 的位址。

```
j = &x[i] - &x[i-2];
```

在此範例中，`x` 第三個元素的位址 (由 `x[i-2]` 指定) 是減去 `x` 第五個元素的位址 (由 `x[i]` 指定) 而得。 差異會除以的長度， **`float`** 結果為整數值2。

## <a name="see-also"></a>另請參閱

[C 加法類運算子](../c-language/c-additive-operators.md)
