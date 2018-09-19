---
title: 編譯器錯誤 C2663 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed35dcce056eb3d2a660c154e94b8058563dba7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083687"
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