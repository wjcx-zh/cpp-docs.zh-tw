---
title: 編譯器警告 （層級 1） C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 75148c210ddd2a611061d58c036d12c084f442cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482022"
---
# <a name="compiler-warning-level-1-c4020"></a>編譯器警告 （層級 1） C4020

'function': 實質參數太多

函式呼叫中的實際參數數目超過函式原型或定義中的型式參數的數目。 編譯器傳遞這些額外實際的參數，根據函式的呼叫慣例。

下列範例會產生 C4020:

```
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

可能的解決方式：

```
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```