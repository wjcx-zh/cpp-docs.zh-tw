---
title: 編譯器錯誤 C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: 5f608d0407c24bd01ed7b80dbef873dd30662661
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221246"
---
# <a name="compiler-error-c2318"></a>編譯器錯誤 C2318

沒有和 catch 處理常式關聯的 try 區塊

已 **`catch`** 定義處理常式，但前面沒有 **`try`** 區塊。

下列範例會產生 C2318：

```cpp
// C2318.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   // no try block
   catch( int ) {}   // C2318
}
```

可能的解決方式：

```cpp
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```
