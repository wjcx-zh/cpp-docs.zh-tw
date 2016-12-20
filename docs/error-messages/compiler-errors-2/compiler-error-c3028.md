---
title: "編譯器錯誤 C3028 | Microsoft Docs"
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
  - "C3028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3028"
ms.assetid: 175e697f-8e8f-492a-8456-6240ffbbb900
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 只有變數或靜態資料成員可以用在資料共用子句中  
  
 傳遞了變數或靜態資料成員以外的符號給簡化子句。  
  
 下列範例會產生 C3028：  
  
```  
// C3028.cpp  
// compile with: /openmp /link vcomps.lib  
int g_i;  
  
class MyClass {  
public:  
   MyClass();  
   MyClass(int x);  
   static int x_public;  
   int mbr;  
private:  
   static int x_private;  
};  
  
int MyClass::x_public;  
int MyClass::x_private;  
  
namespace XyzNS {  
   struct xyz { int x; };  
   xyz xyz;  
}  
  
namespace NS {  
   int a1;  
   struct Bar {  
      static MyClass MyClass;  
   };  
   struct Baz : public Bar {  
      using NS::Bar::MyClass;  
   };  
}  
  
MyClass NS::Bar::MyClass;  
  
typedef int MyInt;  
  
template <class T, size_t n> class CTempl {  
public:  
   static T public_array[n];  
private:  
   static T private_array[n];  
};  
  
template<class T,size_t n> T CTempl<T,n>::public_array[n];  
template<class T,size_t n> T CTempl<T,n>::private_array[n];  
  
CTempl<int,5> tx;  
  
struct Incomplete;  
extern Incomplete inc;  
  
MyClass::MyClass(int x) {  
  
   #pragma omp parallel reduction(+: x, g_i, x_public, x_private)     
   // OK  
      ;  
  
   #pragma omp parallel reduction(+: x, g_i, MyClass::x_public,   
   MyClass::x_private)     
   // OK  
      ;  
  
   #pragma omp parallel reduction(+: mbr)     
   // C3028, member of a class.  
      ;  
}  
  
int main() {  
  
   #pragma omp parallel reduction(+:main)     
   // C3028, main is a function.  
      ;  
  
   #pragma omp parallel reduction(+: XyzNS)     
   // C3028, XyzNS is a namespace.  
      ;  
}  
```