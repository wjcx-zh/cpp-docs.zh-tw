---
title: 如何：定義與使用類別和結構 (C++/CLI)
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418290"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定義與使用類別和結構 (C++/CLI)

本文說明如何在/Cli 中C++定義和使用使用者定義的參考型別和實數值型別。

##  <a name="BKMK_Contents"></a> Contents

[物件具現化](#BKMK_Object_instantiation)

[隱含抽象類別](#BKMK_Implicitly_abstract_classes)

[類型可見度](#BKMK_Type_visibility)

[成員可見度](#BKMK_Member_visibility)

[公用和私用原生類別](#BKMK_Public_and_private_native_classes)

[靜態建構函式](#BKMK_Static_constructors)

[This 指標的語義](#BKMK_Semantics_of_the_this_pointer)

[逐特徵隱藏函式](#BKMK_Hide_by_signature_functions)

[複製建構函式](#BKMK_Copy_constructors)

[析構函數和完成項](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a>物件具現化

Reference （ref）型別只能在 managed 堆積上具現化，而不是在堆疊上或原生堆積上。 實值型別可以在堆疊或 managed 堆積上具現化。

```cpp
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

##  <a name="BKMK_Implicitly_abstract_classes"></a>隱含抽象類別

*隱含抽象類別*無法具現化。 如果類別的基底類型是介面，而且類別不會實作用介面的所有成員函式，則類別會隱含抽象化。

如果您無法從衍生自介面的類別來建立物件，原因可能是類別是隱含抽象的。 如需抽象類別的詳細資訊，請參閱[abstract](../extensions/abstract-cpp-component-extensions.md)。

下列程式碼範例會示範無法將 `MyClass` 類別具現化，因為函式 `MyClass::func2` 不會實作為函式。 若要讓範例進行編譯，請取消批註 `MyClass::func2`。

```cpp
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

##  <a name="BKMK_Type_visibility"></a>類型可見度

您可以控制 common language runtime （CLR）型別的可見度，以便在參考元件時，元件中的型別可以是可見的，或是在元件外部看不到的類型。

`public` 表示包含型別之元件的 `#using` 指示詞的任何原始程式檔都可以看到某個型別。  `private` 表示包含型別之元件 `#using` 指示詞的原始程式檔中，看不到型別。 不過，您可以在相同的元件中看到私用類型。 根據預設，會 `private`類別的可見度。

根據預設，在 Visual Studio 2005 之前，原生類型具有元件外部的公用存取範圍。 啟用[編譯器警告（層級1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) ，以協助您瞭解私用原生類型的使用不正確的位置。 您可以使用[make_public](../preprocessor/make-public.md) pragma，在無法修改的原始程式碼檔中提供原生類型的公用存取範圍。

如需詳細資訊，請參閱 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。

下列範例顯示如何宣告型別並指定其存取範圍，然後在元件記憶體取這些型別。 當然，如果使用 `#using`來參考具有私用類型的元件，則只會顯示元件中的公用類型。

```cpp
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

現在，讓我們重寫先前的範例，使其建立為 DLL。

```cpp
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

下一個範例顯示如何存取元件外部的類型。 在此範例中，用戶端會使用上一個範例中所建立的元件。

```cpp
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

##  <a name="BKMK_Member_visibility"></a>成員可見度

您可以使用 `public`、`protected`和 `private` 的存取規範配對，從相同的元件記憶體取公用類別的成員，而不是從元件外部存取。

下表摘要說明各種存取規範的效果：

|規範|效果|
|---------------|------------|
|public|成員可在元件內部和外部存取。  如需詳細資訊，請參閱[public](../cpp/public-cpp.md) 。|
|private|成員無法存取，不在元件內部或外部。  如需詳細資訊，請參閱[私](../cpp/private-cpp.md)用。|
|受保護的 - protected|成員可在元件內部和外部存取，但僅限於衍生的類型。  如需詳細資訊，請參閱[protected](../cpp/protected-cpp.md) 。|
|內部|成員在元件內是公用的，但在元件外部是私用的。  `internal` 是即時線上關鍵字。  如需詳細資訊，請參閱[即時線上關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。|
|公開保護或受保護的公用|成員在元件內是公用的，但在元件外部受到保護。|
|私用保護或受保護的私用|成員會在元件內部受到保護，但在元件外部是私用的。|

下列範例顯示的公用型別具有以不同存取性宣告的成員，然後顯示從元件內部存取這些成員的方式。

```cpp
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

現在讓我們將先前的範例建立為 DLL。

```cpp
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

下列範例會使用先前範例中所建立的元件，因此會顯示如何從元件外部存取成員。

```cpp
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

##  <a name="BKMK_Public_and_private_native_classes"></a>公用和私用原生類別

您可以從 managed 型別參考原生型別。  例如，managed 類型中的函式可以接受其類型為原生結構的參數。  如果 managed 類型和函式在元件中是公用的，則原生類型也必須是公用的。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

接下來，建立會使用原生類型的原始程式碼檔：

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

現在，請編譯用戶端：

```cpp
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

CLR 型別（例如，類別或結構）可以有一個可以用來初始化靜態資料成員的靜態函數。  靜態的函式最多隻會呼叫一次，而且會在第一次存取類型的任何靜態成員之前呼叫。

實例的函式一律會在靜態的函數之後執行。

如果類別具有靜態的函式，編譯器就無法將呼叫內嵌至函式。  如果類別是實值型別、具有靜態的函式，而且沒有實例的「函數」，則編譯器無法將呼叫內嵌至任何成員函式。  CLR 可以內嵌呼叫，但編譯器無法。

將靜態的函式定義為私用成員函式，因為它只能由 CLR 呼叫。

如需靜態函式的詳細資訊，請參閱[如何：定義介面靜態函數C++（/cli）](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。

```cpp
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

##  <a name="BKMK_Semantics_of_the_this_pointer"></a>This 指標的語義

當您使用視覺效果C++來定義型別時，參考型別中的 `this` 指標是「控制碼」類型。 實值型別中的 `this` 指標是「內部指標」類型。

呼叫預設的索引子時，`this` 指標的這些不同的語義可能會導致非預期的行為。 下一個範例顯示在 ref 型別和實值型別中存取預設索引子的正確方式。

如需詳細資訊，請參閱

- [物件控制代碼運算子 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
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

##  <a name="BKMK_Hide_by_signature_functions"></a>逐特徵隱藏函式

在 standard C++中，基類中的函式會由在衍生類別中具有相同名稱的函式隱藏，即使衍生類別函數的參數數目或種類不相同也一樣。 這稱為「*隱藏名稱*」的語義。 在參考型別中，如果名稱和參數清單都相同，則基類中的函數只能由衍生類別中的函式隱藏。 這就是所謂的*隱藏式*簽章的語義。

當類別的所有函式都在中繼資料中標記為 `hidebysig`時，會將其視為隱藏簽章類別。 根據預設，在 **/clr**底下建立的所有類別都有 `hidebysig` 函數。 當類別具有 `hidebysig` 函式時，編譯器不會依名稱在任何直接基類中隱藏函式，但如果編譯器在繼承鏈中遇到隱藏名稱的類別，它會繼續該程式的隱藏名稱行為。

在隱藏簽章的語義之下，當在物件上呼叫函式時，編譯器會識別包含可滿足函式呼叫之函式的最衍生類別。 如果類別中只有一個可滿足呼叫的函式，則編譯器會呼叫該函式。 如果類別中有一個以上的函式可以滿足呼叫，編譯器會使用多載解析規則來判斷要呼叫的函式。 如需多載規則的詳細資訊，請參閱[函數](../cpp/function-overloading.md)多載。

針對指定的函式呼叫，基類中的函式可能會有簽章，使其比衍生類別中的函式更符合。 不過，如果函式是在衍生類別的物件上明確呼叫，則會呼叫衍生類別中的函數。

由於傳回值不會被視為函式簽章的一部分，因此如果基類函式具有相同的名稱，並採用與衍生類別函式相同的引數數目和種類，即使它在傳回值的類型不同時，也會隱藏該函數。

下列範例顯示，衍生類別中的函式不會隱藏基類中的函數。

```cpp
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

下一個範例顯示，即使轉換C++必須符合一個或多個參數，Microsoft 編譯器還是會呼叫最常衍生類別中的函式，而不是在基類中呼叫與函式呼叫較佳相符的函式。

```cpp
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

下列範例顯示即使基類與衍生類別具有相同的簽章，也可以隱藏函式。

```cpp
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

##  <a name="BKMK_Copy_constructors"></a>複製構造函式

C++標準表示當物件移動時，會呼叫複製的函式，因此會在相同位址建立和終結物件。

不過，當使用 **/clr**進行編譯時，如果編譯為 MSIL 的函式呼叫原生函式，而原生類別（或多個）是以傳值方式傳遞，而原生類別具有複製的函數和/或析構函式，則不會呼叫任何複製程式，而且會在與建立該物件不同的位址上終結該物件。 如果類別有指向本身的指標，或如果程式碼依位址追蹤物件，這可能會造成問題。

如需詳細資訊，請參閱 [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)。

下列範例會示範何時不會產生複製的函式。

```cpp
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

##  <a name="BKMK_Destructors_and_finalizers"></a>析構函數和完成項

參考型別中的析構函數會執行具決定性的資源清除。 完成項會清除非受控資源，並可由析構函式以決定性的方式呼叫，或由垃圾收集行程非確定性地。 如需有關標準C++中的析構函數的詳細資訊，請參閱[析構函數](../cpp/destructors-cpp.md)。

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Managed 視覺效果C++類別中的析構函數行為與的 managed 擴充功能C++不同。 如需這項變更的詳細資訊，請參閱[析構函式語義的變更](../dotnet/changes-in-destructor-semantics.md)。

CLR 垃圾收集行程會刪除未使用的 managed 物件，並在不再需要時釋放其記憶體。 不過，型別可能會使用垃圾收集行程不知道如何釋放的資源。 這些資源稱為非受控資源（例如原生檔案控制代碼）。 我們建議您釋放完成項中的所有非受控資源。 由於受控資源是由垃圾收集行程所非確定性地，因此在完成項中參考 managed 資源並不安全，因為可能是垃圾收集行程已經清除該受控資源。

Visual C++完成項與 <xref:System.Object.Finalize%2A> 方法不同。 （CLR 檔使用完成項和 <xref:System.Object.Finalize%2A> 方法同義）。 <xref:System.Object.Finalize%2A> 方法是由垃圾收集行程所呼叫，它會叫用類別繼承鏈中的每個完成項。 不同于C++ Visual 析構函數，衍生類別的完成項呼叫不會使編譯器在所有基類中叫用完成項。

因為 Microsoft C++編譯器支援決定性的資源發行，所以請勿嘗試執行 <xref:System.IDisposable.Dispose%2A> 或 <xref:System.Object.Finalize%2A> 方法。 不過，如果您熟悉這些方法，以下是 Visual C++ finalizer 和呼叫完成項的析構函式如何對應至 <xref:System.IDisposable.Dispose%2A> 模式：

```cpp
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

Managed 類型也可以使用您想要以決定性方式發行的 managed 資源，而不是在不再需要物件之後，讓垃圾收集行程在某個時間點釋放非確定性地。 具決定性的資源發行可以大幅提升效能。

Microsoft C++編譯器會啟用析構函式的定義，以決定性地清除物件。 使用此析構函式來釋放您想要以決定性方式釋放的所有資源。  如果有完成項，請從析構函式呼叫它，以避免程式碼重複。

```cpp
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

如果使用您的型別的程式碼不會呼叫此函式，垃圾收集行程最後會釋放所有 managed 資源。

出現的析構函數並不表示完成項的存在。 不過，完成項的存在表示您必須定義一個析構函式，並從該析構函式呼叫完成項。 這可提供具決定性的非受控資源版本。

呼叫析構函式會隱藏，方法是使用 <xref:System.GC.SuppressFinalize%2A>-結束物件。 如果未呼叫此函式，則垃圾收集行程最後會呼叫您的類型完成項。

藉由呼叫析構函式來確定清除物件的資源，可以改善效能，相較于讓 CLR 非確定性地完成物件。

以 Visual C++撰寫並使用 **/clr**編譯的程式碼，會在下列情況執行類型的析構函式：

- 使用堆疊語義所建立的物件超出範圍。 如需詳細資訊，請參閱[ C++參考型別的堆疊語義](../dotnet/cpp-stack-semantics-for-reference-types.md)。

- 在物件的結構中，會擲回例外狀況。

- 物件是物件中的成員，其析構函式正在執行。

- 您在控制碼上呼叫[delete](../cpp/delete-operator-cpp.md)運算子（[物件運算子的控制碼（^）](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)）。

- 您會明確地呼叫此函式。

如果您的型別是由以另一種語言撰寫的用戶端所使用，則會呼叫此函式，如下所示：

- 呼叫 <xref:System.IDisposable.Dispose%2A>。

- 呼叫類型上的 `Dispose(void)`。

- 如果類型超出C# `using` 語句的範圍。

如果您在 managed 堆積上建立參考型別的物件（不使用參考型別的堆疊語義），請使用[try-catch](../cpp/try-finally-statement.md)語法來確保例外狀況不會阻止執行析構函式。

```cpp
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

如果您的型別具有「析構函式」，則編譯器會產生可執行 <xref:System.IDisposable>的 `Dispose` 方法。 如果以 Visual C++撰寫的型別具有從另一個語言取用的析構函式，則在該型別上呼叫 `IDisposable::Dispose` 會導致呼叫型別的析構函式。 從 Visual C++ client 取用型別時，您無法直接呼叫 `Dispose`;相反地，請使用 `delete` 運算子來呼叫析構函式。

如果您的型別具有完成項，編譯器會產生覆寫 <xref:System.Object.Finalize%2A>的 `Finalize(void)` 方法。

如果類型具有完成項或析構函式，編譯器會根據設計模式來產生 `Dispose(bool)` 方法。 （如需詳細資訊，請參閱[處置模式](/dotnet/standard/design-guidelines/dispose-pattern)）。 您無法在視覺效果C++中明確地撰寫或呼叫 `Dispose(bool)`。

如果類型具有符合設計模式的基類，則會在呼叫衍生類別的析構函式時呼叫所有基類的析構函數。 （如果您的類型是以 Visual C++撰寫，則編譯器會確保您的類型會執行此模式）。換句話說，參考類別的析構函式會連結至其基底和成員（如C++標準所指定），首先會執行類別的「析構函式」，然後以它們的結構順序反轉其成員的析構函數，最後再以其結構化的順序反轉其基類的析構函數。

在實數值型別或介面中不允許有析構函數和完成項。

完成項只能在參考型別中定義或宣告。 如同函式和析構函數，完成項沒有傳回型別。

在物件的完成項執行之後，也會呼叫任何基類中的處理常式，並從最小的衍生類型開始。 資料成員的完成項不會由類別的完成項自動連結到。

如果完成項刪除 managed 類型中的原生指標，您必須確定原生指標的參考不會提早被收集;呼叫 managed 類型上的析構函式，而不是使用 <xref:System.GC.KeepAlive%2A>。

在編譯時期，您可以偵測類型是否有完成項或析構函式。 如需詳細資訊，請參閱[型別特性的編譯器支援](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

下一個範例會顯示兩個類型，其中一個具有未受管理的資源，另一個則具有決定性釋放的 managed 資源。

```cpp
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

[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)
