---
title: 如何：定義與使用類別和結構 (C++/CLI)
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5bec92ce2bd97f11723cdf59c58b7331b39565f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370188"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定義與使用類別和結構 (C++/CLI)

本文演示如何在C++/CLI中定義和使用使用者定義的引用類型和值類型。

## <a name="contents"></a><a name="BKMK_Contents"></a>內容

[物件實例化](#BKMK_Object_instantiation)

[隱含抽象類別](#BKMK_Implicitly_abstract_classes)

[類型可見度](#BKMK_Type_visibility)

[成員可見度](#BKMK_Member_visibility)

[公共和私有本機類](#BKMK_Public_and_private_native_classes)

[靜態建構函數](#BKMK_Static_constructors)

[此指標的語義](#BKMK_Semantics_of_the_this_pointer)

[按簽署隱藏功能](#BKMK_Hide_by_signature_functions)

[複製建構函式](#BKMK_Copy_constructors)

[析構函數和終結器](#BKMK_Destructors_and_finalizers)

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a>物件實例化

引用(ref) 類型只能在託管堆上實例化,只能在堆疊上或本機堆上實例化。 值類型可以在堆疊或託管堆上實例化。

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a>隱含抽象類別

無法執行式*隱含抽象類別*。 如果類的基類型是介面,並且類未實現介面的所有成員函數,則類是隱式抽象的。

如果無法從從介面派生的類構造物件,原因可能是該類是隱式抽象的。 有關抽象類的詳細資訊,請參閱[抽象](../extensions/abstract-cpp-component-extensions.md)。

以下代碼示例演示了由於函數`MyClass``MyClass::func2`未實現而無法實例化類。 要讓範例編譯,請取消註解`MyClass::func2`。

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a>類型可見度

您可以控制通用語言執行時 (CLR) 類型的可見性,以便在引用程式集時,程式集中的類型可以在程式集外部可見或不可見。

`public`指示類型對包含該類型的程式集的`#using`指令的任何源檔都可見。  `private`指示類型對於包含該類型的程式集的`#using`指令的源檔不可見。 但是,私有類型在同一程式集中可見。 預設情況下,類的可見性為`private`。

默認情況下,在 Visual Studio 2005 之前,本機類型具有程式集外部的公共可存取性。 啟用[編譯器警告(級別 1) C4692,](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)以説明您查看私有本機類型的使用不正確的位置。 使用[make_public](../preprocessor/make-public.md)實用新型為原始碼檔中無法修改的本機類型提供公共可存取。

如需詳細資訊，請參閱 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。

下面的範例展示如何聲明類型並指定其可存取性,然後在程式集中存取這些類型。 當然,如果使用引用具有私有類型的程式集`#using`,則只有程式集中的公共類型可見。

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

現在,讓我們重寫前面的示例,以便將其構建為 DLL。

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

下一個範例簡用如何存取程式集外部的類型。 在此範例中,用戶端使用上一個範例中生成的元件。

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a>成員可見度

您可以使用訪問指定器`public`對 ,使從同一程式集中訪問公共類的成員不同於從程式集外部存取公共類`protected`的成員。`private`

下表總結了各種存取指定器的效果:

|規範|效果|
|---------------|------------|
|public|成員可在程式集內外訪問。  有關詳細資訊,請參閱[公眾](../cpp/public-cpp.md)。|
|private|成員不可訪問,無論是在程式集內部還是外部。  有關詳細資訊,請參閱[私有](../cpp/private-cpp.md)。|
|protected|成員可在程式集內外訪問,但只能訪問派生類型。  有關詳細資訊,請參閱[受保護](../cpp/protected-cpp.md)。|
|internal|成員在程式集內是公共的,但在程式集外部是私有的。  `internal` 是即時線上關鍵字。  如需詳細資訊，請參閱[內容相關性關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。|
|公共保護-或受保護的公眾|成員在程式集內是公共的,但在程式集外部受到保護。|
|私有保護 -或受保護的私有|成員在程式集內受到保護,但在程式集外部是私有的。|

下面的示例顯示了一種公共類型,該類型具有使用不同的訪問許可權聲明的成員,然後顯示這些成員從程式集內訪問。

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

現在,讓我們將前面的示例構建為 DLL。

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

以下範例使用在前一個範例中創建的元件,從而演示如何從程式集外部訪問成員。

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a>公共和私有本機類

可以從託管類型引用本機類型。  例如,託管類型的函數可以採用其類型為本機結構的參數。  如果託管類型和函數在程式集中是公共的,則本機類型也必須為公共類型。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

您可以建立使用本機類型的源碼檔:

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

現在,編譯用戶端:

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a>靜態建構函數

CLR 類型(例如類或結構)可以具有可用於初始化靜態數據成員的靜態構造函數。  靜態構造函數最多調用一次,並在首次訪問類型的任何靜態成員之前調用。

實例構造函數始終在靜態構造函數之後運行。

如果類具有靜態構造函數,編譯器不能將調用內聯到構造函數。  如果類是值類型、具有靜態構造函數並且沒有實例構造函數,則編譯器不能將調用內聯到任何成員函數。  CLR 可以內聯調用,但編譯器不能。

將靜態構造函數定義為私有成員函數,因為它僅由CLR調用。

有關靜態構造函數的詳細資訊,請參閱[如何:定義介面靜態構造函數 (C++/CLI)。](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>此指標的語義

使用 Visual C++定義類型`this`時, 引用類型的指標的類型為「句柄」。 值`this`類型的指標為「內部指標」類型。

當調用預設索引器時`this`,指標的這些不同語義可能會導致意外行為。 下一個範例顯示了在 ref 類型和值類型中訪問預設索引器的正確方法。

如需相關資訊，請參閱

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a>按簽署隱藏功能

在標準C++中,基類中的函數由派生類中具有相同名稱的函數隱藏,即使派生類函數的參數數量或類型不同。 這稱為 *「逐名隱藏*」語義。 在引用類型中,如果名稱和參數清單相同,則基類中的函數只能由派生類中的函數隱藏。 這稱為 *"按簽名隱藏*"語義。

當類的所有函數在元數據中標記為`hidebysig`時,類被視為按簽名隱藏類。 預設情況下,在 **/clr**下創建的所有`hidebysig`類都有 函數。 當類具有`hidebysig`函數時,編譯器不會在任何直接基類中按名稱隱藏函數,但如果編譯器在繼承鏈中遇到逐名隱藏類,則它將繼續這種逐個名稱隱藏行為。

在"逐個簽名"語義下,當在對象上調用函數時,編譯器標識包含可滿足函數調用的函數的最派生類。 如果類中只有一個函數可以滿足調用,編譯器將調用該函數。 如果類中有多個函數可以滿足調用,編譯器將使用重載解析規則來確定調用哪個函數。 有關重載規則的詳細資訊,請參閱[函數重載](../cpp/function-overloading.md)。

對於給定的函數調用,基類中的函數可能具有一個簽名,使其比派生類中的函數稍微匹配一些。 但是,如果在派生類的對象上顯式調用該函數,則調用派生類中的函數。

由於返回值不被視為函數簽名的一部分,因此,如果基類函數具有相同的名稱,並且採用與派生類函數相同的數量和類型的參數,即使它在返回值的類型上有所不同,則隱藏該函數。

下面的示例顯示基類中的函數不被派生類中的函數隱藏。

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

下一個範例顯示 Microsoft C++編譯器調用派生最多的類中的函數,即使需要轉換以匹配一個或多個參數,也不會調用基類中更適合函數調用的函數。

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

下面的示例顯示,即使基類具有與派生類相同的簽名,也可以隱藏函數。

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a>複製建構函式

C++標準表示,在移動物件時調用複製構造函數,以便在同一位址創建和銷毀物件。

但是,當 **/clr**用於編譯,編譯到 MSIL 的函數調用本機函數,其中本機類(或多個類)通過值傳遞,而本機類具有複製構造函數和/或析構函數,則不調用任何複製構造函數,並且物件在創建位置不同的位址被銷毀。 如果類本身有指標,或者代碼按位址跟蹤物件,則可能會導致問題。

有關詳細資訊,請參閱[/clr(通用語言執行時編譯)](../build/reference/clr-common-language-runtime-compilation.md)。

以下範例示範如何生成複製建構函數。

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a>析構函數和終結器

引用類型的析構函數執行資源確定性清理。 終結器清理非託管資源,並且可以由析構函數或垃圾回收器在確定性上調用確定性資源。 有關標準C++中的析構函數的資訊,請參閱[析構函數](../cpp/destructors-cpp.md)。

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

託管 Visual C++ 類中的析構函數的行為不同於 C++的託管擴展。 有關此更改的詳細資訊,請參閱[析構函數語義中的變更](../dotnet/changes-in-destructor-semantics.md)。

CLR 垃圾回收器刪除未使用的託管物件,並在不再需要它們時釋放其記憶體。 但是,類型可能使用垃圾回收器不知道如何釋放的資源。 這些資源稱為非託管資源(例如本機檔句柄)。 我們建議您釋放終結器中的所有非託管資源。 由於託管資源由垃圾回收器非確定性地釋放,因此在終結器中引用託管資源不安全,因為垃圾回收器可能已清理該託管資源。

可視化C++終結器與<xref:System.Object.Finalize%2A>方法不同。 (CLR 文件使用終結器和<xref:System.Object.Finalize%2A>方法 同義)。 垃圾<xref:System.Object.Finalize%2A>回收器調用該方法,它調用類繼承鏈中的每個終結器。 與 Visual C++析構函數不同,派生類終結器調用不會導致編譯器調用所有基類中的終結器。

由於 Microsoft C++編譯器支援資源確定性釋放,因此不要嘗試<xref:System.IDisposable.Dispose%2A><xref:System.Object.Finalize%2A>實現 或 方法。 但是,如果您熟悉這些方法,下面是 Visual C++終結器和將終結器映射<xref:System.IDisposable.Dispose%2A>調用 模式的析構函數的方式:

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

託管類型還可以使用您希望以確定性方式釋放的託管資源,而不是讓垃圾回收器在不再需要物件后的某個時間點以非確定性方式釋放。 確定性資源釋放可以顯著提高性能。

Microsoft C++編譯器使析構函數的定義能夠確定清理物件。 使用析構函數釋放要確定釋放的所有資源。  如果存在終結器,請從析構函數調用它,以避免代碼重複。

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

如果使用您的類型的代碼不調用析構函數,則垃圾回收器最終將釋放所有託管資源。

析構函數的存在並不意味著存在終結器。 但是,終結器的存在意味著您必須定義析構函數並從該析構函數調用終結器。 這提供了非託管資源的確定性釋放。

調用析構函數會通過物件的<xref:System.GC.SuppressFinalize%2A>「定稿」來抑制。 如果未調用析構函數,則垃圾回收器最終將調用類型的終結器。

與讓 CLR 非確定性地完成物件相比,通過調用析構函數來確定清理物件的資源可以提高性能。

從 Visual C++ 中編寫並使用 **/clr**編譯的代碼在:

- 使用堆疊語義創建的物件超出範圍。 有關詳細資訊,請參閱[C++堆疊文的參考類型](../dotnet/cpp-stack-semantics-for-reference-types.md)。

- 在對象的構造期間引發異常。

- 該物件是正在運行析構函數的物件中的成員。

- 在句柄上調用[刪除](../cpp/delete-operator-cpp.md)運算符 ([句柄到對象運算符(*)。](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- 顯式調用析構函數。

如果類型被用其他語言編寫的用戶端使用,則析構函數的調用方式如下:

- 在呼叫<xref:System.IDisposable.Dispose%2A>時。

- 在類型`Dispose(void)`上的調用。

- 如果類型超出 C#`using`語句的範圍。

如果在託管堆上創建引用類型的物件(不對引用類型使用堆疊語義),請使用[嘗試-finally](../cpp/try-finally-statement.md)語法來確保異常不會阻止析構函數運行。

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

如果類型具有析構函數,編譯器將生成實現`Dispose`<xref:System.IDisposable>的方法。 如果以 Visual C++編寫的類型具有從另一種語言消耗的析構函數,則`IDisposable::Dispose`調用 該類型會導致調用該類型的析構函數。 當類型從 Visual C++ 用戶端使用時,不能`Dispose`直接調用 ;相反,使用`delete`運算符調用析構函數。

如果類型具有終結器,編譯器將生成一個`Finalize(void)`重<xref:System.Object.Finalize%2A>寫的方法。

如果類型具有終結器或析構函數,編譯器將根據設計模式產生方法`Dispose(bool)`。 (有關資訊,請參閱[處置模式](/dotnet/standard/design-guidelines/dispose-pattern)。 您不能在 Visual C++中`Dispose(bool)`顯式創作或調用。

如果類型具有符合設計模式的基類,則當調用派生類的析構函數時,將調用所有基類的析構函數。 (如果類型是在 Visual C++中編寫的,編譯器將確保類型實現此模式。換句話說,引用類的析構函數按C++標準指定,鏈到其基和成員,首先運行類的析構函數,然後按其構造順序相反的成員的析構函數,最後以其基類的析構函數按其構造順序的相反運行。

不允許在值類型或介面內使用析構函數和終結器。

只能以引用類型定義或聲明終結器。 與構造函數和析構函數一樣,終結器沒有返回類型。

運行物件的終結器后,還會調用任何基類中的終結器,從派生最少的類型開始。 數據成員的終結者不會由類的終結器自動連結到。

如果終結器刪除託管類型的本機指標,則必須確保不會過早地收集對本機指標的引用或通過本機指標收集的引用;否則,將不過早地收集對本機指標的引用。呼叫託管型態的析構函數,而不是使用<xref:System.GC.KeepAlive%2A>。

在編譯時,可以檢測類型是具有終結器還是析構函數。 如需詳細資訊，請參閱[類型特徵的編譯器支援](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

下一個示例顯示兩種類型,一種具有非託管資源,另一種具有具有確定性釋放的託管資源。

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
