---
title: "編譯器錯誤 C2440 |Microsoft 文件"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2440
dev_langs:
- C++
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62a83da358738f7892fd5db06fbe775ff0b7d7da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2440"></a>編譯器錯誤 C2440
'conversion': 無法從 'type1' 轉換成 'type2'  
  
編譯器無法轉換成`type1`至`type2`。  
  
## <a name="example"></a>範例  
如果您嘗試初始化非常數，可能會造成 C2440 `char*` (或`wchar_t*`) 使用字串常值在 c + + 程式碼中，當編譯器一致性選項[/zc: strictstrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)設定。 在 C 中，字串常值的型別是陣列`char`，但它是在 c + + 陣列的`const char`。 這個範例會產生 C2440:  
  
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
  
## <a name="example"></a>範例  
 如果您嘗試將指標轉換成 void * 的成員，也可能造成 C2440。 下一個範例會產生 C2440:  
  
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
  
## <a name="example"></a>範例  
 如果您嘗試從僅向前宣告，但未定義的型別轉換，也可能造成 C2440。 這個範例會產生 C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## <a name="example"></a>範例  
 C2440 上的錯誤行 15 到 16 的下一個範例以限定`Incompatible calling conventions for UDT return value`訊息。 A *UDT*是使用者定義的型別，例如類別、 結構或等位。 UDT 的呼叫慣例會指定與實際呼叫慣例的 UDT 和相關函式指標的向前宣告相衝突的傳回型別時，會導致這些種類的不相容性錯誤。  
  
 在此範例中，第一次有向前宣告的結構和函式會傳回結構;編譯器會假設該結構中使用 c + + 呼叫慣例。 接下來結構定義，根據預設，會使用 C 呼叫慣例。 因為編譯器不知道該結構的呼叫慣例，直到它完成讀取整個結構中的傳回型別結構的呼叫慣例`get_c2`也假設為 c + +。  
  
 結構後面接著另一個函式宣告會傳回結構，但此時，編譯器知道結構的呼叫慣例是 c + +。 同樣地，函式指標，它會傳回結構，定義結構定義之後，因此編譯器知道結構會使用 c + + 呼叫慣例。  
  
 若要解決不相容的呼叫慣例，就會發生的 C2440，宣告函式傳回 UDT 定義之後的 UDT。  
  
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
  
## <a name="example"></a>範例  
 如果您指派零到內部指標，也會發生 C2440:  
  
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
  
## <a name="example"></a>範例  
 C2440 也可能使用不正確的使用者定義的轉換。 例如，當轉換運算子定義為`explicit`，編譯器無法隱含轉換中使用它。 如需使用者定義轉換的詳細資訊，請參閱[使用者定義轉換 (C + + /CLI)](../../dotnet/user-defined-conversions-cpp-cli.md))。 這個範例會產生 C2440:  
  
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
  
## <a name="example"></a>範例  
 如果您嘗試建立其型別是 Visual c + + 陣列的執行個體也會發生 C2440 <xref:System.Array>。  如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  下一個範例會產生 C2440:  
  
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
  
## <a name="example"></a>範例  
 C2440 也可能是因為屬性功能中的變更。  下列範例會產生 C2440。  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## <a name="example"></a>範例  
 Visual c + + 編譯器不再允許[const_cast 運算子](../../cpp/const-cast-operator.md)向下轉型時來源使用的程式碼**/clr**程式設計進行編譯。  
  
 若要解決此 C2440，使用正確的轉型運算子。 如需詳細資訊，請參閱[轉型運算子](../../cpp/casting-operators.md)。  
  
 這個範例會產生 C2440:  
  
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
  
## <a name="example"></a>範例  
C2440 可以發生在 Visual Studio 2015 Update 3 編譯器一致性變更。 先前，編譯器不正確地視為特定相異運算式相同的型別識別針對範本比對時`static_cast`作業。 現在，編譯器是否正確，可區別類型和程式碼所依賴先前`static_cast`行為就會中斷。 若要修正此問題，變更以符合該樣板參數類型，或使用的樣板引數`reinterpret_cast`c-style 轉換或。
  
這個範例會產生 C2440:  
  
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

## <a name="example"></a>範例  
### <a name="copy-list-initialization"></a>Copy-list-initialization

2017 和更新版本的 visual Studio 正確引發編譯器錯誤與使用 Visual Studio 2015 中未被攔截，可能會導致損毀的初始設定式清單的物件建立相關或未定義的執行階段行為。 在 C + + 17 複製-清單初始化，編譯器需要考慮的多載解析的明確建構函式，但如果實際上選擇該多載，則必須引發錯誤。

下列範例會在 Visual Studio 2015 中，但不是在 Visual Studio 2017 編譯。

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

## <a name="example"></a>範例
### <a name="cv-qualifiers-in-class-construction"></a>類別建構中的 cv 限定詞

在 Visual Studio 2015 中，透過建構函式呼叫來產生類別物件時，編譯器有時會錯誤地忽略 cv 限定詞。 這可能會導致當機或意外執行階段行為。 下列範例會在 Visual Studio 2015 中編譯，但會引發編譯器錯誤在 Visual Studio 2017 和更新版本：

```cpp
struct S 
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

若要更正錯誤，請將運算子 int() 宣告為 const。
