---
title: 編譯器錯誤 C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266266"
---
# <a name="compiler-error-c2682"></a>編譯器錯誤 C2682

無法使用 casting_operator 從 'type1' 轉換成 'type2'

不相容的類型之間轉換嘗試轉型運算子。 例如，您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)指標轉換為參考的運算子。 `dynamic_cast`運算子不適用於能限定詞。 必須符合所有類型的限定詞。

您可以使用`const_cast`運算子來移除屬性，例如`const`， `volatile`，或`__unaligned`。

下列範例會產生 C2682:

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

下列範例會產生 C2682:

```
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