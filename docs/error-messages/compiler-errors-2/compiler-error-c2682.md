---
title: 編譯器錯誤 C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: c1ce0132ed0db418359effe60f59e1eb2d3cc221
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760279"
---
# <a name="compiler-error-c2682"></a>編譯器錯誤 C2682

無法使用 casting_operator 從 ' type1 ' 轉換為 ' type2 '

轉換運算子嘗試在不相容的類型之間進行轉換。 例如，您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子將指標轉換為參考。 `dynamic_cast` 運算子不能用來轉換掉限定詞。 類型上的所有限定詞都必須相符。

您可以使用 `const_cast` 運算子來移除如 `const`、`volatile`或 `__unaligned`等屬性。

下列範例會產生 C2682：

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

下列範例會產生 C2682：

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
