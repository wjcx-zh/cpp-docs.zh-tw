---
title: 如何：定義和使用委派 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: 495ceea6afb222d13953b3a25b7a1c836b299de6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216397"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>如何：定義和使用委派 (C++/CLI)

本文說明如何在 c + +/CLI 中定義和使用委派

雖然 .NET Framework 會提供一些委派，但有時候您可能必須定義新的委派。

下列程式碼範例會定義名為的委派 `MyCallback` 。 事件處理常式代碼（引發這個新委派時所呼叫的函式）必須具有的傳回型別 **`void`** ，並接受 <xref:System.String> 參考。

Main 函式會使用所定義的靜態方法來具現 `SomeClass` 化 `MyCallback` 委派。 委派接著會變成呼叫此函式的替代方法，如藉由將字串 "single" 傳送至委派物件所示範。 接下來，會將的其他實例 `MyCallback` 連結在一起，然後藉由一次呼叫委派物件來執行。

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

下一個程式碼範例顯示如何將委派與實值類別的成員產生關聯。

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>如何撰寫委派

您可以使用 " `-` " 運算子，從組成的委派中移除元件委派。

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**輸出**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>將委派 ^ 傳遞至預期函式指標的原生函式

從 managed 元件中，您可以使用函式指標參數呼叫原生函式，其中原生函式可以呼叫 managed 元件之委派的成員函式。

這個範例會建立匯出原生函式的 .dll：

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

下一個範例會使用 .dll，並將委派控制碼傳遞至預期函式指標的原生函式。

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**輸出**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>將委派與非受控函式產生關聯

若要讓委派與原生函式產生關聯，您必須將原生函式包裝在 managed 類型中，並宣告要透過叫用的函式 `PInvoke` 。

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**輸出**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>若要使用未系結的委派

您可以使用未系結的委派，在呼叫委派時，傳遞您想要呼叫其函式之類型的實例。

如果您想要逐一查看集合中的物件（藉由使用[for each、in](../dotnet/for-each-in.md)關鍵字），並在每個實例上呼叫成員函式，則未系結的委派會特別有用。

以下是宣告、具現化和呼叫系結和未系結委派的方法：

|動作|系結委派|取消繫結委派|
|------------|---------------------|-----------------------|
|宣告|委派簽章必須符合您想要透過委派呼叫之函式的簽章。|委派簽章的第一個參數是您想要呼叫之物件的型別 **`this`** 。<br /><br /> 在第一個參數之後，委派簽章必須符合您想要透過委派呼叫之函式的簽章。|
|化|當您具現化系結委派時，您可以指定實例函數或全域或靜態成員函式。<br /><br /> 若要指定實例函式，第一個參數是您想要呼叫其成員函式之類型的實例，而第二個參數則是您想要呼叫之函式的位址。<br /><br /> 如果您想要呼叫全域或靜態成員函式，只要傳遞全域函式的名稱或靜態成員函式的名稱即可。|當您具現化未系結的委派時，只要傳遞您要呼叫之函式的位址即可。|
|呼叫|當您呼叫系結委派時，只要傳遞委派簽章所需的參數即可。|與系結委派相同，但請記住，第一個參數必須是物件的實例，其中包含您想要呼叫的函數。|

這個範例示範如何宣告、具現化和呼叫未系結的委派：

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**輸出**

```Output
2
3
2
3
2
7
8
7
8
7
```

下一個範例示範如何使用未系結的委派和[for each，在關鍵字中](../dotnet/for-each-in.md)逐一查看集合中的物件，並在每個實例上呼叫成員函式。

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

這個範例會建立屬性存取子函式的未系結委派：

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**輸出**

```Output
11
```

下列範例示範如何叫用多播委派，其中一個實例已系結，另一個實例已解除系結。

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**輸出**

```Output
in f(R ^ r)
in f()
```

下一個範例顯示如何建立和呼叫未系結的泛型委派。

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**輸出**

```Output
12
14
```

## <a name="see-also"></a>另請參閱

[delegate (C++ 元件擴充功能)](../extensions/delegate-cpp-component-extensions.md)
