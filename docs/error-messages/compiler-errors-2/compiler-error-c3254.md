---
title: "編譯器錯誤 C3254 | Microsoft Docs"
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
  - "C3254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3254"
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'explicit override' : 雖然在類別中已含有明確覆寫 'override'，但不是從含有函式宣告的介面衍生而來  
  
 當您[明確覆寫](../../cpp/explicit-overrides-cpp.md)方法時，包含覆寫的類別必須直接或間接衍生自包含您所覆寫的函式之型別。  
  
 下列範例會產生 C3254：  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```