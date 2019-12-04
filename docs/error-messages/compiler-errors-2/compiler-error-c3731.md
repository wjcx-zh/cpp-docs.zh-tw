---
title: 編譯器錯誤 C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 9acf80eec0d36db64fa070d691533e7085754ac0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752947"
---
# <a name="compiler-error-c3731"></a>編譯器錯誤 C3731

不相容的事件 ' function1 ' 和處理常式 ' function2 ';事件來源和事件處理常式必須是相同的類型

事件來源和事件接收者必須有相同的類型 (例如 `native` 類型對 `com` 類型)。 若要修正這個錯誤，請讓事件來源的類型和事件處理常式相符。

下列範例會產生 C3731：

```cpp
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```
