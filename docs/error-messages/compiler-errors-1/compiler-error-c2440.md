---
title: "編譯器錯誤 C2440 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2440"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2440"
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2440
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

conversion' : 無法從 'type1' 轉換為 'type2'  
  
 編譯器無法從 '`type1`' 轉換為 '`type2`'。  
  
## 範例  
 如果在設定了編譯器一致性選項 [\/Zc:strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 時嘗試在 C\+\+ 程式碼中使用字串常值初始化非常數的 `char*` \(或 `wchar_t*`\)，可能會造成 C2440。  在 C\# 中，字串常值的類型是 `char` 的陣列，但在 C\+\+ 中，則是 `const``char` 的陣列。  這個範例產生 C2440：  
  
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
  
## 範例  
 如果嘗試將成員指標轉換為 void\*，也可能造成 C2440 錯誤。  下一個範例會產生 C2440：  
  
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
  
## 範例  
 如果嘗試從只順向宣告但未定義的類型轉換，也會造成 C2440。  這個範例產生 C2440：  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## 範例  
 以下範例中 15 和 16 行上的 C2440 錯誤將以 `Incompatible calling conventions for UDT return value` 訊息限定。\(UDT 是使用者定義的型別，例如類別、結構或等位\)。這些不相容錯誤發生的原因是：順向宣告 \(Forward Declaration\) 的傳回類型中所指定 UDT 呼叫慣例與實際的 UDT 呼叫慣例產生衝突，以及牽涉到函式指標。  
  
 在此範例中，我們先順向宣告了一個結構和一個傳回該結構的函式；編譯器會假設該結構使用 C\+\+ 呼叫慣例。  接下來在預設狀態下，結構定義使用 C 的呼叫慣例。  因為編譯器必須等到讀完整個結構之後才知道結構的呼叫慣例，因此對於 `get_c2` 傳回類型的結構，其呼叫慣例也將假設為 C\+\+。  
  
 結構之後是另一個傳回該結構的函式宣告，但此時編譯器已知道該結構的呼叫慣例為 C\+\+。  同樣地，傳回該結構的函式指標亦定義於結構定義之後，因此編譯器知道該結構使用 C\+\+ 的呼叫慣例。  
  
 若要解決因為呼叫慣例不相容而發生的 C2440，請在 UDT 定義之後宣告傳回 UDT 的函式。  
  
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
  
## 範例  
 如果指定零給內部指標，也可能會發生 C2440：  
  
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
  
## 範例  
 使用者定義轉換使用不正確，也可能會發生 C2440。  如需使用者定義轉換的詳細資訊，請參閱[使用者定義轉換](../../dotnet/user-defined-conversions-cpp-cli.md)。  這個範例產生 C2440：  
  
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
  
## 範例  
 如果嘗試建立型別為 <xref:System.Array> 之 Visual C\+\+ 陣列的執行個體，也可能會發生 C2440。如需詳細資訊，請參閱[Arrays](../../windows/arrays-cpp-component-extensions.md)。下一個範例會產生 C2440：  
  
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
  
## 範例  
 C2440 也可能會因為屬性功能變更而發生。下列範例會產生 C2440：  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## 範例  
 在編譯使用 **\/clr** 程式設計的原始程式碼時，Visual C\+\+ 編譯器不再允許 [const\_cast 運算子](../../cpp/const-cast-operator.md) 執行向下轉換 \(Down Cast\)。  
  
 若要解決這個 C2440，請使用正確的轉型運算子。  如需詳細資訊，請參閱[轉型運算子](../../cpp/casting-operators.md)。  
  
 這個範例產生 C2440：  
  
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
  
## 範例  
 使用 **\/clr:oldSyntax** 也可以產生 C2440：  
  
```cpp  
// c2440h.cpp  
// compile with: /clr:oldSyntax  
__gc class Base {};  
__gc class Derived : public Base {};  
int main() {  
   Derived *d = new Derived;  
   Base *b = d;  
   d = const_cast<Derived*>(b);   // C2440  
   d = dynamic_cast<Derived*>(b);   // OK  
}  
```