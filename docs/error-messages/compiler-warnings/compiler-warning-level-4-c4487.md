---
title: "編譯器警告 (層級 4) C4487 | Microsoft Docs"
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
  - "C4487"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4487"
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4487
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'derived\_class\_function' : 符合繼承的非虛擬方法 'base\_class\_function'，但未明確標記為 'new'  
  
 衍生類別中的函式具有與非虛擬基底類別函式相同的簽章。  C4487 是提醒您，衍生類別函式不會覆寫基底類別函式。  請明確地將衍生類別標記為 `new`，以解除這項警告。  
  
 如需詳細資訊，請參閱[new \(new slot in vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4487。  
  
```  
// C4487.cpp  
// compile with: /W4 /clr  
using namespace System;  
public ref struct B {  
   void f() { Console::WriteLine("in B::f"); }  
   void g() { Console::WriteLine("in B::g"); }  
};  
  
public ref struct D : B {  
   void f() { Console::WriteLine("in D::f"); }   // C4487  
   void g() new { Console::WriteLine("in D::g"); }   // OK  
};  
  
int main() {  
   B ^ a = gcnew D;  
   // will call base class functions  
   a->f();  
   a->g();  
}  
```