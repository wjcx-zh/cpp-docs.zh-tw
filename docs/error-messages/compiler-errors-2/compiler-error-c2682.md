---
title: 編譯器錯誤 C2682 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2682
dev_langs:
- C++
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc19170729d7203b57e305ef2c8a0d2b2d6de1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049198"
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