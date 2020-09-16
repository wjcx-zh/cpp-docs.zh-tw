---
title: 編譯器錯誤 C3867
ms.date: 11/04/2016
f1_keywords:
- C3867
helpviewer_keywords:
- C3867
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
ms.openlocfilehash: 40825bf92a892917f815c955ee4ba1fb6fa906c3
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686414"
---
# <a name="compiler-error-c3867"></a>編譯器錯誤 C3867

' func '：函式呼叫遺漏引數清單;使用 ' &func ' 來建立成員的指標

您嘗試取得成員函式的位址，而未使用其類別名稱和傳址運算子來限定成員函式。

這項錯誤也可能是因為針對 Visual Studio 2005：增強的成員指標一致性所進行的編譯器一致性工作所產生。 在 Visual Studio 2005 之前編譯的程式碼現在會產生 C3867。

## <a name="examples"></a>範例

使用誤導的建議解決方法，即可從編譯器發出 C3867。 若可能，請使用最新衍生的類別。

下列範例會產生 C3867，並示範如何修正此問題。

```cpp
// C3867_1.cpp
// compile with: /c
struct Base {
protected:
   void Test() {}
};

class Derived : public Base {
   virtual void Bar();
};

void Derived::Bar() {
   void (Base::*p1)() = Test;   // C3867
   &Derived::Test;   // OK
}
```

下列範例會產生 C3867，並示範如何修正此問題。

```cpp
// C3867_2.cpp
#include<stdio.h>

struct S {
   char *func() {
      return "message";
   }
};

class X {
public:
   void f() {}
};

int main() {
   X::f;   // C3867

   // OK
   X * myX = new X;
   myX->f();

   S s;
   printf_s("test %s", s.func);   // C3867
   printf_s("test %s", s.func());   // OK
}
```

下列範例會產生 C3867，並示範如何修正此問題。

```cpp
// C3867_3.cpp
class X {
public:
   void mf(){}
};

int main() {
   void (X::*pmf)() = X::mf;   // C3867

   // try the following line instead
   void (X::*pmf2)() = &X::mf;
}
```

下列範例會產生 C3867。

```cpp
// C3867_4.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b1;
      b1.p = f;   // C3867
   }
};
```

下列範例會產生 C3867。

```cpp
// C3867_5.cpp
// compile with: /EHsc
#include <iostream>

class Testpm {
public:
   void m_func1() {
      std::cout << m_num << "\tm_func1\n";
    }

   int m_num;
   typedef void (Testpm::*pmfn1)();
   void func(Testpm* p);
};

void Testpm::func(Testpm* p) {
   pmfn1 s = m_func1;   // C3867
   pmfn1 s2 = &Testpm::m_func1;   // OK
   (p->*s2)();
}

int main() {
   Testpm *pTestpm = new Testpm;
   pTestpm->m_num = 10;

   pTestpm->func(pTestpm);
}
```
