---
title: 簡單指派 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: 64112a54828a9a6626e78e556e8fe6dc52a3300f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229541"
---
# <a name="simple-assignment-c"></a>簡單指派 (C)

簡單指派運算子會將其右運算元指派給其左運算元。 右運算元的值會轉換為指派運算式的類型，並且取代儲存在左運算元指定之物件中的值。 以指派的轉換規則為準 (請參閱[指派轉換](../c-language/assignment-conversions.md))。

```
double x;
int y;

x = y;
```

在此範例中，的值 `y` 會轉換成類型 **`double`** 並指派給 `x` 。

## <a name="see-also"></a>另請參閱

[C 指派運算子](../c-language/c-assignment-operators.md)
