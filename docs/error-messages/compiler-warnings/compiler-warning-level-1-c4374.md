---
title: "編譯器警告 (層級 1) C4374 | Microsoft Docs"
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
  - "C4374"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4374"
ms.assetid: 4ac9aaec-d815-4b6e-825f-fa872092dd3b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4374
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function1' : 介面方法將無法由非虛擬方法 'function2' 實作  
  
 編譯器預期在方法定義中找到 [virtual](../../cpp/virtual-specifier.md) 關鍵字。  
  
 下列範例會產生 C4374：  
  
```  
// C4374.cpp  
// compile with: /clr /W1 /c /WX  
public interface class I {  
   void f();  
};  
  
public ref struct B {  
   void f() {  
      System::Console::WriteLine("B::f()");  
   }  
};  
  
public ref struct C {  
   virtual void f() {  
      System::Console::WriteLine("C::f()");  
   }  
};  
  
public ref struct D : B, I {};   // C4374  
public ref struct E : C, I {};   // OK  
```