---
title: "編譯器錯誤 C3627 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3627"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3627"
ms.assetid: 905ad0a0-8c49-4187-b66e-b375f5a1fae5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3627
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有實值型別可以執行 box 的動作  
  
 只有數值類別可被 Box。  
  
 下列範例會產生 C3627：  
  
```  
// C3627.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value class vA {  
};  
  
__gc class A {  
};  
  
int main()  
{  
   A* a;  
   __box(a);   // C3627  
  
   // box a value type  
   vA va;  
   __box(va);  
}  
```