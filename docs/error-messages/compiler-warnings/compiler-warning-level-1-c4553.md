---
title: 編譯器警告（層級1） C4553
ms.date: 11/04/2016
f1_keywords:
- C4553
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
ms.openlocfilehash: a2d5e52e565878011b2439792c721eeb57cdd20a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966332"
---
# <a name="compiler-warning-level-1-c4553"></a>編譯器警告（層級1） C4553

' operator '：運算子沒有作用;您想要 ' operator ' 嗎？

如果運算式語句的運算子沒有任何副作用做為運算式的頂端，可能就會發生錯誤。

下列範例會產生 C4553：

```cpp
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```