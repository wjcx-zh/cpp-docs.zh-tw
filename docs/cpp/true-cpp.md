---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: 5cfc99f446499201a0f54c8e5b1dcc2d7152445c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404698"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>語法

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>備註

這個關鍵字是類型的變數的兩個值的其中一個[bool](../cpp/bool-cpp.md)或條件運算式 （條件運算式是現在，則為 true 的布林運算式）。 如果`i`屬於型別**bool**，則陳述式`i = true;`指派 **，則為 true**至`i`。

## <a name="example"></a>範例

```cpp
// bool_true.cpp
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