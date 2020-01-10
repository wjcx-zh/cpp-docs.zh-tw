---
title: 編譯器錯誤 C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d0e283c7cd6116655a56f8df67ab4eecf9923b68
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760937"
---
# <a name="compiler-error-c2884"></a>編譯器錯誤 C2884

' name '：使用-宣告引入與區域函數 ' function ' 衝突

您嘗試多次定義函式。 第一個定義是區域定義。 第二個是來自具有 `using` 宣告的命名空間。

下列範例會產生 C2884：

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
