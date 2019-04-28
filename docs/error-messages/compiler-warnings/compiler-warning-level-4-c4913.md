---
title: 編譯器警告 (層級 4) C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: a06fda0999e5f164fca81917cecbb63312fea25d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359978"
---
# <a name="compiler-warning-level-4-c4913"></a>編譯器警告 (層級 4) C4913

**使用者定義的二進位運算子 ',' 存在，但沒有多載可以轉換所有的運算元，使用預設的內建二進位運算子 ','**

呼叫內建逗號運算子所在的程式中，也有多載的逗號運算子；您認為可能會發生的轉換並未發生。

下列程式碼範例會產生 C4913：

```
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```