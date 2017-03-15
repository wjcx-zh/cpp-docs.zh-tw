---
title: "使用者定義轉換 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "使用者定義轉換 [C++]"
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者定義轉換 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在其中一個型別轉換為實值型別 \(Value Type\) 或參考型別的參考或執行個體時，這個章節將討論使用者定義的轉換 \(UDC\)。  
  
## 隱含和明確轉換  
 使用者定義的轉換可能是隱含或明確的。如果轉換不會造成資訊遺失， UDC 應該是隱含的。  否則會定義明確 UDC。  
  
 原生類別的建構函式可以用來轉換參考或實值型別的原生類別。  
  
 如需有關轉換的詳細資訊，請參閱[Boxing](../windows/boxing-cpp-component-extensions.md) 和[標準轉換](../cpp/standard-conversions.md)。  
  
```  
// mcpp_User_Defined_Conversions.cpp  
// compile with: /clr  
#include "stdio.h"  
ref class R;  
class N;  
  
value class V {  
   static operator V(R^) {  
      return V();  
   }  
};  
  
ref class R {  
public:  
   static operator N(R^);  
   static operator V(R^) {  
      System::Console::WriteLine("in R::operator N");  
      return V();  
   }  
};  
  
class N {  
public:  
   N(R^) {  
      printf("in N::N\n");  
   }  
};  
  
R::operator N(R^) {  
   System::Console::WriteLine("in R::operator N");  
   return N(nullptr);  
}  
  
int main() {  
   // Direct initialization:  
   R ^r2;  
   N n2(r2);   // direct initialization, calls constructor  
   static_cast<N>(r2);   // also direct initialization  
  
   R ^r3;  
   // ambiguous V::operator V(R^) and R::operator V(R^)  
   // static_cast<V>(r3);     
}  
```  
  
 **Output**  
  
  **在 N::N**  
**在 N::N**   
## 轉換來源運算子  
 轉換從運算子建立運算子從其他類別定義物件之類別的物件。  
  
 Standard C\+\+ 轉換不從運算子支援;Standard C\+\+ 用於這個建構函式。  不過，當使用 CLR 型別時， Visual C\+\+ 提供轉換從運算子的呼叫的語法支援。  
  
 與其他符合 CLS 標準的語言都要很好互通，您可能會想要將特定類別的每個使用者定義之一元的建構函式具有對應轉換從運算子。  
  
 轉換來源運算子  
  
-   將定義為靜態函式。  
  
-   可以是隱含 \(不會失去精確度，例如縮短為 int\) 的轉換或明確，雖然有精確度時遺失。  
  
-   會傳回包含類別的物件。  
  
-   將具有「從」型別為單一參數型別。  
  
 下列範例顯示隱含和明確「變更成」，從使用者定義的轉換 \(UDC\) 運算子。  
  
```  
// clr_udc_convert_from.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
  
   MyDouble(int i) {  
      d = static_cast<double>(i);  
      System::Console::WriteLine("in constructor");  
   }  
  
   // Wrap the constructor with a convert-from operator.  
   // implicit UDC because conversion cannot lose precision  
   static operator MyDouble (int i) {  
      System::Console::WriteLine("in operator");  
      // call the constructor  
      MyDouble d(i);  
      return d;  
   }  
  
   // an explicit user-defined conversion operator  
   static explicit operator signed short int (MyDouble) {  
      return 1;  
   }  
};  
  
int main() {  
   int i = 10;  
   MyDouble md = i;  
   System::Console::WriteLine(md.d);  
  
   // using explicit user-defined conversion operator requires a cast    
   unsigned short int j = static_cast<unsigned short int>(md);  
   System::Console::WriteLine(j);  
}  
```  
  
 **Output**  
  
  **in 運算子**  
**在建構函式中**  
**10**  
**1**   
## 轉換目標運算子  
 轉換為運算子的轉換運算子定義為其他物件類別的物件。  下列範例顯示隱含，將值轉換成，使用者定義的轉換運算子:  
  
```  
// clr_udc_convert_to.cpp  
// compile with: /clr  
using namespace System;  
value struct MyInt {  
   Int32 i;  
  
   // convert MyInt to String^  
   static operator String^ ( MyInt val ) {  
      return val.i.ToString();  
   }  
  
   MyInt(int _i) : i(_i) {}  
};  
  
int main() {  
   MyInt mi(10);  
   String ^s = mi;  
   Console::WriteLine(s);  
}  
```  
  
 **Output**  
  
  **10** 明確的使用者定義轉換為轉換運算子為可能會以某種方式遺失資料的轉換為適當的。  若要叫用明確轉換為運算子，則必須使用轉型。  
  
```  
// clr_udc_convert_to_2.cpp  
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
   d.d = 10.3;  
   System::Console::WriteLine(d.d);  
   int i = 0;  
   i = static_cast<int>(d);  
   System::Console::WriteLine(i);  
}  
```  
  
 **Output**  
  
  **10.3**  
**10**   
## 轉換泛型類別  
 您可以將泛型類別至 T。  
  
```  
// clr_udc_generics.cpp  
// compile with: /clr  
generic<class T>   
public value struct V {  
   T mem;  
   static operator T(V v) {  
      return v.mem;  
   }  
  
   void f(T t) {  
      mem = t;  
   }  
};  
  
int main() {  
   V<int> v;  
   v.f(42);  
   int i = v;  
   i += v;  
   System::Console::WriteLine(i == (42 * 2) );  
}  
```  
  
 **Output**  
  
  **True** 已轉換的建構函式接受型別來建立物件。已轉換的建構函式呼叫與只有直接初始化;轉換不會叫用轉換建構函式。  根據預設，轉換建構函式為 CLR 型別是明確的。  
  
```  
// clr_udc_converting_constructors.cpp  
// compile with: /clr  
public ref struct R {  
   int m;  
   char c;  
  
   R(int i) : m(i) { }  
   R(char j) : c(j) { }  
};  
  
public value struct V {  
   R^ ptr;  
   int m;  
  
   V(R^ r) : ptr(r) { }  
   V(int i) : m(i) { }  
};  
  
int main() {   
   R^ r = gcnew R(5);  
  
   System::Console::WriteLine( V(5).m);  
   System::Console::WriteLine( V(r).ptr);  
}  
```  
  
 **Output**  
  
  **5**  
**R** 在這個程式碼範例，隱含靜態轉換函式進行和明確轉換建構函式相同。  
  
```  
public value struct V {  
   int m;  
   V(int i) : m(i) {}  
   static operator V(int i) {  
      V v(i*100);  
      return v;  
   }  
};  
  
public ref struct R {  
   int m;  
   R(int i) : m(i) {}  
   static operator R^(int i) {  
      return gcnew R(i*100);  
   }  
};  
  
int main() {  
   V v(13);   // explicit  
   R^ r = gcnew R(12);   // explicit  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
  
   // explicit ctor can't be called here: not ambiguous  
   v = 5;  
   r = 20;  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
}  
```  
  
 **Output**  
  
  **13**  
**12**  
**500**  
**2000**   
## 請參閱  
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)