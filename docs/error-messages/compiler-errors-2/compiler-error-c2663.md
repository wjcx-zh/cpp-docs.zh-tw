---
title: 編譯器錯誤 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756028"
---
# <a name="compiler-error-c2663"></a>編譯器錯誤 C2663

' function '：數位多載沒有 ' this ' 指標的合法轉換

編譯器無法將 `this` 轉換為成員函式的任何多載版本。

這個錯誤可能是因為在 `const` 物件上叫用非`const` 的成員函式所造成。  可能的解決方式：

1. 從物件宣告中移除 `const`。

1. 將 `const` 加入其中一個成員函式多載。

下列範例會產生 C2663：

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
