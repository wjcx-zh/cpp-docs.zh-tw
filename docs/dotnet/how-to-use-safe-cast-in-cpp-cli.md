---
title: "如何：在 C++/CLI 中使用 safe_cast | Microsoft Docs"
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
  - "safe_cast 關鍵字 [C++], 向上轉型"
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用 safe_cast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將會示範如何在 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 應用程式使用 safe\_cast。  如需 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]中 safe\_cast 的詳細資訊，請參閱 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
## 向上轉型  
 向上轉型為衍生型別的轉型為其中一個基底類別。  這個轉換是安全的，不需要明確轉型標記法。  下列範例顯示如何執行向上轉型，與 `safe_cast` ，也不需要它。  
  
```  
// safe_upcast.cpp  
// compile with: /clr  
using namespace System;  
interface class A {  
   void Test();  
};  
  
ref struct B : public A {  
   virtual void Test() {  
      Console::WriteLine("in B::Test");  
   }  
  
   void Test2() {  
      Console::WriteLine("in B::Test2");  
   }  
};  
  
ref struct C : public B {  
   virtual void Test() override {  
      Console::WriteLine("in C::Test");  
   };  
};  
  
int main() {  
   C ^ c = gcnew C;  
  
   // implicit upcast  
   B ^ b = c;  
   b->Test();  
   b->Test2();  
  
   // upcast with safe_cast  
   b = nullptr;  
   b = safe_cast<B^>(c);  
   b->Test();  
   b->Test2();  
}  
```  
  
  **in C::Test**  
**in B::Test2**  
**in C::Test**  
**in B::Test2**   
## 向下轉型  
 向下轉型為基底類別的轉型為衍生自基底類別的類別。向下轉型是安全的，才能處理在執行階段的物件是實際位址每個衍生類別物件。不同於`static_cast`，如果轉換失敗， `safe_cast` 會執行動態檢查並擲回 <xref:System.InvalidCastException> 。  
  
```  
// safe_downcast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class A { void Test(); };  
  
ref struct B : public A {  
   virtual void Test() {   
      Console::WriteLine("in B::Test()");  
   }  
  
   void Test2() {   
      Console::WriteLine("in B::Test2()");  
   }  
};  
  
ref struct C : public B {  
   virtual void Test() override {   
      Console::WriteLine("in C::Test()");  
   }  
};  
  
interface class I {};  
  
value struct V : public I {};  
  
int main() {  
   A^ a = gcnew C();  
   a->Test();  
   B^ b = safe_cast<B^>(a);  
   b->Test();  
   b->Test2();  
  
   V v;   
   I^ i = v;   // i boxes V  
   V^ refv = safe_cast<V^>(i);   
  
   Object^ o = gcnew B;  
   A^ a2= safe_cast<A^>(o);  
}  
```  
  
  **in C::Test\(\)**  
**in C::Test\(\)**  
**in B::Test2\(\)**   
## 使用使用者定義轉換的 safe\_cast  
 下一個範例示範如何使用 `safe_cast` 叫用使用者定義的轉換。  
  
```  
// safe_cast_udc.cpp  
// compile with: /clr  
using namespace System;  
value struct V;  
  
ref struct R {  
   int x;  
   R() {  
      x = 1;  
   }  
  
   R(int argx) {  
      x = argx;  
   }  
  
   static operator R::V^(R^ r);  
};  
  
value struct V {  
   int x;  
   static operator R^(V& v) {  
      Console::WriteLine("in operator R^(V& v)");  
      R^ r = gcnew R();  
      r->x = v.x;    
      return r;  
   }  
  
   V(int argx) {  
      x = argx;  
   }  
};  
  
   R::operator V^(R^ r) {  
      Console::WriteLine("in operator V^(R^ r)");  
      return gcnew V(r->x);  
   }  
  
int main() {  
   bool fReturnVal = false;  
   V v(2);  
   R^ r = safe_cast<R^>(v);   // should invoke UDC  
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC  
}  
```  
  
  **in operator R^\(V& v**  
**in operator V^\(R^ r\)**   
## safe\_cast 和 boxing 作業  
 **Boxing**  
  
 Boxing 定義為編譯器插入，使用者定義的轉換。因此，您可以使用 `safe_cast` 將 CLR 堆積上的值設為 boxed。  
  
 下列範例顯示具有簡單和使用者定義的實值型別 Boxing。`safe_cast` 在原生堆疊上實值型別變數進行 Box 處理，讓它可以指派給記憶體回收堆積的變數。  
  
```  
// safe_cast_boxing.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct I {};  
  
value struct V : public I {   
   int m_x;  
  
   V(int i) : m_x(i) {}  
};  
  
int main() {  
   // box a value type  
   V v(100);  
   I^ i = safe_cast<I^>(v);  
  
   int x = 100;  
   V^ refv = safe_cast<V^>(v);  
   int^ refi = safe_cast<int^>(x);  
}  
```  
  
 下一個範例，容器會在使用者定義的轉換優先權在 `safe_cast` 作業。  
  
```  
// safe_cast_boxing_2.cpp  
// compile with: /clr  
static bool fRetval = true;  
  
interface struct I {};  
value struct V : public I {  
   int x;  
  
   V(int argx) {  
      x = argx;  
   }  
  
   static operator I^(V v) {  
      fRetval = false;  
      I^ pi = v;  
      return pi;  
   }  
};  
  
ref struct R {  
   R() {}  
   R(V^ pv) {}  
};  
  
int main() {  
   V v(10);  
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"  
}  
```  
  
 **Unboxing**  
  
 UnBoxing 定義為編譯器插入，使用者定義的轉換。因此，您可以使用 `safe_cast` 將 CLR 堆積上的值設為 uxboxed。  
  
 Unbox 處理是使用者定義的轉換，不過，不同於 Boxing、Unboxing 必須是明確的，它必須由 `static_cast`， C\-Style 轉換或者 `safe_cast`執行;Unboxing 無法以隱含方式執行。  
  
```  
// safe_cast_unboxing.cpp  
// compile with: /clr  
int main() {  
   System::Object ^ o = 42;  
   int x = safe_cast<int>(o);  
}  
```  
  
 下列範例顯示具有實值型別和基本型別的 Unboxing。  
  
```  
// safe_cast_unboxing_2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct I {};  
  
value struct VI : public I {};  
  
void test1() {  
   Object^ o = 5;  
   int x = safe_cast<Int32>(o);  
}  
  
value struct V {  
   int x;  
   String^ s;  
};  
  
void test2() {  
   V localv;  
   Object^ o = localv;  
   V unboxv = safe_cast<V>(o);  
}  
  
void test3() {  
   V localv;  
   V^ o2 = localv;  
   V unboxv2 = safe_cast<V>(o2);  
}  
  
void test4() {  
   I^ refi = VI();  
   VI vi  = safe_cast<VI>(refi);  
}  
  
int main() {  
   test1();  
   test2();  
   test3();  
   test4();  
}  
```  
  
## safe\_cast 和泛型型別  
 下一個範例示範如何使用 `safe_cast` 執行向下轉換與泛型型別。  
  
```  
// safe_cast_generic_types.cpp  
// compile with: /clr  
interface struct I {};  
  
generic<class T> where T:I  
ref struct Base {  
   T t;  
   void test1() {}  
};  
  
generic<class T> where T:I  
ref struct Derived:public Base <T> {};  
  
ref struct R:public I {};  
  
typedef Base<R^> GBase_R;  
typedef Derived<R^> GDerived_R;  
  
int main() {  
   GBase_R^ br = gcnew GDerived_R();  
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);  
}  
```  
  
## 請參閱  
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)