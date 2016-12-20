---
title: "編譯器錯誤 C2093 | Microsoft Docs"
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
  - "C2093"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2093"
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2093
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable1' : 不可以使用自動變數 'variable2' 的位址初始化  
  
 在使用 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 編譯時，程式嘗試使用自動變數 \(Automatic Variable\) 位址做為初始設定式。  
  
 下列範例會產生 C2093：  
  
```  
// C2093.c  
// compile with: /Za /c  
void func() {  
   int li;   // an implicit auto variable  
   int * s[]= { &li };   // C2093 address is not a constant  
  
   // OK  
   static int li2;  
   int * s2[]= { &li2 };  
}  
```