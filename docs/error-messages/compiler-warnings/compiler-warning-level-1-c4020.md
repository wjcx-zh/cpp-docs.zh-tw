---
title: 編譯器警告（層級1） C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 2136e94a261b2f767165e43acfd66583e8d15e9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164582"
---
# <a name="compiler-warning-level-1-c4020"></a>編譯器警告（層級1） C4020

' function '：太多實際參數

函式呼叫中的實際參數數目超過函數原型或定義中的型式參數數目。 編譯器會根據函數的呼叫慣例，傳遞額外的實際參數。

下列範例會產生 C4020：

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

可能的解決方案：

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```
