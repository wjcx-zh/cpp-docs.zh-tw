---
title: 編譯器錯誤 C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 7e8173c2697a931e5b292dc974b6d1b22f376794
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744104"
---
# <a name="compiler-error-c2452"></a>編譯器錯誤 C2452

' type '： safe_cast 的來源類型無效

[Safe_cast](../../extensions/safe-cast-cpp-component-extensions.md)的來源類型無效。  例如，`safe_cast` 作業中的所有類型都必須是 CLR 類型。

下列範例會產生 C2452：

```cpp
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```
