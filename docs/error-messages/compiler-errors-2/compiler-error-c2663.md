---
title: 編譯器錯誤 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f9746ecb41e873fb1d929a939c78f1817dc0e2f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220271"
---
# <a name="compiler-error-c2663"></a>編譯器錯誤 C2663

' function '：數位多載沒有 ' this ' 指標的合法轉換

編譯器無法轉換為成員函式的任何多載 **`this`** 版本。

這個錯誤可能是因為在物件上叫用非成員函式所造成 **`const`** **`const`** 。  可能的解決方式：

1. **`const`** 從物件宣告中移除。

1. 將加入 **`const`** 其中一個成員函式多載。

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
