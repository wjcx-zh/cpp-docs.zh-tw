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
ms.openlocfilehash: 77c61101e9540a0d9469e7176eb15992a73b4b09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158276"
---
# <a name="simple-assignment-c"></a>簡單指派 (C)

簡單指派運算子會將其右運算元指派給其左運算元。 右運算元的值會轉換為指派運算式的類型，並且取代儲存在左運算元指定之物件中的值。 以指派的轉換規則為準 (請參閱[指派轉換](../c-language/assignment-conversions.md))。

```
double x;
int y;

x = y;
```

在此範例中，`y` 的值會轉換成類型 **double** 並指派給 `x`。

## <a name="see-also"></a>請參閱

[C 指派運算子](../c-language/c-assignment-operators.md)
