---
title: 編譯器錯誤 C2387
ms.date: 11/04/2016
f1_keywords:
- C2387
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
ms.openlocfilehash: df9e92bfa333be88e860bbdecd5acaa64ec80440
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393671"
---
# <a name="compiler-error-c2387"></a>編譯器錯誤 C2387

'type': 模稜兩可的基底類別

編譯器無法明確地解析函式呼叫因為函式存在於一個以上的基底類別。

若要解決這個錯誤，請移除其中一個基底類別繼承，或是明確限定函式呼叫。

下列範例會產生 C2387:

```
// C2387.cpp
namespace N1 {
   struct B {
      virtual void f() {
      }
   };
}

namespace N2 {
   struct B {
      virtual void f() {
      }
   };
}

struct D : N1::B, N2::B {
   virtual void f() {
      B::f();   // C2387
      // try the following line instead
      // N1::B::f();
   }
};

int main() {
   D aD;
   aD.f();
}
```