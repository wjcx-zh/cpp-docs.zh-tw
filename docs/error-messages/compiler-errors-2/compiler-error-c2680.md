---
title: "編譯器錯誤 C2680 | Microsoft Docs"
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
  - "C2680"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2680"
ms.assetid: d6f7129e-dd17-4661-b680-18d6b925b1cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2680
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : name 的目標型別無效  
  
 轉型 \(Casting\) 運算子嘗試轉換成不是指標或參考的型別。  [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 運算子只供指標或參考使用。  
  
 下列範例會產生 C2680：  
  
```  
// C2680.cpp  
// compile with: /c  
class A { virtual void f(); };  
class B : public A {};  
  
void g(B b) {  
   A a;  
   a = dynamic_cast<A>(b);   // C2680  target not a reference type  
   a = dynamic_cast<A&>(b);   // OK  
}  
```  
  
 未定義目標時，也可能會發生 C2680。  
  
```  
// C2680b.cpp  
// compile with: /clr /c  
// C2680 expected  
using namespace System::Collections;  
  
// Delete the following line to resolve.  
ref class A;   // not defined  
  
// Uncomment the following line to resolve.  
// ref class A{};  
  
public ref class B : ArrayList {  
   property A^ C[int] {  
      A^ get(int index) {  
         return dynamic_cast<A^>(this->default::get(index));  
      }  
      void set(int index, A^ value) {  
         this->default::set(index, value);   
      }  
   }  
};  
```