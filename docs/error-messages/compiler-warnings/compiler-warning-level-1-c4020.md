---
title: 編譯器警告（層級1） C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: ccab8eaac42932491fc8b88cd28f2d3334b2e849
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626314"
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

可能的解決方式：

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```