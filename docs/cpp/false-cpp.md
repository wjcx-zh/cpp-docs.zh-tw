---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: f363e309b91e44472447d040aa36752750afec6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188931"
---
# <a name="false-c"></a>false (C++)

關鍵字是[bool](../cpp/bool-cpp.md)類型變數或條件運算式（條件運算式現在是**true**布林運算式）的兩個值之一。 例如，如果 `i` 是**bool**類型的變數，則 `i = false;` 語句會將**false**指派給 `i`。

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
