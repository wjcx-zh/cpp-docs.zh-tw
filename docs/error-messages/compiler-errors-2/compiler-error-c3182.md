---
title: 編譯器錯誤 C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: 6866c7bbcee0a4097e490b344c79a6eec7f94570
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626742"
---
# <a name="compiler-error-c3182"></a>編譯器錯誤 C3182

'class': using 宣告或存取宣告的成員是在 managed 或 WinRTtype 不合法

A[使用](../../cpp/using-declaration.md)內所有形式的 managed 類別的宣告無效。

下列範例會產生 C3182，並說明如何加以修正。

```
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
