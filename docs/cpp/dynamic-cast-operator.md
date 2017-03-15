---
title: "dynamic_cast 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "dynamic_cast"
  - "dynamic_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dynamic_cast 關鍵字 [C++]"
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# dynamic_cast 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將運算元 `expression` 轉換至型別 `type-id`的物件。  
  
## 語法  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## 備註  
 `type-id` 必須是指標或指向先前定義的類別的參考或是 「空指標」。  如果 `type-id` 是指標，`expression` 的型別必須為指標，或是如果 `type-id` 為參考，它就是 l\-value。  
  
 請參閱 [static\_cast](../cpp/static-cast-operator.md) 以獲得靜態和動態轉型之間的差異，以及使用時機的說明。  
  
 Managed 程式碼在 `dynamic_cast` 上的行為有兩個重大變更 :  
  
-   `dynamic_cast` 至指向基礎型別為 boxed enum 的指標會在執行階段失敗，如果是轉換後的指標則傳回 0。  
  
-   如果`type-id` 是內部指標至實值型別， `dynamic_cast` 不會再擲回一個例外狀況，而是在執行階段型別轉換失敗。轉換現在會傳回 0 指標值而不會擲回。  
  
 如果 `type-id` 是指向 `expression`的所有可存取的直接或間接基底類別的指針，結果為指向 `type-id` 型別唯一的子物件的指標。  例如：  
  
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
  
 這種轉換稱為 「向上轉型」，因為它往上移動類別階層架構的指標，從衍生類別至它衍生自的類別。  向上轉型是隱含轉換。  
  
 如果 `type-id` 是 void\*，執行階段會進行檢查以判斷 `expression`的實體型別。  結果是由 `expression`指向完全物件的指標。  例如：  
  
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
  
 如果 `type-id` 不是 void\*，執行階段會進行檢查以查看 `expression` 指向的物件是否可轉換成 `type-id`指向的型別。  
  
 如果 `expression` 的型別為 `type-id` 的型別的基底類別，執行階段會檢查是否 `expression` 實際上指向類別為 `type-id` 的完整物件。  如果為 true，則結果是指向 `type-id`類型的完整物件。  例如：  
  
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
  
 這種轉換稱為 「向下轉型」，因為它往下移動類別階層架構中的指標，從衍生自的類別至它衍生的類別。  
  
 在多重繼承的情況下，產生了歧義的可能性。  考慮下圖所示的類別階層架構。  
  
 對於 CLR 型別，在或中 `dynamic_cast` 結果為空操作，如果轉換可以隱含地執行，或者為 MSIL `isinst` 指令，它執行動態檢查，如果轉換失敗傳回 `nullptr` 。  
  
 下列範例使用 `dynamic_cast` 決定類別是否為特定型別執行個體:  
  
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
  
 ![顯示多重繼承的類別階層](../cpp/media/vc39011.png "vc39011")  
顯示多重繼承的類別階層架構  
  
 指向 `D` 型別物件的指標可以安全地轉換為 `B` 或 `C`。  不過，如果 `D` 被轉換為指向 `A` 物件， `A` 將會產生哪一個執行個體?  這樣會造成有歧義的轉換錯誤。  若要避過這個問題，您可以執行兩個明確的轉換。  例如：  
  
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
  
 進一步的歧義會被使用虛擬基底類別時引入。  考慮下圖所示的類別階層架構。  
  
 ![顯示虛擬基底類別的類別階層](../cpp/media/vc39012.png "vc39012")  
顯示虛擬基底類別的類別階層架構  
  
 在階層架構中， `A` 是虛擬基底類別。  虛擬基底類別的定義請參閱 [虛擬基底類別](../misc/virtual-base-classes.md) 。  給予類別為 `E` 的執行個體和指向 `A` 子物件的指標， `dynamic_cast` 至指標 `B` 會因為歧義而失敗。  您必須先轉換回完整的 `E` 物件，然後以明確的方法用您的方式往上移動階層架構，以達到正確的 `B` 物件。  
  
 考慮下圖所示的類別階層架構。  
  
 ![顯示重複基底類別的類別階層](../cpp/media/vc39013.png "vc39013")  
顯示重複基底類別的類別階層架構  
  
 給予型別為 `E` 的物件和指向 `D` 子物件的指標，從 `D` 子物件巡覽到最左邊的 `A` 子物件，三個轉換動作會被進行。  您可以執行從 `D` 指標用 `dynamic_cast` 轉換成 `E` 指標，然後轉換由 \( `dynamic_cast` 或隱含轉換\)  `E` 到 `B` ，最後從 `B` 隱含轉換為 `A`。  例如：  
  
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
  
 `dynamic_cast` 運算子也可以用來執行 「交互轉換」。使用相同類別階層架構，只要完整物件屬於型別 `E`，轉換為指標是可能的，例如，從 `B` 子物件至 `D` 子物件。  
  
 考慮交互轉換，只用兩個步驟做從指至 `D` 的指標至指至最左邊的 `A` 子物件的指標的轉換是可能的。  您可以執行從 `D` 至 `B` 的交互轉型，並從 `B` 隱含轉換為 `A`。  例如：  
  
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
  
 空指標值轉換成目的型別為 `dynamic_cast` 的空指標值。  
  
 當您使用 `dynamic_cast < type-id > ( expression )`時，如果 `expression` 無法安全地轉換成 `type-id`，執行階段檢查將造成轉換失敗。  例如：  
  
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
  
 轉型至指標失敗的值為空指標。  對參考型別的轉換失敗會擲回 [bad\_cast Exception](../cpp/bad-cast-exception.md)。   如果 `expression` 沒有指向或沒有參考有效的物件，就會擲回 `__non_rtti_object` 例外狀況。  
  
 `__non_rtti_object` 例外狀況的說明請參閱 [typeid](../cpp/typeid-operator.md) 。  
  
## 範例  
 下列範例建立指向物件 \(結構 C\) 的基底類別 \(結構\) 指標。這個加上這些是虛擬函式的事實，讓執行階段能夠多型。  
  
 這個範例也會呼叫在階層架構中的非虛擬函式。  
  
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
  
  **在 C**  
**在 B 的 test2**  
**在 GlobalTest**  
**無法轉換為 C**   
## 請參閱  
 [轉型運算子](../cpp/casting-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)