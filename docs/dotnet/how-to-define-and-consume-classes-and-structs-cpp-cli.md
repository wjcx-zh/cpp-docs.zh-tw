---
title: '如何：定義和使用類別和結構 (c + +/CLI) '
description: 如何在 c + +/CLI 程式碼中建立及使用使用者定義的類別和結構類型。
ms.date: 09/25/2020
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 17d0885d42febc1d2789c8711b54a76066ee8176
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414577"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定義和使用類別和結構 (c + +/CLI) 

本文說明如何在 c + +/CLI 中定義和使用使用者定義的參考型別和實數值型別

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a> 物件具現化

參考 (ref) 類型只能在 managed 堆積上具現化，而不是在堆疊上或在原生堆積上具現化。 實值型別可在堆疊或 managed 堆積上具現化。

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> 隱含抽象類別

*隱含抽象類別*無法具現化。 當下列情況時，類別會隱含抽象化：

- 類別的基底類型是介面，而
- 類別不會執行所有介面的成員函式。

您可能無法從衍生自介面的類別來建立物件。 原因可能是類別是隱含抽象的。 如需抽象類別的詳細資訊，請參閱 [抽象](../extensions/abstract-cpp-component-extensions.md)。

下列程式碼範例示範無法具現化類別，因為函式並未實作為函式 `MyClass` `MyClass::func2` 。 若要讓範例進行編譯，請取消批註 `MyClass::func2` 。

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a> 類型可見度

您可以控制 common language runtime (CLR) 類型的可見度。 參考您的元件時，您可以控制元件中的類型是可見的，還是在元件外部看不到。

`public` 指出包含型別之元件的指示詞的任何原始程式檔都可以看見型別 `#using` 。  `private` 指出包含型別之元件的指示詞的原始程式檔看不到型別 `#using` 。 不過，私用類型會顯示在相同的元件中。 根據預設，類別的可見度為 `private` 。

