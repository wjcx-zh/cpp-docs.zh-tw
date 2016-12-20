---
title: "如何︰ 定義和使用類別和結構 (c + + CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "結構 [C++]"
  - "類別 [C++]，執行個體化"
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定義與使用類別和結構 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將說明如何定義及使用使用者定義的參考型別和實值型別 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]。  
  
##  <a name="a-namebkmkcontentsa-contents"></a><a name="BKMK_Contents"></a> 內容  
 [物件具現化](#BKMK_Object_instantiation)  
  
 [隱含抽象類別](#BKMK_Implicitly_abstract_classes)  
  
 [型別可視性](#BKMK_Type_visibility)  
  
 [成員可視性](#BKMK_Member_visibility)  
  
 [公用和私用原生類別](#BKMK_Public_and_private_native_classes)  
  
 [靜態建構函式](#BKMK_Static_constructors)  
  
 [語意 （semantics) 之 this 指標](#BKMK_Semantics_of_the_this_pointer)  
  
 [依簽章隱藏型函式](#BKMK_Hide_by_signature_functions)  
  
 [複製建構函式](#BKMK_Copy_constructors)  
  
 [解構函式和完成項](#BKMK_Destructors_and_finalizers)  
  
##  <a name="a-namebkmkobjectinstantiationa-object-instantiation"></a><a name="BKMK_Object_instantiation"></a> 物件具現化  
 參考 (ref) 型別和實值型別可以只具現化 managed 堆積上不是在堆疊或原生堆積上。  
  
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
  
##  <a name="a-namebkmkimplicitlyabstractclassesa-implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> 隱含抽象類別  
  *隱含抽象類別* 無法具現化。 如果類別的基底型別是介面和類別沒有實作介面的成員函式的所有類別都是隱含抽象。  
  
 如果您無法建構類別衍生自介面的物件，原因可能是隱含抽象類別。 如需抽象類別的詳細資訊，請參閱 [抽象](../windows/abstract-cpp-component-extensions.md)。  
  
 下列程式碼範例會示範， `MyClass` 因為類別無法具現化函式 `MyClass::func2` 未實作。 要編譯範例，請取消註解 `MyClass::func2`。  
  
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
  
##  <a name="a-namebkmktypevisibilitya-type-visibility"></a><a name="BKMK_Type_visibility"></a> 型別可視性  
 以便參考組件時，如果組件中的型別可以是可見或不可見組件之外，您可以控制可見性的 common language runtime (CLR) 型別。  
  
 `public` 表示型別都可以看到任何原始程式檔，其中包含 `#using` 指示詞包含類型的組件。  `private` 表示型別不會看見包含的原始程式檔 `#using` 指示詞包含類型的組件。 然而，私用型別是在相同的組件內為可見。 根據預設，類別的可見性是 `private`。  
  
 根據預設，Visual c + + 2005年之前，原生型別必須在組件外部的公用存取範圍。 啟用 [編譯器警告 （層級 1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) 來協助您了解私用原生型別未正確使用。 使用 [make_public](../preprocessor/make-public.md) pragma 在原始程式碼檔案，您無法修改的原生型別提供公用存取範圍。  
  
 如需詳細資訊，請參閱 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。  
  
 下列範例示範如何宣告型別並指定其存取範圍，然後存取這些組件內的型別。 當然，如果具有私用類型的組件使用參考 `#using`, ，只有公用型別組件中的會顯示。  
  
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
  
 現在，讓我們重新撰寫先前的範例，以便建置而成的 DLL。  
  
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
  
 接下來的範例示範如何存取組件之外的型別。 在此範例中，用戶端會使用內建於前一個範例的元件。  
  
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
  
##  <a name="a-namebkmkmembervisibilitya-member-visibility"></a><a name="BKMK_Member_visibility"></a> 成員可視性  
 您可以對存取相同組件中的公用類別的成員不同存取，從組件外部使用的存取規範組 `public`, ，`protected`, ，並 `private`  
  
 這個表格摘要說明各種不同的存取規範的效果︰  
  
|指定名稱|作用|  
|---------------|------------|  
|public|成員可存取的內部與外部組件。  請參閱 [公用](../cpp/public-cpp.md) 如需詳細資訊。|  
|private|無法存取，在內部或外部組件都不成員。  請參閱 [私人](../cpp/private-cpp.md) 如需詳細資訊。|  
|protected|存取內部和外部組件，但僅限於衍生型別成員。  請參閱 [保護](../cpp/protected-cpp.md) 如需詳細資訊。|  
|internal|成員是公用組件內，但組件外部的私用。  `internal` 是即時線上關鍵字。  如需詳細資訊，請參閱 [即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。|  
|公開受保護受保護-或-公用|成員是公用組件內，但組件外部的受保護。|  
|私用受保護受保護-或-私用|成員是在組件受到保護，但組件外部的私用。|  
  
 下列範例顯示具有不同的存取範圍，以宣告的成員的公用型別，並顯示 [從組件內的這些成員的存取。  
  
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
  
 現在我們就來建置成 DLL 先前的範例。  
  
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
  
 下列範例使用的元件，會建立在先前範例中，並藉此示範如何存取外部組件中的成員。  
  
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
  
##  <a name="a-namebkmkpublicandprivatenativeclassesa-public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> 公用和私用原生類別  
 原生型別可以從 managed 型別參考。  比方說，managed 類型中的函式可以採用型別是原生結構的參數。  如果公用組件中的 managed 型別和函式，然後原生型別也必須公開。  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 接下來，建立原始程式碼檔使用原生型別︰  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 現在，編譯用戶端︰  
  
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
  
##  <a name="a-namebkmkstaticconstructorsa-static-constructors"></a><a name="BKMK_Static_constructors"></a> 靜態建構函式  
 CLR 型別，例如類別或結構，可以有可以用來初始化靜態資料成員的靜態建構函式。  靜態建構函式是最多一次，而且第一次存取型別的任何靜態成員之前呼叫。  
  
 執行個體建構函式一律會執行靜態建構函式之後。  
  
 如果類別的靜態建構函式，編譯器無法內嵌的建構函式的呼叫。  如果類別是實值型別、 靜態建構函式，並且不需要的執行個體建構函式，編譯器無法內嵌的任何成員函式呼叫。  CLR 可能內嵌呼叫，但編譯器不能。  
  
 定義靜態建構函式為私用成員函式，因為它只能由 CLR 呼叫。  
  
 如需靜態建構函式的詳細資訊，請參閱 [How to︰ 定義介面靜態建構函式 (C + + /cli CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。  
  
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
  
##  <a name="a-namebkmksemanticsofthethispointera-semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a> 語意 （semantics) 之 this 指標  
 當您使用 Visual c + + 來定義型別， `this` 在參考類型的指標是型別 「 控制代碼 」。  `this` 在實值類型的指標為內部指標 」。  
  
 這些不同的語意 `this` 指標可能會造成非預期的行為，當預設索引子會呼叫。 下一個範例是正確的方式來存取參考型別和實值型別中的預設索引子。  
  
 如需詳細資訊，請參閱  
  
-   [物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [如何︰ 使用索引的屬性](../misc/how-to-use-indexed-properties.md)  
  
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
  
##  <a name="a-namebkmkhidebysignaturefunctionsa-hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> 依簽章隱藏型函式  
 標準 c + + 中，基底類別的函式會隱藏由衍生類別中具有相同名稱的函式，即使該衍生類別函式並沒有相同數目或類型的參數。 這指 *隱藏依名稱* 語意 （semantics)。 在參考類型中，基底類別的函式可以只會隱藏在衍生類別中的函式如果的名稱和參數清單相同。 這稱為 *依簽章隱藏* 語意 （semantics)。  
  
 類別會被視為依簽章隱藏類別，其所有功能都標示為做為中繼資料中時 `hidebysig`。 根據預設，所有的類別下建立 **/clr** 有 `hidebysig` 函式。 不過，使用編譯的類別 **/clr:oldSyntax** 沒有 `hidebysig` 函式，而是依名稱隱藏函式。 當類別必須 `hidebysig` 函式，編譯器不會依名稱的任何直接基底類別隱藏函式，但如果編譯器遇到隱藏依名稱中的類別繼承鏈結，它會繼續該隱藏依名稱的行為。  
  
 底下依簽章隱藏語意，當呼叫函式物件，編譯器會識別最具衍生性的類別，其中包含符合函式呼叫的函式。 如果無法滿足呼叫類別中只有一個函式，則編譯器會呼叫該函式。 如果無法滿足呼叫類別中有多個函式，編譯器會使用多載解析規則來決定要呼叫的函式。 如需多載規則的詳細資訊，請參閱 [函式多載](../cpp/function-overloading.md)。  
  
 對於特定的函式呼叫基底類別的函式必須讓它稍微好一點的相符項目，比函式在衍生類別中的簽章。 不過，如果衍生類別的物件上明確呼叫函式，會呼叫衍生類別中的函式。  
  
 傳回值不是函式的簽章的一部分，因為基底類別函式隱藏如果具有相同的名稱，並採用相同的數目和類型的引數為衍生類別函式，即使仍有不同的傳回值的型別。  
  
 下列範例顯示由衍生類別中的函式不會隱藏基底類別的函式。  
  
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
  
 接下來的範例將示範 Visual c + + 編譯器呼叫的函式，最多衍生類別中 — 即使要比對一個或多個參數都必須轉換，並不是比較適合函式呼叫基底類別中呼叫的函式。  
  
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
  
 下列範例會定義元件會使用編譯的 **/clr:oldSyntax**。 使用 Managed Extensions for c + + 所定義的類別有依名稱隱藏成員函式。  
  
```  
  
// compile with: /clr:oldSyntax /LD  
using namespace System;  
public __gc struct Base0 {  
   void Test() {   
      Console::WriteLine("in Base0::Test");  
   }  
};  
  
public __gc struct Base1 : public Base0 {  
   void Test(int i) {   
      Console::WriteLine("in Base1::Test");  
   }  
};  
```  
  
 接下來的範例會使用內建於前一個範例的元件。 請注意如何根據簽章隱藏型功能不會套用至基底類別的型別會使用編譯的 **/clr:oldSyntax**。  
  
```  
  
// compile with: /clr:oldSyntax /LD  
// compile with: /clr  
using namespace System;  
#using "hide_by_signature_4.dll"  
  
ref struct Derived : public Base1 {  
   void Test(int i, int j) {   
      Console::WriteLine("Derived::Test");  
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   t->Test(8, 8);   // OK  
   t->Test(8);   // OK  
   t->Test();   // C2661  
}  
```  
  
##  <a name="a-namebkmkcopyconstructorsa-copy-constructors"></a><a name="BKMK_Copy_constructors"></a> 複製建構函式  
 C + + 標準所規定的複製建構函式稱為時移動物件，使物件建立和摧毀在相同的位址。  
  
 不過，當 **/clr** 是用來編譯並編譯為 MSIL 呼叫原生函式在原生類別的函式，或多個 — 傳遞值和其中原生類別具有複製建構函式和 （或） 解構函式、 沒有複製建構函式呼叫以及在不同於建立所在位址終結物件。 如果類別的指標至本身，或如果程式碼追蹤物件的位址，這可能會造成問題。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
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
  
##  <a name="a-namebkmkdestructorsandfinalizersa-destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> 解構函式和完成項  
 在參考類型的解構函式執行具決定性清除的資源。 完成項清除 unmanaged 資源，且解構函式或非確定性地記憶體回收行程可以以決定性的方式呼叫。 標準 c + + 解構函式的相關資訊，請參閱 [解構函式](../cpp/destructors-cpp.md)。  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 在受管理的 Visual c + + 類別的解構函式的行為不同從 Managed Extensions for c + +。 如需有關這項變更的詳細資訊，請參閱 [解構函式語意的變更](../dotnet/changes-in-destructor-semantics.md)。  
  
 CLR 記憶體回收行程刪除未使用受管理的物件，並已不再需要時釋放其記憶體。 不過，型別可能會使用記憶體回收行程不知道如何釋放資源。 這些資源稱為未受管理的資源 （原生檔案控制代碼，例如）。 我們建議您釋放完成項中的所有 unmanaged 的資源。 非確定性地釋放 managed 的資源的記憶體回收行程，因為它並不安全，請參閱受管理資源在完成項中很可能因為記憶體回收行程的受管理資源已清除。  
  
 Visual c + + 完成項不是相同 <xref:System.Object.Finalize%2A> 方法。 (CLR 文件會使用完成項和 <xref:System.Object.Finalize%2A> 方法 synonymously)。  <xref:System.Object.Finalize%2A> 方法由記憶體回收行程會叫用類別繼承鏈結中的每個完成項呼叫。 不同於 Visual c + + 解構函式，衍生類別完成項呼叫不會造成編譯器叫用所有基底類別中的完成項。  
  
 因為 Visual c + + 編譯器支援決定性的資源釋放，所以請勿嘗試實作 <xref:System.IDisposable.Dispose%2A> 或 <xref:System.Object.Finalize%2A> 方法。 不過，如果您已熟悉這些方法，以下是如何 Visual c + + 的完成設定式和解構函式呼叫完成項對應至 <xref:System.IDisposable.Dispose%2A> 模式︰  
  
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
  
 Managed 型別也可以使用您想要以決定性的方式，請釋放，並不會讓記憶體回收行程，在某個時間點之後不再需要物件時被非確定性地釋放 managed 的資源。 決定性的資源釋放可大幅提升效能。  
  
 Visual c + + 編譯器可讓您以決定性地清除物件的解構函式的定義。 使用解構函式來釋出您想要以決定性的方式釋放的所有資源。  如果完成項，則會呼叫解構函式，以避免程式碼重複。  
  
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
  
 如果使用您的類型的程式碼不會呼叫解構函式，記憶體回收行程最後釋放受管理的所有資源。  
  
 解構函式的存在並不表示完成項存在。 不過，完成項的存在意味著您必須定義解構函式，並從該解構函式呼叫完成項。 這會提供決定性的 unmanaged 資源釋放。  
  
 呼叫解構函式會隱藏 — 使用 <xref:System.GC.SuppressFinalize%2A>— 最終處理的物件。 如果未呼叫解構函式，終究會由記憶體回收行程呼叫型別的完成項。  
  
 決定性地清除物件的資源，藉由呼叫解構函式，可以改善效能相較於讓 CLR 被非確定性地結束該物件。  
  
 以 Visual c + + 撰寫並使用編譯的程式碼 **/clr** 時執行類型的解構函式︰  
  
-   使用堆疊語意建立的物件會超出範圍。 如需詳細資訊，請參閱 [參考類型的 c + + 堆疊語意](../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
-   物件的建構期間擲回例外狀況。  
  
-   此物件為的物件的解構函式正在執行中的成員。  
  
-   您呼叫 [刪除](../cpp/delete-operator-cpp.md) 控點上的運算子 ([物件控制代碼運算子 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md))。  
  
-   您可以明確呼叫解構函式。  
  
 如果您的型別以另一種語言撰寫的用戶端所使用，解構函式呼叫，如下所示︰  
  
-   在呼叫 <xref:System.IDisposable.Dispose%2A>。  
  
-   在呼叫 `Dispose(void)` 型別。  
  
-   如果類型超出範圍，在 C# `using` 陳述式。  
  
 如果您建立參考型別的物件 （不使用堆疊語意的參考型別） 在 managed 堆積上，使用 [試最後](../cpp/try-finally-statement.md) 語法，以確保例外狀況不會防止解構函式的執行。  
  
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
  
 如果您的型別具有解構函式，編譯器會產生 `Dispose` 方法實作 <xref:System.IDisposable>。 如果以 Visual c + + 撰寫，而且已使用另一種語言的解構函式的型別，則呼叫 `IDisposable::Dispose` 該型別上會導致要呼叫的解構函式的型別。 型別從 Visual c + + 用戶端取用，當您無法直接呼叫 `Dispose`; 相反地，呼叫解構函式使用 `delete` 運算子。  
  
 如果您的型別具有完成項，則編譯器會產生 `Finalize(void)` 方法會覆寫 <xref:System.Object.Finalize%2A>。  
  
 如果型別具有完成項或解構函式，編譯器會產生 `Dispose(bool)` 方法，根據設計模式。 (如需資訊，請參閱 [處置模式](../Topic/Dispose%20Pattern.md))。 您無法明確地撰寫或呼叫 `Dispose(bool)` Visual c + +。  
  
 如果型別符合設計模式的基底類別，所有基底類別的解構函式會呼叫衍生類別的解構函式呼叫時。 （如果您的型別以 Visual c + + 撰寫，編譯器會確保您的型別實作此模式。）換句話說，參考類別的解構函式鏈結到其基底和 c + + 標準所指定的成員，該類別的解構函式會執行，則其成員的順序中的使用者所建構，相反的解構函式的第一個和最後的相反順序建構在其基底類別的解構函式。  
  
 實值型別或介面內不允許解構函式和完成項。  
  
 完成項可以只定義或參考型別宣告。 如同建構函式和解構函式中，完成項會有任何傳回型別。  
  
 物件的完成項執行之後，任何基底類別中的完成項也會呼叫，開頭為最低的衍生型別。 資料成員的完成項是不會自動鏈結至由類別的完成項。  
  
 如果完成項刪除原生指標在 managed 類型中的，您必須確定，或是透過原生指標的參考不會過早收集。解構函式，呼叫受管理的型別，而不是使用 <xref:System.GC.KeepAlive%2A>。  
  
 在編譯時期，您可以偵測型別具有完成項或解構函式。 如需詳細資訊，請參閱 [類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 接下來的範例將示範兩種類型的 unmanaged 的資源，將具有 managed 資源，以決定性的方式發行。  
  
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