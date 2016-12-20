---
title: "編譯器錯誤 C2845 | Microsoft Docs"
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
  - "C2845"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2845"
ms.assetid: 31b28ee9-978f-403b-94d8-dbaacd24cce0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2845
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 這個型別上不允許指標算術  
  
 您不能遞增指向 Managed 類別的指標。  
  
 **Managed Extensions for C\+\+**  
  
 您不能遞增指向 [\_\_gc](../../misc/gc.md) 類別的指標。而且，字串運算子只有用 **\/clr** 才有效 \(不是 **\/clr:oldSyntax**\)。  
  
 下列範例會產生 C2845：  
  
```  
// C2845b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class X {};  
  
int main() {  
   X *pX = new X;  
   pX++;   // C2845  
  
   String * a = new String("abc");  
   String * b = new String("def");  
   Console::WriteLine(a + b);   // C2845 not with /clr:oldSyntax  
}  
```