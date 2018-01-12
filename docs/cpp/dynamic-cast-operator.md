---
title: "dynamic_cast 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: dynamic_cast_cpp
dev_langs: C++
helpviewer_keywords: dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29add795c7adeca67fc85c7cf3b1b90d17f804fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dynamiccast-operator"></a>dynamic_cast 運算子
將運算元轉換`expression`物件的型別`type-id`。  
  
## <a name="syntax"></a>語法  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>備註  
 `type-id`必須是指標，或先前定義的類別類型的參考或"void 的指標 」。 如果 `type-id` 是指標，則 `expression` 類型必須是指標；或如果 `type-id` 是參考，則為左值 (l-value)。  
  
 請參閱[static_cast](../cpp/static-cast-operator.md)需靜態和動態轉型轉換之間，則會適當地使用每個差異的說明。  
  
 行為中有兩個重大變更`dynamic_cast`在 managed 程式碼：  
  
-   `dynamic_cast`boxed 列舉的基礎類型的指標將會在執行階段，傳回 0 而不是轉換後的游標失敗。  
  
-   `dynamic_cast`將不會再擲回例外狀況時`type-id`是實值類型，以轉換在執行階段失敗的內部指標。  轉型現在會傳回 0 的指標值，而不是擲回。  
  
 如果`type-id`是模稜兩可存取直接或間接基底類別指標`expression`，唯一的子物件類型的指標`type-id`是結果。 例如:   
  
```  
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
  
 這種轉換稱為 「 向上轉型 」，因為它移動從它衍生自的類別衍生類別的類別階層架構往上的指標。 向上轉型為隱含轉換。  
  
 如果`type-id`是 void * 進行執行階段檢查，以決定實際的類型`expression`。 結果為指向完整物件的指標`expression`。 例如:   
  
```  
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
  
 如果`type-id`不是 void * 若要查看如果指向的物件進行執行階段檢查`expression`可以轉換成所指向的類型`type-id`。  
  
 如果類型`expression`基底類別的型別`type-id`，進行執行階段檢查，以查看是否`expression`確實指向完整物件的型別`type-id`。 如果為 true，結果會是完整的物件類型的指標`type-id`。 例如:   
  
```  
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
  
 這種類型的轉換稱為 「 向下轉型 」 因為指標下移類別階層架構，從指定類別的類別衍生自它。  
  
 在多重繼承的情況下，會產生模稜兩可的可能性。 請考慮下圖所示的類別階層。  
  
 針對 CLR 類型，`dynamic_cast`會導致執行任何作業可以隱含地執行轉換或 MSIL`isinst`指令，以執行動態檢查，並傳回`nullptr`如果轉換失敗。  
  
 下列範例會使用`dynamic_cast`判斷類別是否為特定類型的執行個體：  
  
```  
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
  
 ![類別階層顯示多重繼承的](../cpp/media/vc39011.gif "vc39011")  
顯示多重繼承的類別階層架構  
  
 類型的物件的指標`D`可以安全地轉換成`B`或`C`。 不過，如果`D`轉型為指向`A`物件，哪一個執行個體`A`會產生嗎？ 這會導致模稜兩可的轉換錯誤。 若要解決這個問題，您可以執行兩個明確的轉換 （cast）。 例如:   
  
```  
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
  
 當您使用虛擬基底類別時，可以導入進一步模稜兩可。 請考慮下圖所示的類別階層。  
  
 ![類別會顯示虛擬基底類別的階層](../cpp/media/vc39012.gif "vc39012")  
顯示虛擬基底類別的類別階層  
  
 這個階層中，`A`是虛擬基底類別。 指定類別的執行個體`E`以及一個指向`A`子物件，`dynamic_cast`指標`B`將會失敗，因為模稜兩可。 您必須先轉換回完整`E`物件，然後處理模稜兩可的方式，連線到正確的備份，在階層`B`物件。  
  
 請考慮下圖所示的類別階層。  
  
 ![類別階層顯示重複基底類別的](../cpp/media/vc39013.gif "vc39013")  
顯示重複基底類別的類別階層  
  
 指定型別的物件`E`以及一個指向`D`子物件，從瀏覽`D`最左邊的子物件`A`子物件，才能進行三個轉換。 您可以執行`dynamic_cast`從轉換`D`指標`E`指標，則轉換 (可能是`dynamic_cast`或隱含轉換) 從`E`至`B`，以及最後的隱含轉換`B`至`A`。 例如:   
  
```  
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
  
 `dynamic_cast`運算子也可用來執行 「 交叉轉換 」。 使用相同的類別階層架構，便可從範例中，轉換為指標，`B`子物件至`D`子物件，只要完成的物件屬於類型`E`。  
  
 考慮跨轉型，您可實際執行從指標轉換`D`最左邊指標`A`只有兩個步驟中的子物件。 您可以執行轉換成交叉`D`至`B`，然後從的隱含轉換`B`至`A`。 例如:   
  
```  
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
  
 Null 指標值會轉換成目的地類型的 null 指標值`dynamic_cast`。  
  
 當您使用`dynamic_cast < type-id > ( expression )`，如果`expression`無法安全地轉換成輸入`type-id`，執行階段檢查會導致轉換失敗。 例如:   
  
```  
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
  
 失敗成指標類型的值是轉換的 null 指標。 參考型別會擲回轉換失敗[bad_cast 例外狀況](../cpp/bad-cast-exception.md)。   如果`expression`不會指向或參考有效的物件，`__non_rtti_object`擲回例外狀況。  
  
 請參閱[typeid](../cpp/typeid-operator.md)取得說明`__non_rtti_object`例外狀況。  
  
## <a name="example"></a>範例  
 下列範例會建立基底類別 (struct A) 指標的物件 (struct C)。  再加上那里的事實虛擬函式，可讓執行階段的多型。  
  
 此範例也會呼叫非虛擬函式階層中。  
  
```  
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
 [轉型運算子](../cpp/casting-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)