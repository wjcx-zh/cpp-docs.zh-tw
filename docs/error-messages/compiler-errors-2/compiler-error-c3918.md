---
title: "編譯器錯誤 C3918 | Microsoft Docs"
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
  - "C3918"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3918"
ms.assetid: a8b3a90a-3fe1-4244-a5ff-a31cdae97d98
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3918
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用方式必須有 'member' 才能成為資料成員  
  
 C3918 會因與事件相關的幾種原因而產生。  
  
## 範例  
 C3918 可能會因為類別成員需要在目前的內容中而產生。  下列範例會產生 C3918。  
  
```  
// C3918.cpp  
// compile with: /clr /c  
public ref class C {  
public:  
   System::Object ^ o;  
   delegate void Del();  
  
   event Del^ MyEvent {  
      void add(Del^ev) {  
         if ( MyEvent != nullptr) {}   // C3918  
         if ( o != nullptr) {}   // OK  
   }  
   void remove(Del^){}  
   }  
};  
```  
  
## 範例  
 如果您嘗試檢查 null 的 trivial 事件 \(事件名稱無法再提供直接存取至該事件的支援存放區委派\)，也可能會產生 C3918。  
  
 下列範例會產生 C3918。  
  
```  
// C3918_2.cpp  
// compile with: /clr /c  
using namespace System;  
public delegate int MyDel(int);  
  
interface struct IEFace {  
   event MyDel ^ E;  
};  
  
ref struct EventSource : public IEFace {  
   virtual event MyDel ^ E;  
   void Fire_E(int i) {  
      if (E)   // C3918  
         E(i);  
   }  
};  
```  
  
## 範例  
 如果您不正確地訂閱了事件，也可能會發生 C3918。  下列範例會產生 C3918。  
  
```  
// C3918_3.cpp  
// compile with: /clr /c  
using namespace System;  
  
public delegate void del();  
  
public ref class A {  
public:  
   event del^ e {  
      void add(del ^handler ) {  
         d += handler;  
      }  
  
      void remove(del ^handler) {  
         d -= handler;  
      }  
  
      void raise() {   
         d();  
      }  
   }  
  
   del^ d;  
   void f() {}  
  
   A() {  
      e = gcnew del(this, &A::f);   // C3918  
      // try the following line instead  
      // e += gcnew del(this, &A::f);  
      e();  
   }  
};  
  
int main() {  
   A a;  
}  
```