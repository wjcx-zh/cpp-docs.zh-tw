---
title: "編譯器錯誤 C3723 | Microsoft Docs"
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
  - "C3723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3723"
ms.assetid: ef0fb1ff-3f9a-4093-a6b6-894d1ab0c4b9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 無法解析事件  
  
 `function` 無法解析要呼叫的事件。  
  
 下列範例會產生 C3723：  
  
```  
// C3723.cpp  
struct A {  
   // To resolve, comment void f(int); and uncomment the __event function  
   void f(int);  
   // __event void f(int);  
   void f(float);  
  
};  
  
struct B {  
   void g(int);  
   B(A* a) {  
   __hook(&A::f, a, &B::g);   // C3723  
   }  
};  
  
int main() {  
}  
```  
  
 `__hook` 和 `__unhook` 與 \/clr 程式設計不相容。請改用 \+\= 和 \-\= 運算子。  
  
 下列範例會產生 C3723：  
  
```  
// C3723b.cpp  
// compile with: /clr  
using namespace System;  
  
public delegate void delegate1();  
  
public ref class CPSource {  
public:  
   event delegate1^ event1;  
};  
  
public ref class CReceiver {  
public:  
   void Handler1() {  
   }  
  
   void UnhookAll(CPSource^ pSrc) {  
      __unhook(&CPSource::event1, pSrc, &CReceiver::Handler1); // C3723  
      // Try the following line instead.  
      // pSrc->event1 -= gcnew delegate1(this, &CReceiver::Handler1);  
   }  
};  
  
int main() {  
}  
```