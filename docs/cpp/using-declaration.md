---
title: using 宣告
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: a158094141307acb507d5f3e873c600e89135ad7
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301271"
---
# <a name="using-declaration"></a>using 宣告

**Using**宣告會將名稱引入宣告式區域，其中會顯示 using 聲明。

## <a name="syntax"></a>語法

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>參數

*嵌套名稱-規範*命名空間、類別或列舉名稱的序列，以及範圍解析運算子（：:)，由範圍解析運算子終止。 單一範圍解析運算子可用來引入全域命名空間中的名稱。 關鍵字**typename**是選擇性的，而且可以在從基類引入類別樣板時用來解析相依名稱。

不*合格-識別碼*不合格的識別碼運算式，可能是識別碼、多載的運算子名稱、使用者定義的常值運算子或轉換函式名稱、類別的析構函數名稱，或範本名稱和引數清單。

宣告子 *-list*以逗號分隔的 [**typename**]*嵌套名稱-規範* *-id*宣告子清單，後面接著選擇性的省略號。

## <a name="remarks"></a>備註

Using 宣告導入了不合格的名稱，做為在其他地方宣告之實體的同義字。 它允許在其出現的宣告區域中，使用特定命名空間的單一名稱，而不需要明確限定。 這與[using](../cpp/namespaces-cpp.md#using_directives)指示詞相反，它允許命名空間中的*所有*名稱都可以使用，而不需要限定。 **Using**關鍵字也用於[類型別名](../cpp/aliases-and-typedefs-cpp.md)。

## <a name="example"></a>範例

Using 宣告可以在類別定義中使用。

```cpp
// using_declaration1.cpp
#include <stdio.h>
class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class D : B {
public:
   using B::f;    // B::f(char) is now visible as D::f(char)
   using B::g;    // B::g(char) is now visible as D::g(char)
   void f(int) {
      printf_s("In D::f()\n");
      f('c');     // Invokes B::f(char) instead of recursing
   }

   void g(int) {
      printf_s("In D::g()\n");
      g('c');     // Invokes B::g(char) instead of recursing
   }
};

int main() {
   D myD;
   myD.f(1);
   myD.g('a');
}
```

```Output
In D::f()
In B::f()
In B::g()
```

## <a name="example"></a>範例

當用來宣告成員時，using 宣告必須參考基類的成員。

```cpp
// using_declaration2.cpp
#include <stdio.h>

class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class C {
public:
   int g();
};

class D2 : public B {
public:
   using B::f;   // ok: B is a base of D2
   // using C::g;   // error: C isn't a base of D2
};

int main() {
   D2 MyD2;
   MyD2.f('a');
}
```

```Output
In B::f()
```

## <a name="example"></a>範例

使用 using 宣告宣告的成員可以使用明確限定性來參考。 `::` 的前置詞是指全域命名空間。

```cpp
// using_declaration3.cpp
#include <stdio.h>

void f() {
   printf_s("In f\n");
}

namespace A {
   void g() {
      printf_s("In A::g\n");
   }
}

namespace X {
   using ::f;   // global f is also visible as X::f
   using A::g;   // A's g is now visible as X::g
}

void h() {
   printf_s("In h\n");
   X::f();   // calls ::f
   X::g();   // calls A::g
}

int main() {
   h();
}
```

```Output
In h
In f
In A::g
```

## <a name="example"></a>範例

進行 using 宣告時，宣告所建立的同義字只會參考在 using 宣告中有效的定義。 在 using 宣告之後加入命名空間的定義，不是有效的同義字。

**Using**宣告所定義的名稱是其原始名稱的別名。 它不會影響原始宣告的類型、連結或其他屬性。

```cpp
// post_declaration_namespace_additions.cpp
// compile with: /c
namespace A {
   void f(int) {}
}

using A::f;   // f is a synonym for A::f(int) only

namespace A {
   void f(char) {}
}

void f() {
   f('a');   // refers to A::f(int), even though A::f(char) exists
}

void b() {
   using A::f;   // refers to A::f(int) AND A::f(char)
   f('a');   // calls A::f(char);
}
```

## <a name="example"></a>範例

相對於命名空間中的函式，如果在宣告式區域中提供了一組針對單一名稱的區域宣告和 using 宣告，則它們必須全都參考相同的實體，或全部都必須參考函式。

```cpp
// functions_in_namespaces1.cpp
// C2874 expected
namespace B {
    int i;
    void f(int);
    void f(double);
}

void g() {
    int i;
    using B::i;   // error: i declared twice
    void f(char);
    using B::f;   // ok: each f is a function
}
```

在上述範例中，`using B::i` 語句會導致在 `g()` 函數中宣告第二個 `int i`。 `using B::f` 語句不會與 `f(char)` 函數衝突，因為 `B::f` 引進的函數名稱具有不同的參數類型。

## <a name="example"></a>範例

區域函式宣告的名稱和類型不能與使用宣告所引進的函式相同。 例如：

```cpp
// functions_in_namespaces2.cpp
// C2668 expected
namespace B {
    void f(int);
    void f(double);
}

namespace C {
    void f(int);
    void f(double);
    void f(char);
}

void h() {
    using B::f;          // introduces B::f(int) and B::f(double)
    using C::f;          // C::f(int), C::f(double), and C::f(char)
    f('h');              // calls C::f(char)
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)
}
```

## <a name="example"></a>範例

就繼承而言，當 using 宣告從基類引入衍生類別範圍的名稱時，衍生類別中的成員函式會覆寫基類中具有相同名稱和引數類型的虛擬成員函式。

```cpp
// using_declaration_inheritance1.cpp
#include <stdio.h>
struct B {
   virtual void f(int) {
      printf_s("In B::f(int)\n");
   }

   virtual void f(char) {
      printf_s("In B::f(char)\n");
   }

   void g(int) {
      printf_s("In B::g\n");
   }

   void h(int);
};

struct D : B {
   using B::f;
   void f(int) {   // ok: D::f(int) overrides B::f(int)
      printf_s("In D::f(int)\n");
   }

   using B::g;
   void g(char) {   // ok: there is no B::g(char)
      printf_s("In D::g(char)\n");
   }

   using B::h;
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)
};

void f(D* pd) {
   pd->f(1);     // calls D::f(int)
   pd->f('a');   // calls B::f(char)
   pd->g(1);     // calls B::g(int)
   pd->g('a');   // calls D::g(char)
}

int main() {
   D * myd = new D();
   f(myd);
}
```

```Output
In D::f(int)
In B::f(char)
In B::g
In D::g(char)
```

## <a name="example"></a>範例

使用宣告中提及之名稱的所有實例都必須可以存取。 特別是，如果衍生類別使用 using 宣告來存取基類的成員，則必須能夠存取該成員名稱。 如果是多載成員函式的名稱，則所有名為的函數都必須是可存取的。

如需成員存取範圍的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。

```cpp
// using_declaration_inheritance2.cpp
// C2876 expected
class A {
private:
   void f(char);
public:
   void f(int);
protected:
   void g();
};

class B : public A {
   using A::f;   // C2876: A::f(char) is inaccessible
public:
   using A::g;   // B::g is a public synonym for A::g
};
```

## <a name="see-also"></a>請參閱

[命名空間](../cpp/namespaces-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)