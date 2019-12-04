---
title: 編譯器錯誤 C3736
ms.date: 11/04/2016
f1_keywords:
- C3736
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
ms.openlocfilehash: 9c4626164fe8fe3fb932fba3ae8e87c774f5aeec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752843"
---
# <a name="compiler-error-c3736"></a>編譯器錯誤 C3736

' event '：必須是方法，或在 managed 事件的情況下，選擇性地是資料成員

原生和 COM 事件必須是方法。 .NET 事件也可以是資料成員。

下列範例會產生 C3736：

```cpp
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```
