---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 5fc27c7f1dfde7d1f686f0a752652773ade9cc0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183722"
---
# <a name="false-c"></a>false (C++)

關鍵字是類型的變數的兩個值的其中一個[bool](../cpp/bool-cpp.md)或 條件運算式 (條件式運算式現在是 **，則為 true**布林運算式)。 比方說，如果`i`類型的變數**bool**，則`i = false;`陳述式指派**false**至`i`。

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