根據預設，在 Visual Studio 2005 之前，原生類型在元件外部具有公用存取範圍。 啟用 [編譯器警告 (層級 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) ，以協助您瞭解私用原生類型的使用方式不正確。 使用 [make_public](../preprocessor/make-public.md) pragma，將公用存取範圍提供給無法修改之原始程式碼檔中的原生類型。

如需詳細資訊，請參閱 [#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。

下列範例示範如何宣告型別並指定其存取範圍，然後在元件記憶體取這些類型。 如果使用參考具有私用類型的元件，則 `#using` 只會顯示元件中的公用類型。

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

現在，讓我們重寫先前的範例，讓它以 DLL 的形式建立。

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

下一個範例顯示如何存取元件之外的型別。 在此範例中，用戶端會使用先前範例中所建立的元件。

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a> 成員可見度

您可以使用存取規範的配對，從元件外部存取公用類別的成員，而不是從元件外部存取該成員。 **`public`** **`protected`****`private`**

下表摘要說明各種存取規範的效果：

|規範|效果|
|---------------|------------|
|`public`|成員可在元件內部和外部進行存取。 如需詳細資訊，請參閱 [`public`](../cpp/public-cpp.md)。|
|`private`|成員在元件內部和外部無法存取。  如需詳細資訊，請參閱 [`private`](../cpp/private-cpp.md)。|
|`protected`|成員可在元件內部和外部存取，但僅適用于衍生類型。 如需詳細資訊，請參閱 [`protected`](../cpp/protected-cpp.md)。|
|`internal`|成員在元件內是公用的，但在元件外部是私用的。 `internal` 是即時線上關鍵字。  如需詳細資訊，請參閱[內容相關性關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。|
|`public protected` -或- `protected public`|成員在元件內是公用的，但在元件外部受到保護。|
|`private protected` -或- `protected private`|成員在元件內部受到保護，但在元件外部是私用的。|

下列範例顯示的公用類型具有使用不同存取規範宣告的成員。 然後，它會顯示從元件內部對這些成員的存取。

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

現在讓我們以 DLL 的形式建立先前的範例。

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

下列範例會使用在上一個範例中建立的元件。 它會顯示如何從元件外部存取成員。

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> 公用和私用原生類別

您可以從 managed 類型參考原生類型。  例如，managed 型別中的函式可以採用其型別為原生結構的參數。  如果 managed 型別和函式在元件中是公用的，則原生型別也必須是公用的。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

接下來，建立使用原生類型的原始程式碼檔：

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

現在，編譯用戶端：

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a> 靜態函式

CLR 類型（例如類別或結構）可以有可用於初始化靜態資料成員的靜態函式。  靜態的函式最多隻會呼叫一次，而且會在第一次存取型別的任何靜態成員之前呼叫。

實例的函式一律會在靜態函式之後執行。

如果類別具有靜態的函式，則編譯器無法內嵌對函式的呼叫。 如果類別是實值型別、具有靜態的函式，而且沒有實例的函式，則編譯器無法內嵌對任何成員函式的呼叫。 CLR 可以內嵌呼叫，但編譯器無法。

將靜態的函式定義為私用成員函式，因為它的目的只是要由 CLR 呼叫。

如需靜態函式的詳細資訊，請參閱 [如何：定義介面靜態函式 (c + +/cli) ](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>指標的語義 `this`

當您使用 c + + \CLI 來定義型別時， **`this`** 參考型別中的指標是型別 *控制碼*。 實 **`this`** 值型別中的指標是 *內部指標*類型。

**`this`** 當呼叫預設索引子時，指標的這些不同語義可能會導致非預期的行為。 下一個範例會顯示在 ref 型別和實值型別中存取預設索引子的正確方式。

如需詳細資訊，請參閱 [物件運算子控制碼 (^) ](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) 和 [Interior_ptr (c + +/cli) ](../extensions/interior-ptr-cpp-cli.md)

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> 依簽章隱藏函式

在標準 c + + 中，衍生類別中的函式會隱藏基類中的函式，即使衍生類別函數沒有相同類型或數目的參數也是一樣。 這就是所謂的 *依名稱隱藏* 語義。 在參考型別中，如果名稱和參數清單相同，則基類中的函式只會被衍生類別中的函式所隱藏。 這就是所謂的 *隱藏簽* 章語義。

當類別的所有函式在中繼資料中標記為時，就會將類別視為隱藏簽章類別 `hidebysig` 。 根據預設，在下建立的所有類別 **`/clr`** 都具有函式 `hidebysig` 。 當某個類別具有函式時 `hidebysig` ，編譯器不會在任何直接基類中依名稱隱藏函式，但是如果編譯器在繼承鏈中遇到依名稱隱藏的類別，則會繼續進行依名稱的隱藏行為。

在隱藏簽章的語法下，當在物件上呼叫函式時，編譯器會識別最常衍生的類別，其中包含可滿足函式呼叫的函式。 如果類別中只有一個可滿足呼叫的函式，則編譯器會呼叫該函式。 如果類別中有一個以上可滿足呼叫的函式，編譯器會使用多載解析規則來判斷要呼叫的函式。 如需多載規則的詳細資訊， [請參閱函](../cpp/function-overloading.md)式多載。

針對指定的函式呼叫，基類中的函式可能會有簽章，使其比衍生類別中的函式更好。 但是，如果函式是在衍生類別的物件上明確呼叫，則會呼叫衍生類別中的函式。

由於傳回值不會被視為函式簽章的一部分，因此，如果基類函式具有相同的名稱，並採用與衍生類別函式相同的種類和數目的引數，即使它不同于傳回值的類型，也會被隱藏。

下列範例顯示基類中的函式不會隱藏基類中的函式。

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

下一個範例顯示 Microsoft c + + 編譯器會呼叫最常衍生類別中的函式，即使需要轉換來比對一或多個參數，也不會在基類中呼叫函式，而該函式呼叫會比較符合函式呼叫。

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

下列範例顯示即使基類的簽章與衍生類別相同，也可以隱藏函式。

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a> 複製函式

C + + 標準指出當移動物件時，會呼叫複製的函式，以便在相同的位址建立和終結物件。

不過，當編譯為 MSIL 的函式呼叫原生函式，其中的原生類別（或多個）以傳值方式傳遞，且原生類別具有複製函式或析構函式時，不會呼叫複製的函式，而且物件會在與建立時不同的位址終結。 如果類別具有指向自身的指標，或如果程式碼是依位址追蹤物件，此行為可能會造成問題。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)。

下列範例會示範何時不產生複製的函式。

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> 析構函數和完成項

參考型別中的析構程式會對資源進行決定性的清除。 完成項清除未受管理的資源，並可由函式以決定性的方式呼叫，或由垃圾收集行程非確定性地。 如需標準 c + + 中之析構函數的詳細資訊，請參閱「[析構](../cpp/destructors-cpp.md)

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

CLR 垃圾收集行程會刪除未使用的 managed 物件，並在不再需要時釋放其記憶體。 不過，型別可能會使用垃圾收集行程不知道如何釋放的資源。 這些資源稱為 *非受控* 資源 (原生檔案控制代碼，例如) 。 建議您釋放完成項中的所有非受控資源。 垃圾收集行程會釋出受控資源非確定性地，因此在完成項中參考 managed 資源是不安全的。 這是因為垃圾收集行程可能已經清除它們。

Visual C++ 完成項與 <xref:System.Object.Finalize%2A> 方法不同。  (CLR 檔會使用完成項和 <xref:System.Object.Finalize%2A> 方法同義) 。 此 <xref:System.Object.Finalize%2A> 方法是由垃圾收集行程所呼叫，它會叫用類別繼承鏈中的每個完成項。 不同于 Visual C++ 的析構函數，衍生類別的完成項呼叫不會導致編譯器在所有基類中叫用完成項。

因為 Microsoft c + + 編譯器支援確定性的資源釋放，所以請勿嘗試實作為 <xref:System.IDisposable.Dispose%2A> 或 <xref:System.Object.Finalize%2A> 方法。 但是，如果您熟悉這些方法，以下是 Visual C++ 完成項和呼叫完成項的函式對應至模式的方式 <xref:System.IDisposable.Dispose%2A> ：

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

Managed 類型也可以使用您想要以決定性的方式發行的 managed 資源。 在不再需要物件之後，您可能不想讓垃圾收集行程釋放物件非確定性地。 確定性的資源版本可以大幅提升效能。

Microsoft c + + 編譯器可讓函式的定義以決定性的方式清除物件。 使用「函式」來釋出您想要以決定性方式發行的所有資源。  如果有完成項，請從函式呼叫它，以避免程式碼重複。

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

如果使用您的型別的程式碼不會呼叫該函式，垃圾收集行程最後會釋放所有 managed 資源。

函式的存在不表示完成項的存在。 不過，完成項表示您必須定義一個自訂函式，並從該函式呼叫完成項。 此呼叫提供非受控資源的決定性版本。

呼叫的函式會使用完成物件的結束，來抑制 <xref:System.GC.SuppressFinalize%2A> 。 如果未呼叫此函式，則最後會由垃圾收集行程呼叫您的型別完成項。

您可以藉由呼叫「函式」來明確清除物件的資源，而不是讓 CLR 非確定性地完成物件，藉以改善效能。

如果有下列情況，則以 Visual C++ 撰寫並使用編譯的程式碼會 **`/clr`** 執行類型的函式：

- 使用堆疊語義建立的物件會超出範圍。 如需詳細資訊，請參閱參考型別的 [c + + 堆疊語義](../dotnet/cpp-stack-semantics-for-reference-types.md)。

- 物件的結構中會擲回例外狀況。

- 物件是正在執行其執行程式之物件中的成員。

- 您可以在控制碼上呼叫 [delete](../cpp/delete-operator-cpp.md) 運算子， (控制碼運算子的控制碼 [ (^) ](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)) 。

- 您明確地呼叫該函式。

如果以其他語言撰寫的用戶端使用您的型別，則會呼叫此函式，如下所示：

- 呼叫時 <xref:System.IDisposable.Dispose%2A> 。

- 在類型的呼叫上 `Dispose(void)` 。

- 如果類型超出 c # 語句中的範圍 **`using`** 。

如果您未對參考型別使用堆疊語義，並且在 managed 堆積上建立參考型別的物件，請使用 [try-finally](../cpp/try-finally-statement.md) 語法，以確保例外狀況不會讓此函式無法執行。

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

如果您的類型有一個函式，編譯器會產生可執行檔 `Dispose` 方法 <xref:System.IDisposable> 。 如果以 Visual C++ 撰寫的型別，而且具有從另一種語言取用的函式，則 `IDisposable::Dispose` 在該型別上呼叫會導致呼叫類型的函式。 從 Visual C++ 用戶端取用型別時，您不能直接呼叫， `Dispose` 而是使用運算子呼叫此函式 **`delete`** 。

如果您的型別具有完成項，則編譯器 `Finalize(void)` 會產生可覆寫的方法 <xref:System.Object.Finalize%2A> 。

如果型別具有完成項或「函式」，則編譯器會 `Dispose(bool)` 根據設計模式產生方法。  (需詳細資訊，請參閱 [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)) 。 您無法在 Visual C++ 中明確撰寫或呼叫 `Dispose(bool)` 。

如果類型具有符合設計模式的基類，則會在呼叫衍生類別的函式時呼叫所有基類的析構函式。  (如果您的類型是以 Visual C++ 撰寫，則編譯器會確保您的型別會實作為此模式。 ) 換句話說，參考類別的函式會根據 c + + 標準所指定的基底和成員來連結。 首先，會執行類別的函式。 然後，其成員的析構函數會以它們的建立順序相反的循序執行。 最後，其基類的析構函數會以它們的建立順序相反的循序執行。

數值型別或介面中不允許有析構函數和完成項。

只能在參考型別中定義或宣告完成項。 和函式和函式一樣，完成項沒有傳回型別。

在物件的完成項執行之後，也會呼叫任何基類中的完成項，從最不衍生的類型開始。 資料成員的完成項不會由類別的完成項自動連結到。

如果完成項刪除 managed 類型中的原生指標，您必須確定不會提早收集或透過原生指標的參考。 在 managed 類型上呼叫此函式，而不是使用 <xref:System.GC.KeepAlive%2A> 。

您可以在編譯時期偵測型別是否具有完成項或函式。 如需詳細資訊，請參閱[類型特徵的編譯器支援](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

下一個範例會示範兩種類型：一個具有未受管理的資源，另一個則具有以決定性方式釋放的 managed 資源。

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

[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)
