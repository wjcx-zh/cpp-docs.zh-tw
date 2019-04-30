---
title: 編譯器錯誤 C2245
ms.date: 11/04/2016
f1_keywords:
- C2245
helpviewer_keywords:
- C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
ms.openlocfilehash: 53288d86a59fe2cd31ddac4af7766360544c65c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403033"
---
# <a name="compiler-error-c2245"></a>編譯器錯誤 C2245

將不存在的成員函式 'function' 指定為 friend (成員函式簽章不符合任何多載)

編譯器找不到指定為 friend 的函式。

下列範例會產生 C2245：

```
// C2245.cpp
// compile with: /c
class B {
   void f(int i);
};

class A {
   int m_i;
   friend void B::f(char);   // C2245
   // try the following line instead
   // friend void B::f(int);
};

void B::f(int i) {
   A a;
   a.m_i = 0;
}
```