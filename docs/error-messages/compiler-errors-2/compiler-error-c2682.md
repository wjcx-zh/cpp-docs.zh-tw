---
title: 編譯器錯誤 C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 2697ce5a790fffe762d97ca3380853514de6d437
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220258"
---
# <a name="compiler-error-c2682"></a>編譯器錯誤 C2682

無法使用 casting_operator 從 ' type1 ' 轉換為 ' type2 '

轉換運算子嘗試在不相容的類型之間進行轉換。 例如，您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子將指標轉換為參考。 **`dynamic_cast`** 運算子不能用來轉換掉限定詞。 類型上的所有限定詞都必須相符。

您可以使用 **`const_cast`** 運算子來移除屬性 **`const`** ，例如、 **`volatile`** 或 **`__unaligned`** 。

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
