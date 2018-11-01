---
title: 編譯器錯誤 C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: d7d4898e5f0b55c50a4c18cef053cc150394d7e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485068"
---
# <a name="compiler-error-c2571"></a>編譯器錯誤 C2571

'function': 虛擬函式不能在等位 'union'

等位宣告具有虛擬函式。 您可以宣告只能在類別或結構中的虛擬函式。  可能的解決方式：

1. 將類別或結構的聯集。

1. 讓非虛擬函式。

下列範例會產生 C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```