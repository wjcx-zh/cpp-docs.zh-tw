---
title: 作法：在 C++/CLI 中使用 safe_cast
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: 56ac19871bcdc5162b959f6d60103387551ac2a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225653"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>作法：在 C++/CLI 中使用 safe_cast

本文說明如何在 c + +/CLI 應用程式中使用 safe_cast。 如需 c + +/CX 中 safe_cast 的詳細資訊，請參閱[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)。

## <a name="upcasting"></a>Upcasting

向上轉換是從衍生類型轉型為它的其中一個基類。 這種轉換是安全的，不需要明確的轉換標記法。 下列範例顯示如何使用和不搭配執行向上轉換 `safe_cast` 。

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>向下檢視

轉換是從基類轉換成衍生自基類的類別。  只有在執行時間所定址的物件實際定址衍生類別物件時，向下轉換才是安全的。  不同 **`static_cast`** `safe_cast` 于，會執行動態檢查，並 <xref:System.InvalidCastException> 在轉換失敗時擲回。

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>使用者定義的轉換 safe_cast

下一個範例會顯示如何使用來叫用 `safe_cast` 使用者定義的轉換。

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>safe_cast 和裝箱作業

### <a name="boxing"></a>Box 處理

「裝箱」定義為編譯器插入的使用者定義轉換。  因此，您可以使用 `safe_cast` 來 BOX CLR 堆積上的值。

下列範例示範如何使用簡單和使用者定義的實數值型別來進行裝箱。  一個方塊，它是 `safe_cast` 原生堆疊上的實值型別變數，可以將它指派給垃圾收集堆積上的變數。

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

下一個範例顯示，在作業中，在使用者定義的轉換上，該裝箱的優先順序高於 `safe_cast` 。

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Unbox 處理

取消裝箱會定義為編譯器插入的使用者定義轉換。  因此，您可以使用 `safe_cast` 將 CLR 堆積上的值取消裝箱。

取消裝箱是使用者定義的轉換，但與裝箱不同的是，取消裝箱必須是明確的，也就是必須由 C 樣式的轉換來執行， **`static_cast`** 或者，無法以隱含方式 `safe_cast` 執行取消錄製。

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

下列範例會顯示具有實數值型別和基本類型的取消裝箱。

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>safe_cast 和泛型型別

下一個範例會示範如何使用 `safe_cast` 來執行具有泛型型別的向下轉換。

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>另請參閱

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
