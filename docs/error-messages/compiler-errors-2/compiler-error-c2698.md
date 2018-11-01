---
title: 編譯器錯誤 C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651902"
---
# <a name="compiler-error-c2698"></a>編譯器錯誤 C2698

using 宣告為 'declaration 1' 不能同時存在與 using 宣告為' declaration 2'

一旦[using 宣告](../../cpp/using-declaration.md)資料成員，任何使用不允許使用相同的名稱與相同範圍中的宣告，因為只有函式可以多載。

下列範例會產生 C2698:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```