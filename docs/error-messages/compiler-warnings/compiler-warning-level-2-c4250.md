---
title: 編譯器警告 (層級 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 8baf3c03c87dc70a80b785d7f81cbee4e1d828f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454856"
---
# <a name="compiler-warning-level-2-c4250"></a>編譯器警告 (層級 2) C4250

'class1': 繼承 'class2::member'，經由支配

兩個或多個成員具有相同的名稱。 中的一個`class2`因為它是包含此成員的其他類別的基底類別繼承。

若要抑制 C4250，請使用[警告](../../preprocessor/warning.md)pragma。

因為多個衍生類別之間共用虛擬基底類別，衍生類別中的名稱會主導的基底類別中的名稱。 比方說，假設下列類別階層架構，有兩個定義的函式在菱形中繼承： 經由弱式類別，並與基準:: func （） 透過主控類別 vbc::func() 執行個體。 Func （） 透過菱形類別物件，不合格的呼叫一律會呼叫 dominate:: func （） 執行個體。  介紹 func （） 的執行個體的弱式類別一樣，都不會支配定義，並呼叫會標示為模稜兩可。

```
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

## <a name="example"></a>範例

下列範例會產生 C4250。

```
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

## <a name="example"></a>範例

此範例會示範一個比較複雜狀況。 下列範例會產生 C4250。

```
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```