---
title: 編譯器錯誤 C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755183"
---
# <a name="compiler-error-c2698"></a>編譯器錯誤 C2698

' 宣告 1 ' 的 using 宣告不能與 ' 宣告 2 ' 的現有 using 宣告並存

當您有資料成員的[using](../../cpp/using-declaration.md)宣告時，不允許在相同範圍中使用相同名稱的任何 using 宣告，因為只有函式可以多載。

下列範例會產生 C2698：

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
