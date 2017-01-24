---
title: "編譯器錯誤 C3166 | Microsoft Docs"
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
  - "C3166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3166"
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'pointer' : 不可以將指向內部 \_\_gc 指標的指標宣告為 'type' 的成員  
  
 編譯器發現一個無效的指標宣告 \(指向 [\_\_gc](../../misc/gc.md) 指標的 [\_\_nogc](../../misc/nogc.md) 指標\)。  未來發行版本中可能會支援這種語法。  
  
 C3166 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3166：  
  
```  
// C3166.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct G {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __gc class H {  
public:  
   Int32 __gc* __nogc* p;   // C3166  
};  
  
public __value struct I {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __value class J {  
public:  
   int __gc* __nogc* p;   // C3166  
};  
  
int main() {  
   G* pG = new G;  
   H* pH = new H;  
}  
```