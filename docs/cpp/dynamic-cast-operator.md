---
title: dynamic_cast 運算子
description: 語言 dynamic_cast 運算子C++的總覽。
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 0073aaa886bba33a0ec6c07fb89d6eee032765c8
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972225"
---
# <a name="dynamic_cast-operator"></a>dynamic_cast 運算子

將運算元 `expression` 轉換成 `type-id`類型的物件。

## <a name="syntax"></a>語法

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>備註

`type-id` 必須是指標，或參考先前定義的類別類型或「void 的指標」。 如果 `type-id` 是指標，則 `expression` 類型必須是指標；或如果 `type-id` 是參考，則為左值 (l-value)。

如需靜態和動態轉型轉換之間的差異，以及何時適合使用各項的說明，請參閱[static_cast](../cpp/static-cast-operator.md) 。

Managed 程式碼中**dynamic_cast**的行為有兩個重大變更：

- 在執行時間，對已裝箱列舉之基礎類型的指標**dynamic_cast**將會失敗，傳回0而不是已轉換的指標。

- 當 `type-id` 是實值型別的內部指標，而且在執行時間發生轉換失敗時， **dynamic_cast**將不會再擲回例外狀況。  轉換現在會傳回0指標值，而不是擲回。

如果 `type-id` 是 `expression`明確存取的直接或間接基類的指標，則 `type-id` 類型之唯一子物件的指標就是結果。 例如：

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

這種類型的轉換稱為「向上連結」，因為它會將指標向上移動到類別階層，從衍生的類別到衍生自的類別。 向上轉換是隱含的轉換。

如果 `type-id` 為 void *，就會進行執行時間檢查，以判斷 `expression`的實際類型。 結果是 `expression`所指向之完整物件的指標。 例如：

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

如果 `type-id` 不是 void *，就會進行執行時間檢查，以查看是否 `expression` 所指向的物件可以轉換成 `type-id`所指向的類型。

如果 `expression` 的類型是 `type-id`類型的基類，則會進行執行時間檢查，以查看 `expression` 是否實際指向 `type-id`類型的完整物件。 如果這是 true，則結果會是 `type-id`類型之完整物件的指標。 例如：

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

這種類型的轉換稱為「轉換」，因為它會將指標向下移動類別階層，從指定的類別到衍生自它的類別。

在多重繼承的情況下，會引進不明確的可能性。 請考慮下圖所示的類別階層。

針對 CLR 型別，如果轉換可以隱含執行，則**dynamic_cast**會導致無 op，或是執行動態檢查的 MSIL `isinst` 指令，如果轉換失敗，則會傳回**nullptr** 。

下列範例會使用**dynamic_cast**來判斷類別是否為特定類型的實例：

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![顯示多重繼承的類別階層](../cpp/media/vc39011.gif "顯示多重繼承的類別階層") <br/>
顯示多重繼承的類別階層

`D` 類型之物件的指標可以安全地轉換成 `B` 或 `C`。 不過，如果 `D` 轉換成指向 `A` 物件，`A` 的實例會產生什麼結果？ 這會導致不明確的轉換錯誤。 若要解決這個問題，您可以執行兩個明確的轉換。 例如：

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

當您使用虛擬基類時，可以引進進一步的歧義。 請考慮下圖所示的類別階層。

![顯示虛擬基類的類別階層](../cpp/media/vc39012.gif "顯示虛擬基底類別的類別階層") <br/>
顯示虛擬基底類別的類別階層

在此階層中，`A` 是虛擬基類。 假設類別的實例 `E`，而 `A` 子物件的指標，則 `B` 指標的**dynamic_cast**將會因為不明確而失敗。 您必須先轉型回完整的 `E` 物件，然後以明確的方式來備份階層，以達到正確的 `B` 物件。

請考慮下圖所示的類別階層。

![顯示重複基類的類別階層](../cpp/media/vc39013.gif "顯示重複基底類別的類別階層") <br/>
顯示重複基底類別的類別階層

假設 `E` 類型的物件和指向 `D` 子物件的指標，從 `D` 的子物件導覽到最左邊的 `A` 子物件，就可以進行三項轉換。 您可以從 `E` 指標的 `D` 指標執行**dynamic_cast**轉換，然後從 `E` **dynamic_cast**轉換成 `B`，最後是從 `B` 隱含轉換成 `A`）。 例如：

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

**Dynamic_cast**運算子也可以用來執行「交叉轉型」。 使用相同的類別階層時，您可以將指標（例如，從 `B` 子物件轉換成 `D` 子物件），只要完整的物件屬於類型 `E`。

考慮交叉轉型，實際上可以在兩個步驟中，從指標將 `D` 轉換為最左邊 `A` 子物件的指標。 您可以執行從 `D` 到 `B`的交叉轉型，然後從 `B` 隱含轉換到 `A`。 例如：

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Null 指標值會藉由**dynamic_cast**，轉換為目的地類型的 null 指標值。

當您使用 `dynamic_cast < type-id > ( expression )`時，如果 `expression` 無法安全地轉換成類型 `type-id`，執行時間檢查會導致轉換失敗。 例如：

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

轉換成指標類型的失敗值為 null 指標。 轉換成參考型別的失敗會擲回[Bad_cast 例外](../cpp/bad-cast-exception.md)狀況。   如果 `expression` 未指向或參考有效的物件，則會擲回 `__non_rtti_object` 例外狀況。

如需 `__non_rtti_object` 例外狀況的說明，請參閱[typeid](../cpp/typeid-operator.md) 。

## <a name="example"></a>範例

下列範例會建立基類（結構 A）指標，指向物件（結構 C）。  這也是虛擬函式的事實，可啟用執行時間多型。

此範例也會呼叫階層中的非虛擬函式。

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)