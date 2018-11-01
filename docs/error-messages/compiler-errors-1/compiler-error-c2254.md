---
title: 編譯器錯誤 C2254
ms.date: 11/04/2016
f1_keywords:
- C2254
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
ms.openlocfilehash: da89741811bbb9055f3f6793d115a357d80ab79a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629147"
---
# <a name="compiler-error-c2254"></a>編譯器錯誤 C2254

'function': 純規範或抽象覆寫規範不允許在 friend 函式

A`friend`函式指定為純`virtual`。

下列範例會產生 C2254:

```
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```