---
title: 編譯器錯誤 C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: 0af0b0e0fbf8894e5f29482a80c05c9ed1ce141d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748082"
---
# <a name="compiler-error-c2318"></a>編譯器錯誤 C2318

沒有和 catch 處理常式關聯的 try 區塊

已定義 `catch` 處理常式，但它前面沒有 `try` 區塊。

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

可能的解決方案：

```cpp
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```
