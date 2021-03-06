---
title: 編譯器錯誤 C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 74c5032338b3f4cf30bdb75bdf070cee7b67ce58
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742108"
---
# <a name="compiler-error-c2440"></a>編譯器錯誤 C2440

' 轉換 '：無法從 ' type1 ' 轉換為 ' type2 '

編譯器無法從轉換 `type1` 成 `type2` 。

如果您嘗試 **`char*`** `wchar_t*` 在 c + + 程式碼中使用字串常值來初始化非 const (或) ，則在設定編譯器一致性選項 [/zc： strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 時，可能會造成 C2440。 在 C 中，字串常值的型別是的陣列 **`char`** ，但是在 c + + 中，它是的陣列 `const char` 。

## <a name="examples"></a>範例

此範例會產生 C2440：

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

如果您嘗試將成員指標轉換成 void *，也可能會造成 C2440。 下一個範例會產生 C2440：

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

如果您嘗試從僅向前宣告但未定義的類型進行轉換，則也可能會造成 C2440。 此範例會產生 C2440：

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

下一個範例的行15和16行的 C2440 錯誤會以訊息限定 `Incompatible calling conventions for UDT return value` 。 *UDT*是使用者定義型別，例如類別、結構或等位。 當向前宣告的傳回型別中所指定之 UDT 的呼叫慣例與 UDT 的實際呼叫慣例和函式指標相關時，就會導致這類不相容錯誤。

在此範例中，會先有結構的向前宣告，以及傳回結構的函式。編譯器會假設結構使用 c + + 呼叫慣例。 接下來是結構定義，預設會使用 C 呼叫慣例。 由於編譯器不知道結構的呼叫慣例，直到它完成讀取整個結構為止，傳回型別中結構的呼叫慣例 `get_c2` 也會假設為 c + +。

結構後面接著另一個會傳回結構的函式宣告，但此時，編譯器知道結構的呼叫慣例是 c + +。 同樣地，傳回結構的函式指標會定義在結構定義之後，讓編譯器知道結構會使用 c + + 呼叫慣例。

若要解決由於呼叫慣例不相容而發生的 C2440，請宣告在 UDT 定義之後傳回 UDT 的函數。

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

如果您將零指派給內部指標，也會發生 C2440：

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

如果使用者定義轉換的使用不正確，也可能會發生 C2440。 例如，當轉換運算子定義為時 **`explicit`** ，編譯器無法在隱含轉換中使用它。 如需使用者定義轉換的詳細資訊，請參閱 [ (c + +/cli) ) 的使用者定義轉換 ](../../dotnet/user-defined-conversions-cpp-cli.md) 。 此範例會產生 C2440：

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

如果您嘗試建立型別為的 Visual C++ 陣列的實例，也會發生 C2440 <xref:System.Array> 。  如需詳細資訊，請參閱[陣列](../../extensions/arrays-cpp-component-extensions.md)。  下一個範例會產生 C2440：

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

因為屬性功能中的變更，也會發生 C2440。  下列範例會產生 C2440。

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

當使用 **/clr**程式設計的原始程式碼經過編譯時，Microsoft c + + 編譯器不再允許[const_cast 運算子](../../cpp/const-cast-operator.md)進行轉換。

若要解決此 C2440，請使用正確的轉換運算子。 如需詳細資訊，請參閱 [轉換運算子](../../cpp/casting-operators.md)。

此範例會產生 C2440：

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

由於 Visual Studio 2015 Update 3 中編譯器的一致性變更，因此會發生 C2440。 先前，編譯器在識別作業的範本相符時，錯誤地將某些相異運算式視為相同的類型 **`static_cast`** 。 現在編譯器會正確地區分型別，而依賴先前行為的程式碼 **`static_cast`** 則會中斷。 若要修正此問題，請變更範本引數以符合範本參數類型，或使用 **`reinterpret_cast`** 或 C 樣式轉換。

此範例會產生 C2440：

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 和更新版本會使用未在 Visual Studio 2015 中攔截到的初始化運算式清單，正確地引發與物件建立相關的編譯器錯誤，而且可能會導致當機或未定義的執行時間行為。 在 c + + 17 的複製清單初始化中，編譯器必須考慮用於多載解析的明確的函式，但如果實際選擇該多載，就必須引發錯誤。

下列範例會在 Visual Studio 2015 中編譯，但不會在 Visual Studio 2017 中進行編譯。

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

若要更正錯誤，請使用直接初始化︰

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

### <a name="cv-qualifiers-in-class-construction"></a>類別建構中的 cv 限定詞

在 Visual Studio 2015 中，透過建構函式呼叫來產生類別物件時，編譯器有時會錯誤地忽略 cv 限定詞。 這可能會導致當機或意外執行階段行為。 下列範例會在 Visual Studio 2015 中編譯，但會在 Visual Studio 2017 和更新版本中引發編譯器錯誤：

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正錯誤，請將運算子 int() 宣告為 const。
