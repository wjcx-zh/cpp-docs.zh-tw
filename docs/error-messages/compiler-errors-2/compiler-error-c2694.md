---
title: "編譯器錯誤 C2694 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2694"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2694"
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2694
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override': 基底類別虛擬成員函式 'base' 的例外狀況規格比覆寫虛擬函式的嚴格  
  
 虛擬函式已遭覆寫，但在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，覆寫函式的[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)較不嚴格。  
  
 下列範例會產生 C2694：  
  
```  
// C2694.cpp  
// compile with: /Za /c  
class MyBase {  
public:  
   virtual void f(void) throw(int) {  
   }  
};  
  
class Derived : public MyBase {  
public:  
   void f(void) throw(...) {}   // C2694  
   void f2(void) throw(int) {}   // OK  
};  
```