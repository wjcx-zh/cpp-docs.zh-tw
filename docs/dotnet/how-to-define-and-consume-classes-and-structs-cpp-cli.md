---
title: 如何： 定義和使用類別和結構 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8356d96b0193566814c0d52173a03a3a79d08d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定義與使用類別和結構 (C++/CLI)
本文將說明如何定義與使用使用者定義的參考類型和實值類型，在 C + + /CLI。  
  
##  <a name="BKMK_Contents"></a> 內容  
 [物件具現化](#BKMK_Object_instantiation)  
  
 [隱含抽象類別](#BKMK_Implicitly_abstract_classes)  
  
 [類型可視性](#BKMK_Type_visibility)  
  
 [成員可視性](#BKMK_Member_visibility)  
  
 [公用和私用原生類別](#BKMK_Public_and_private_native_classes)  
  
 [靜態建構函式](#BKMK_Static_constructors)  
  
 [語意的 this 指標](#BKMK_Semantics_of_the_this_pointer)  
  
 [依簽章隱藏型函式](#BKMK_Hide_by_signature_functions)  
  
 [複製建構函式](#BKMK_Copy_constructors)  
  
 [解構函式與完成項](#BKMK_Destructors_and_finalizers)  
  
##  <a name="BKMK_Object_instantiation"></a> 物件具現化  
 參考 (ref) 類型和實值類型可以只具現化 managed 堆積上、 不是在堆疊或原生堆積上。  
  
```  
// mcppv2_ref_class2.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
  
   // nested class  
   ref class MyClass2 {  
   public:  
      int i;  
   };  
  
   // nested interface  
   interface struct MyInterface {  
      void f();  
   };  
};  
  
ref class MyClass2 : public MyClass::MyInterface {  
public:  
   virtual void f() {  
      System::Console::WriteLine("test");  
   }  
};  
  
public value struct MyStruct {  
   void f() {  
      System::Console::WriteLine("test");  
   }     
};  
  
int main() {  
   // instantiate ref type on garbage-collected heap  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass -> i = 4;  
  
   // instantiate value type on garbage-collected heap  
   MyStruct ^ p_MyStruct = gcnew MyStruct;  
   p_MyStruct -> f();  
  
   // instantiate value type on the stack  
   MyStruct p_MyStruct2;  
   p_MyStruct2.f();  
  
   // instantiate nested ref type on garbage-collected heap  
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;  
   p_MyClass2 -> i = 5;  
}  
```  
  
##  <a name="BKMK_Implicitly_abstract_classes"></a> 隱含抽象類別  
 *隱含抽象類別*無法具現化。 如果類別的基底類型是介面，且該類別未實作所有介面的成員函式，是隱含抽象類別。  
  
 如果您無法建構衍生自介面類別的物件，原因可能是隱含抽象類別。 如需抽象類別的詳細資訊，請參閱[抽象](../windows/abstract-cpp-component-extensions.md)。  
  
 下列程式碼範例會示範`MyClass`因為類別無法具現化函式`MyClass::func2`未實作。 若要啟用來編譯範例，請取消註解`MyClass::func2`。  
  
```  
// mcppv2_ref_class5.cpp  
// compile with: /clr  
interface struct MyInterface {  
   void func1();  
   void func2();  
};  
  
ref class MyClass : public MyInterface {  
public:  
   void func1(){}  
   // void func2(){}  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259   
                                          // To resolve, uncomment MyClass::func2.  
}  
```  
  
##  <a name="BKMK_Type_visibility"></a> 類型可視性  
 您可以控制 common language runtime (CLR) 類型的可見性，如此在參考組件時，如果組件中的類型可以是可見或不在組件外部可見。  
  
 `public` 指出類型可包含任何原始程式檔看見`#using`包含類型的組件指示詞。  `private` 指出類型不是包含來源檔案顯示`#using`包含類型的組件指示詞。 不過，私用類型都在相同的組件內為可見的。 根據預設，類別的可見性是`private`。  
  
 根據預設，Visual c + + 2005年之前，原生型別必須在組件外部的公用存取範圍。 啟用[編譯器警告 （層級 1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)可協助您查看私用原生型別會使用的位置不正確。 使用[make_public](../preprocessor/make-public.md) pragma 提供公用存取範圍不能修改原始程式碼檔案中的原生型別。  
  
 如需詳細資訊，請參閱[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。  
  
 下列範例會示範如何宣告型別，並指定其存取範圍，然後再存取這些類型在組件。 當然，如果具有私用類型的組件使用參考`#using`，只有在組件中的公用類型會顯示。  
  
```  
// type_visibility.cpp  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// default accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   Private_Class ^ b = gcnew Private_Class;  
   b->Test();  
  
   Private_Class_2 ^ c = gcnew Private_Class_2;  
   c->Test();  
}  
```  
  
 **輸出**  
  
```Output  
in Public_Class  
in Private_Class  
in Private_Class_2  
```  
  
 現在，使其建置為 DLL，讓我們來重寫前一個範例。  
  
```  
// type_visibility_2.cpp  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside the assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// by default, accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
```  
  
 下一個範例示範如何存取組件之外的型別。 在此範例中，用戶端會使用內建於前一個範例的元件。  
  
```  
// type_visibility_3.cpp  
// compile with: /clr  
#using "type_visibility_2.dll"  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   // private types not accessible outside the assembly  
   // Private_Class ^ b = gcnew Private_Class;  
   // Private_Class_2 ^ c = gcnew Private_Class_2;  
}  
```  
  
 **輸出**  
  
```Output  
in Public_Class  
```  
  
##  <a name="BKMK_Member_visibility"></a> 成員可視性  
 您可以對存取相同組件中的公用類別的成員不同於存取從組件外部使用成對的存取規範`public`， `protected`，和 `private`  
  
 本表會摘要說明各種不同的存取規範的效果：  
  
|指定名稱|作用|  
|---------------|------------|  
|public|成員可存取的內部與外部組件。  請參閱[公用](../cpp/public-cpp.md)如需詳細資訊。|  
|private|成員不是可在內部都在組件外部存取。  請參閱[私人](../cpp/private-cpp.md)如需詳細資訊。|  
|protected|存取內部和外部組件，而只是衍生型別成員。  請參閱[保護](../cpp/protected-cpp.md)如需詳細資訊。|  
|internal|成員是公用的在組件但私用組件之外。  `internal` 是即時線上關鍵字。  如需詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。|  
|公開受保護受保護-或-公用|成員是公用的在組件，但組件外部的受保護。|  
|私用受保護-或-受保護的私用|成員是在組件受到保護，但組件外部的私用。|  
  
 下列範例顯示公用類型有不同的存取範圍，以宣告的成員，並顯示從這些成員在組件的存取。  
  
```  
  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
   a->Protected_Public_Function();  
   a->Public_Protected_Function();  
  
   // accessible inside but not outside the assembly  
   a->Internal_Function();  
  
   // call protected functions  
   b->Test();  
  
   // not accessible inside or outside the assembly  
   // a->Private_Function();  
}  
```  
  
 **輸出**  
  
```Output  
in Public_Function  
in Protected_Public_Function  
in Public_Protected_Function  
in Internal_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Private_Function  
in Private_Protected_Function  
exiting function of derived class  
=======================  
```  
  
 現在讓我們來建置為 DLL 先前的範例。  
  
```  
  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
```  
  
 下列範例會使用建立在先前範例中，並藉此示範如何存取與組件外的之成員的元件。  
  
```  
  
// compile with: /clr  
#using "type_member_visibility_2.dll"  
using namespace System;  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Public_Function();  
      Public_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
  
   // call protected functions  
   b->Test();  
  
   // can't be called outside the assembly  
   // a->Private_Function();  
   // a->Internal_Function();     
   // a->Protected_Private_Function();  
   // a->Private_Protected_Function();  
}  
```  
  
 **輸出**  
  
```Output  
in Public_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Public_Function  
in Public_Protected_Function  
exiting function of derived class  
=======================  
```  
  
##  <a name="BKMK_Public_and_private_native_classes"></a> 公用和私用原生類別  
 您可以從 managed 型別參考原生類型。  比方說，managed 類型中的函式可以採用的參數，其類型是原生結構。  如果組件中的公用 managed 的類型和函式，然後原生型別也必須是公用。  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 接下來，建立會耗用原生類型的來源檔案：  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 現在，編譯用戶端：  
  
```  
  
// compile with: /clr  
#using "mcppv2_ref_class3.dll"  
  
#include "mcppv2_ref_class3.h"  
  
int main() {  
   R ^r = gcnew R;  
   N n;  
   r->f(n);  
}  
```  
  
##  <a name="BKMK_Static_constructors"></a> 靜態建構函式  
 CLR 型別，例如類別或結構，可以有可以用來初始化靜態資料成員的靜態建構函式。  靜態建構函式會呼叫一次，並會在第一次存取類型的任何靜態成員之前呼叫。  
  
 執行個體建構函式一定會執行靜態建構函式之後。  
  
 如果類別有靜態的建構函式，編譯器無法內嵌建構函式的呼叫。  如果類別是實值類型、 靜態建構函式，並且沒有執行個體建構函式，編譯器無法內嵌呼叫任何成員函式。  CLR 可能會內嵌呼叫，但編譯器無法。  
  
 定義靜態建構函式為私用成員函式，因為它用來只能由 CLR 呼叫。  
  
 如需靜態建構函式的詳細資訊，請參閱[如何： 定義介面靜態建構函式 (C + + /CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
private:  
   static int i = 0;  
  
   static MyClass() {  
      Console::WriteLine("in static constructor");  
      i = 9;  
   }  
  
public:  
   static void Test() {  
      i++;  
      Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass::Test();  
   MyClass::Test();  
}  
```  
  
 **輸出**  
  
```Output  
in static constructor  
10  
11  
```  
  
##  <a name="BKMK_Semantics_of_the_this_pointer"></a> 語意的 this 指標  
 當您使用 Visual c + + 來定義型別，`this`在參考類型的指標為型別 」 控制代碼 」。 `this`在實值類型的指標為 「 內部指標 」 類型。  
  
 這些不同的語意`this`指標可能會導致非預期的行為，當呼叫時的預設索引子。 下一個範例顯示正確的方式來存取在 ref 類型和實值類型的預設索引子。  
  
 如需詳細資訊，請參閱  
  
-   [物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref struct A {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
  
   A() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this[3.3]);  
   }  
};  
  
value struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
   void Test() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this->default[3.3]);  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```  
  
 **輸出**  
  
```Output  
10.89  
10.89  
```  
  
##  <a name="BKMK_Hide_by_signature_functions"></a> 依簽章隱藏型函式  
 標準 c + + 函式中的基底類別隱藏在衍生類別中，具有相同名稱的函式即使衍生類別函式沒有相同數目或類型的參數。 這指*隱藏依名稱*語意。 在參考類型，基底類別中的函式可以只會隱藏在衍生類別中的函式名稱和參數清單都相同。 這稱為*依簽章隱藏*語意。  
  
 類別會被視為依簽章隱藏類別，其函式全都會標示為做為中繼資料中時`hidebysig`。 根據預設，會建立在之下的所有類別 **/clr**有`hidebysig`函式。 當類別只有`hidebysig`函式，編譯器不會隱藏函式的任何直接基底類別中的名稱，但如果編譯器遇到隱藏依名稱中的類別繼承鏈結，它會繼續依名稱隱藏行為。  
  
 下依簽章隱藏語意，當呼叫函式物件，編譯器會識別最多衍生的類別，其中包含符合函式呼叫的函式。 如果無法滿足呼叫類別中只有一個函式，編譯器會呼叫此函式。 如果無法滿足呼叫類別中有一個以上的函式，編譯器會使用多載解析規則來判斷要呼叫的函式。 如需多載規則的詳細資訊，請參閱[函式多載](../cpp/function-overloading.md)。  
  
 針對指定的函式呼叫的基底類別中的函式可能使得稍微好一點的相符項目，比函式在衍生類別中的簽章。 不過，如果在衍生類別的物件上明確呼叫的函式，會呼叫衍生類別中的函式。  
  
 傳回值不會視為函式的簽章的一部分，因為基底類別函式隱藏如果它具有相同的名稱，並採用相同的數目和類型的引數為衍生類別函式，即使它與不同類型的傳回值。  
  
 下列範例會顯示在衍生類別中的函式並未隱藏基底類別中的函式。  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test() {   
      Console::WriteLine("Base::Test");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test(int i) {   
      Console::WriteLine("Derived::Test");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Test() in the base class will not be hidden  
   t->Test();  
}  
```  
  
 **輸出**  
  
```Output  
Base::Test  
```  
  
 下一個範例顯示 Visual c + + 編譯器，最多衍生類別中呼叫的函式 — 即使要比對一個或多個參數都必須轉換，並不是比較適合函式呼叫的基底類別中呼叫的函式。  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test2(Single d) {   
      Console::WriteLine("Base::Test2");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test2(Double f) {   
      Console::WriteLine("Derived::Test2");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Base::Test2 is a better match, but the compiler  
   // calls a function in the derived class if possible  
   t->Test2(3.14f);  
}  
```  
  
 **輸出**  
  
```Output  
Derived::Test2  
```  
  
 下列範例示範可以隱藏函式，即使基底類別衍生的類別相同的簽章。  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   int Test4() {   
      Console::WriteLine("Base::Test4");   
      return 9;   
   }  
};  
  
ref struct Derived : public Base {  
   char Test4() {   
      Console::WriteLine("Derived::Test4");   
      return 'a';   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
  
   // Base::Test4 is hidden  
   int i = t->Test4();  
   Console::WriteLine(i);  
}  
```  
  
 **輸出**  
  
```Output  
Derived::Test4  
97  
```  
  
##  <a name="BKMK_Copy_constructors"></a> 複製建構函式  
 C + + 標準所規定的複製建構函式稱為當移動物件時，使得物件會建立並終結在相同的位址。  
  
 不過，當 **/clr**是用來編譯並編譯為原生函式在原生類別的 MSIL 呼叫的函式 — 或多個 — 以傳值和原生類別之複製建構函式及/或解構函式，沒有複本建構函式呼叫，而且在不同的位址，比建立所在終結物件。 如果類別的指標至本身，或如果程式碼追蹤物件的位址，這可能會造成問題。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下列範例會示範時不會產生複製建構函式。  
  
```  
  
// compile with: /clr  
#include<stdio.h>  
  
struct S {  
   int i;  
   static int n;  
  
   S() : i(n++) {   
      printf_s("S object %d being constructed, this=%p\n", i, this);   
   }  
  
   S(S const& rhs) : i(n++) {   
      printf_s("S object %d being copy constructed from S object "  
               "%d, this=%p\n", i, rhs.i, this);   
   }  
  
   ~S() {  
      printf_s("S object %d being destroyed, this=%p\n", i, this);   
   }  
};  
  
int S::n = 0;  
  
#pragma managed(push,off)  
void f(S s1, S s2) {  
   printf_s("in function f\n");  
}  
#pragma managed(pop)  
  
int main() {  
   S s;  
   S t;  
   f(s,t);  
}  
```  
  
 **輸出**  
  
```Output  
S object 0 being constructed, this=0018F378  
S object 1 being constructed, this=0018F37C  
S object 2 being copy constructed from S object 1, this=0018F380  
S object 3 being copy constructed from S object 0, this=0018F384  
S object 4 being copy constructed from S object 2, this=0018F2E4  
S object 2 being destroyed, this=0018F380  
S object 5 being copy constructed from S object 3, this=0018F2E0  
S object 3 being destroyed, this=0018F384  
in function f  
S object 5 being destroyed, this=0018F2E0  
S object 4 being destroyed, this=0018F2E4  
S object 1 being destroyed, this=0018F37C  
S object 0 being destroyed, this=0018F378  
```  
  
##  <a name="BKMK_Destructors_and_finalizers"></a> 解構函式與完成項  
 在參考類型的解構函式執行決定性清除的資源。 完成項清除 unmanaged 資源，而且在記憶體回收行程的解構函式或被非確定性地決定性地呼叫。 標準 c + + 解構函式的相關資訊，請參閱[解構函式](../cpp/destructors-cpp.md)。  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 在受管理的 Visual c + + 類別的解構函式的行為不同從 Managed Extensions for c + +。 如需有關這項變更的詳細資訊，請參閱[解構函式語意變更](../dotnet/changes-in-destructor-semantics.md)。  
  
 CLR 記憶體回收行程刪除未使用的受管理的物件，並已不再需要時釋放其記憶體。 不過，類型可以使用記憶體回收行程不知道如何釋放資源。 這些資源稱為未受管理的資源 （原生檔案控制代碼，例如）。 我們建議您釋放完成項中的所有 unmanaged 的資源。 記憶體回收行程會被非確定性地釋放 managed 的資源，因為它並不安全是指在完成項中的 managed 資源可能因為記憶體回收行程的受管理資源已清除。  
  
 Visual c + + 完成項不是相同<xref:System.Object.Finalize%2A>方法。 (CLR 文件會使用完成項和<xref:System.Object.Finalize%2A>方法意義)。 <xref:System.Object.Finalize%2A>方法由記憶體回收行程，這會叫用每個類別的繼承鏈結中的完成項呼叫。 與不同的是 Visual c + + 解構函式，衍生類別完成項呼叫不會造成編譯器將叫用所有基底類別中的完成項。  
  
 由於 Visual c + + 編譯器支援決定性的資源釋放，請勿嘗試實作<xref:System.IDisposable.Dispose%2A>或<xref:System.Object.Finalize%2A>方法。 不過，如果您熟悉這些方法，以下是 Visual c + + 完成項和解構函式呼叫完成項的如何對應至<xref:System.IDisposable.Dispose%2A>模式：  
  
```  
// Visual C++ code  
ref class T {  
   ~T() { this->!T(); }   // destructor calls finalizer  
   !T() {}   // finalizer  
};  
  
// equivalent to the Dispose pattern  
void Dispose(bool disposing) {  
   if (disposing) {  
      ~T();  
   } else {  
      !T();  
   }  
}  
```  
  
 Managed 型別可能也會使用您想要釋放決定性的方式，並不會讓記憶體回收行程，在某個時間點之後不再需要物件時被非確定性地釋放 managed 的資源。 決定性的資源釋放可大幅提升效能。  
  
 Visual c + + 編譯器可讓物件決定性地清除解構函式的定義。 使用解構函式來釋出您想要確定的方式發行的所有資源。  如果有完成項，則會呼叫解構函式，以避免程式碼重複。  
  
```  
  
// compile with: /clr /c  
ref struct A {  
   // destructor cleans up all resources  
   ~A() {  
      // clean up code to release managed resource  
      // ...  
      // to avoid code duplication,   
      // call finalizer to release unmanaged resources  
      this->!A();  
   }  
  
   // finalizer cleans up unmanaged resources  
   // destructor or garbage collector will  
   // clean up managed resources  
   !A() {  
      // clean up code to release unmanaged resources  
      // ...  
   }  
};  
```  
  
 如果使用您的類型的程式碼不會呼叫解構函式，記憶體回收行程最終會釋放所有的 managed 的資源。  
  
 解構函式的存在並不表示完成項存在。 不過，出現的完成項暗示，您必須定義解構函式，並從該解構函式呼叫的完成項。 這提供決定性的 unmanaged 資源釋放。  
  
 呼叫解構函式會隱藏 — 使用<xref:System.GC.SuppressFinalize%2A>— 最終處理的物件。 如果未呼叫解構函式，最後會在記憶體回收行程呼叫類型的完成項。  
  
 決定性地清除物件的資源，藉由呼叫解構函式，可以改善效能與讓 CLR 被非確定性地完成物件相比較。  
  
 以 Visual c + + 撰寫並使用編譯的程式碼 **/clr**會執行類型的解構函式：  
  
-   使用堆疊語意建立的物件會超出範圍。 如需詳細資訊，請參閱[參考類型的 c + + 堆疊語意](../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
-   物件的建構期間擲回例外狀況。  
  
-   此物件為的物件的解構函式正在執行中的成員。  
  
-   您呼叫[刪除](../cpp/delete-operator-cpp.md)控點上的運算子 ([物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md))。  
  
-   您可以明確呼叫解構函式。  
  
 如果您的型別所耗用的另一個語言所撰寫的用戶端，解構函式呼叫，如下所示：  
  
-   在呼叫<xref:System.IDisposable.Dispose%2A>。  
  
-   在呼叫`Dispose(void)`類型上。  
  
-   如果類型超出範圍，在 C#`using`陳述式。  
  
 如果您建立參考類型的物件 （不使用堆疊語意的參考型別） 在 managed 堆積上，使用[再試一次最後](../cpp/try-finally-statement.md)語法以確認例外狀況不會防止解構函式的執行。  
  
```  
  
// compile with: /clr  
ref struct A {  
   ~A() {}  
};  
  
int main() {  
   A ^ MyA = gcnew A;  
   try {  
      // use MyA  
   }  
   finally {  
      delete MyA;  
   }  
}  
```  
  
 如果您的類型具有解構函式，編譯器會產生`Dispose`方法，可實作<xref:System.IDisposable>。 如果類型以 Visual c + + 撰寫，且具有耗用從另一種語言的解構函式，呼叫`IDisposable::Dispose`該類型會使要呼叫的解構函式的類型。 當類型從 Visual c + + 用戶端取用時，您便無法直接呼叫`Dispose`; 相反地，使用呼叫解構函式`delete`運算子。  
  
 如果您的類型具有完成項，則編譯器會產生`Finalize(void)`方法會覆寫<xref:System.Object.Finalize%2A>。  
  
 如果類型具有完成項或解構函式，編譯器會產生`Dispose(bool)`方法，根據設計模式。 (如需資訊，請參閱[Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern))。 您無法明確地撰寫或呼叫`Dispose(bool)`Visual c + + 中。  
  
 如果類型符合 「 設計 」 模式的基底類別，所有基底類別的解構函式會呼叫衍生類別的解構函式呼叫時。 （如果您的型別以 Visual c + + 撰寫，編譯器會確保您的型別實作此模式。）換句話說，參考類別的解構函式鏈結到其基底和 c + + 標準所指定的成員，該類別的解構函式是執行，則相反的順序，它們所建構中, 其成員的解構函式的第一個和最後相反的順序建構在其基底類別的解構函式。  
  
 實值類型或介面內不允許解構函式與完成項。  
  
 完成項只能定義或參考類型中宣告。 如同建構函式和解構函式中，完成項會有沒有傳回型別。  
  
 物件的完成項執行之後，任何基底類別中的完成項也稱為，開頭為至少衍生的型別。 資料成員的完成項不會自動鏈結到由類別的完成項。  
  
 如果完成項刪除原生指標的 managed 類型中，您必須確定，還是透過原生指標的參考不會提前收集;解構函式呼叫 managed 型別，而不是使用<xref:System.GC.KeepAlive%2A>。  
  
 在編譯時期，您可以偵測到的類型具有完成項或解構函式。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 下一個範例示範兩種類型的 unmanaged 的資源，一個具有 managed 決定性地釋放資源。  
  
```  
  
// compile with: /clr  
#include <vcclr.h>  
#include <stdio.h>  
using namespace System;  
using namespace System::IO;  
  
ref class SystemFileWriter {  
   FileStream ^ file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
public:  
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),   
                                     arr(gcnew array<Byte>(1024)) {}  
  
   void Flush() {  
      file->Write(arr, 0, bufLen);  
      bufLen = 0;  
   }  
  
   ~SystemFileWriter() {  
      Flush();  
      delete file;  
   }  
};  
  
ref class CRTFileWriter {  
   FILE * file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
   static FILE * getFile(String ^ n) {  
      pin_ptr<const wchar_t> name = PtrToStringChars(n);  
      FILE * ret = 0;  
      _wfopen_s(&ret, name, L"ab");  
      return ret;  
   }  
  
public:  
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}  
  
   void Flush() {  
      pin_ptr<Byte> buf = &arr[0];  
      fwrite(buf, 1, bufLen, file);  
      bufLen = 0;  
   }  
  
   ~CRTFileWriter() {  
      this->!CRTFileWriter();  
   }  
  
   !CRTFileWriter() {  
      Flush();  
      fclose(file);  
   }  
};  
  
int main() {  
   SystemFileWriter w("systest.txt");  
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)   
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)