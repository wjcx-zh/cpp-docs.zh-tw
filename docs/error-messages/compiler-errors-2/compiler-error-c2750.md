---
title: 編譯器錯誤 C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 56f4e6e1d6c392fc377fe5fdf11643ae8a2e503a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759603"
---
# <a name="compiler-error-c2750"></a>編譯器錯誤 C2750

' type '：不能在參考型別上使用 ' new ';請改用 ' gcnew '

若要建立 CLR 型別的實例，使實例放在垃圾收集堆積上，您必須使用[gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)。

下列範例會產生 C2750：

```cpp
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```
