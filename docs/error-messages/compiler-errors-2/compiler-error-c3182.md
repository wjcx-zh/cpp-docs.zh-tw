---
title: 編譯器錯誤 C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: c6b183eb30dd0e617e69ab9aac58bea5cb721591
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761656"
---
# <a name="compiler-error-c3182"></a>編譯器錯誤 C3182

' class '：在 managed 或 WinRTtype 中，成員 using 宣告或存取宣告不合法

在所有形式的 managed 類別中， [using](../../cpp/using-declaration.md)宣告無效。

下列範例會產生 C3182，並說明如何加以修正。

```cpp
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
