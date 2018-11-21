---
title: dynamic_cast 運算子
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176961"
---
# <a name="dynamiccast-operator"></a>dynamic_cast 運算子

將轉換的運算元`expression`物件的型別`type-id`。

## <a name="syntax"></a>語法

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>備註

`type-id`必須是指標，或先前定義的類別類型的參考或 「 為 void 的指標 」。 如果 `type-id` 是指標，則 `expression` 類型必須是指標；或如果 `type-id` 是參考，則為左值 (l-value)。

請參閱[static_cast](../cpp/static-cast-operator.md)需靜態和動態轉型轉換之間，以及適用於每個時的差異的說明。

中的行為有兩項重大變更**dynamic_cast**以 managed 程式碼：

- **dynamic_cast**經過 boxing 處理列舉的基礎類型的指標會在執行階段失敗，傳回 0 而不是轉換後的指標。

- **dynamic_cast**將不會再擲回例外狀況時`type-id`是實值類型，無法在執行階段轉換的內部指標。  轉型，現在會傳回 0 的指標值，而非擲回。

如果`type-id`模稜兩可存取直接或間接基底類別的指標`expression`，唯一的子物件型別的指標`type-id`是結果。 例如: 

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

這種類型的轉換稱為 「 向上轉型 」，因為指標類別階層架構中向上移動從它衍生自的類別衍生的類別。 向上轉型是隱含的轉換。

如果`type-id`是 void * 中，執行階段檢查對判斷的實際型別`expression`。 結果是指向完整物件的指標`expression`。 例如: 

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

如果`type-id`不是 void *，若要查看如果指向的物件進行執行階段檢查`expression`可轉換為所指的型別`type-id`。

如果的型別`expression`的基底類別之型別的`type-id`，以查看是否進行執行階段檢查`expression`確實指向完整的物件之型別的`type-id`。 如果為 true，結果會是完整的物件之型別的指標`type-id`。 例如: 

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

這種類型的轉換稱為 「 向下轉型 」 指標下移類別將特定類別的類別階層，因為它衍生。

在多重繼承的情況下，會介紹模稜兩可的可能性。 請考慮下圖所示的類別階層架構。

針對 CLR 類型， **dynamic_cast**導致沒有選項可以隱含地執行轉換或 MSIL`isinst`指示，它會執行動態檢查，並傳回**nullptr**如果轉換會失敗。

下列範例會使用**dynamic_cast**判斷類別是否為特定類型的執行個體：

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

![類別階層顯示多重繼承](../cpp/media/vc39011.gif "類別顯示多重繼承的階層") <br/>
顯示多重繼承的類別階層

型別的物件的指標`D`可以安全地轉換成`B`或`C`。 不過，如果`D`轉型為指向`A`物件，哪一個執行個體`A`而造成？ 這會導致模稜兩可的轉換錯誤。 若要解決此問題，您可以執行兩個模稜兩可的轉換 （cast）。 例如: 

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   D* pd = new D;
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

當您使用虛擬基底類別時，可能會造成進一步模稜兩可。 請考慮下圖所示的類別階層架構。

![類別會顯示虛擬基底類別的階層](../cpp/media/vc39012.gif "類別顯示虛擬基底類別的階層") <br/>
顯示虛擬基底類別的類別階層

在此階層中，`A`虛擬基底類別。 指定類別的執行個體`E`以及指標`A`子物件**dynamic_cast**指標`B`因為模稜兩可會失敗。 您必須先轉換回完整`E`物件，然後備份階層中，進行以明確的方式，連線到正確`B`物件。

請考慮下圖所示的類別階層架構。

![類別顯示重複基底類別的階層](../cpp/media/vc39013.gif "類別顯示重複基底類別的階層") <br/>
顯示重複基底類別的類別階層

指定類型的物件`E`以及指標`D`子物件，從瀏覽`D`最左邊的子物件`A`子物件，可將三個轉換。 您可以執行**dynamic_cast**從轉換`D`指標`E`指標，則轉換 (任一**dynamic_cast**或隱含的轉換) 從`E`要`B`，以及最後的隱含轉換`B`至`A`。 例如: 

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

**Dynamic_cast**運算子也可用來執行 「 跨轉換 」。 使用相同的類別階層架構，便可從範例中，轉換為指標，`B`子物件至`D`子物件，為完整的物件型別的`E`。

考慮跨轉換 （cast），您可實際執行的指標轉換`D`最左邊指標`A`只有兩個步驟中的子物件。 您可以執行轉換從跨`D`要`B`，然後從的隱含轉換`B`至`A`。 例如: 

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

Null 指標值會轉換為 null 指標值的目的型別所**dynamic_cast**。

當您使用`dynamic_cast < type-id > ( expression )`的話`expression`無法安全地轉換為類型`type-id`，執行階段檢查會導致轉換失敗。 例如: 

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

失敗的型別轉換為指標類型的值是 null 指標。 失敗的轉型至參考型別會擲回[bad_cast 例外狀況](../cpp/bad-cast-exception.md)。   如果`expression`不會指向或參考有效的物件，`__non_rtti_object`擲回例外狀況。

請參閱[typeid](../cpp/typeid-operator.md)如需說明`__non_rtti_object`例外狀況。

## <a name="example"></a>範例

下列範例會建立基底類別 (struct 的) 指標的物件 （C 結構）。  再加上那里的事實是虛擬函式，可讓執行階段的多型。

此範例也會呼叫非虛擬函式階層中。

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

## <a name="see-also"></a>另請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)