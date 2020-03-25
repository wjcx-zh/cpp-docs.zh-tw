---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: b497c3c9eb1b30074c9b7286c438d0077525e05b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188034"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>語法

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>備註

這個關鍵字是[bool](../cpp/bool-cpp.md)類型變數或條件運算式（條件運算式現在是 true 布林運算式）的兩個值之一。 如果 `i` 的類型為**bool**，則語句 `i = true;` 會將**true**指派給 `i`。

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
