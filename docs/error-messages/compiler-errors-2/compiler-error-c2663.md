---
title: 編譯器錯誤 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644336"
---
# <a name="compiler-error-c2663"></a>編譯器錯誤 C2663

'function': 數字的多載包含有 'this' 指標不合法轉換

編譯器無法將轉換`this`任何成員函式多載版本。

此錯誤可能因叫用非`const`成員函式`const`物件。  可能的解決方式：

1. 移除`const`從物件宣告。

1. 新增`const`其中一個成員函式多載。

下列範例會產生 C2663:

```
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