---
title: "編譯器錯誤 C2325 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2325"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2325"
ms.assetid: e6b0a186-3f2a-4adf-beae-fadd75492bf7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2325
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 'name' 的右邊出現未預期的型別  
  
 呼叫不正確型別的解構函式。  
  
 下列範例會產生 C2325：  
  
```  
// C2325.cpp  
// compile with: /c  
class A {};  
typedef A* pA_t;  
void f() {  
    A** ppa = new A *;  
    ppa->~A*;   // C2325  
  
   pA_t *ppa2 = new pA_t;  
   ppa2->~pA_t();   // OK  
}  
```