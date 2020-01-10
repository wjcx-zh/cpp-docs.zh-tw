---
title: 編譯器警告（層級2） C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 03826f10659cbdf6035cd4dedebecca3e3302e3a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052120"
---
# <a name="compiler-warning-level-2-c4250"></a>編譯器警告（層級2） C4250

' class1 '：透過支配繼承 ' class2：： member '

有兩個或多個成員具有相同的名稱。 `class2` 中的會被繼承，因為它是包含這個成員之其他類別的基類。

若要隱藏 C4250，請使用[warning](../../preprocessor/warning.md) pragma。

由於虛擬基類是在多個衍生類別之間共用，因此衍生類別中的名稱會主導基類中的名稱。 例如，假設有下列類別階層架構，則在菱形中會繼承兩個 func 的定義：使用弱式類別的 vbc：： func （）實例，以及透過主要類別的主要：： func （）。 透過菱形類別物件的 func （）不合格呼叫，一律會呼叫「中」：： func （）實例。  如果弱式類別要引進 func （）的實例，則兩種定義都不會被佔據，而且呼叫會標示為不明確。

```cpp
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

```cpp
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

這個範例會顯示更複雜的情況。 下列範例會產生 C4250。

```cpp
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