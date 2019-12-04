---
title: 編譯器錯誤 C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758901"
---
# <a name="compiler-error-c2247"></a>編譯器錯誤 C2247

無法存取 ' identifier '，因為 ' class ' 使用 ' 規範 ' 繼承自 ' class '

`identifier` 繼承自使用私用或受保護存取所宣告的類別。

下列範例會產生 C2247：

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

針對 Visual Studio .NET 2003 執行的編譯器一致性工作，也可能會產生此錯誤：具有受保護成員的存取控制。 只能透過繼承自其（n）所屬類別（A）之類別（B）的成員函式來存取受保護的成員（n）。

對於在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效的程式碼，請將該成員宣告為該類型的 friend。 也可以使用公用繼承。

```cpp
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

針對 Visual Studio .NET 2003 進行的編譯器一致性工作，也可能會產生 C2247：私用基類現在無法存取。 屬於類型（B）之私用基類的類別（A），不應可供使用 B 做為基類的類型（C）存取。

對於在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效的程式碼，請使用範圍運算子。

```cpp
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```
