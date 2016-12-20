---
title: "編譯器警告 (層級 1) C4803 | Microsoft Docs"
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
  - "C4803"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4803"
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4803
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method' : 產生的方法具有與該事件的 'event' 不同的儲存類別  
  
 事件方法與事件宣告必須有相同的儲存類別。  編譯器會調整事件方法，使儲存類別相同。  
  
 如果有自介面實作事件的類別，可能會發生此警告。  編譯器不會在介面中明確地為事件產生引發方法。  當您在類別中實作介面時，編譯器會明確地產生引發方法，而且該方法不是虛擬的，因此警告產生。  
  
 如需關於如何關閉警告的資訊，請參閱 [warning](../../preprocessor/warning.md) pragma。  
  
## 範例  
 使用 **\/clr** 可能會產生 C4803。  如需使用事件的詳細資訊，請參閱 [event](../../windows/event-cpp-component-extensions.md)。  
  
 下列範例會產生 C4803。  
  
```  
// C4803.cpp  
// compile with: /clr /W1  
using namespace System;  
  
public delegate void Del();  
  
ref struct E {  
   Del ^ _pd1;  
   event Del ^ E1 {  
      void add (Del ^ pd1) {  
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));  
      }  
  
      void remove(Del^ pd1) {  
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));  
      }  
  
      virtual void raise() {   // C4803 warning (remove virtual)  
         if (_pd1)  
            _pd1();  
      }  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E ^ ep = gcnew E;  
   ep->E1 += gcnew Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= gcnew Del(ep, &E::func);  
   ep->E1();  
}  
```  
  
## 範例  
 使用 **\/clr:oldSyntax** 也可以產生 C4803。  下列範例會產生 C4803。  
  
```  
// C4803_b.cpp  
// compile with: /clr:oldSyntax /W1  
using namespace System;  
  
public __delegate void Del();  
  
__gc struct E {  
   Del* _pd1;  
   virtual __event void add_E1(Del* pd1) {  
      _pd1 = dynamic_cast<Del*> (Delegate::Combine(_pd1, pd1));  
   }  
  
   virtual __event void remove_E1(Del* pd1) {  
      _pd1 = dynamic_cast<Del*> (Delegate::Remove(_pd1, pd1));  
   }  
  
   __event void raise_E1 () {   // C4803, add virtual  
      if (_pd1)  
         _pd1->Invoke();  
   }  
  
   void func() {  
      Console::WriteLine("In E::func()");  
   }  
};  
  
int main() {  
   E* ep = new E;  
   ep->E1 += new Del(ep, &E::func);  
   ep->E1();  
   ep->E1 -= new Del(ep, &E::func);  
   ep->E1();  
}  
```