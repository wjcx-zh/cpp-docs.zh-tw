---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: d6162bdde3dea0d245a0c83c1d52b06003fee16c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227487"
---
# <a name="false-c"></a>false (C++)

關鍵字是[bool](../cpp/bool-cpp.md)類型變數或條件運算式（條件運算式現在是布林運算式）的兩個值之一 **`true`** 。 例如，如果 `i` 是類型的變數 **`bool`** ，則語句會將 `i = false;` 指派 **`false`** 給 `i` 。

## <a name="example"></a>範例

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
