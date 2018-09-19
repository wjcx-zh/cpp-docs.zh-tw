---
title: 編譯器警告 （層級 1） C4020 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4020
dev_langs:
- C++
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0303c1a811304cd2edaa8622208dc4bada86ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046728"
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