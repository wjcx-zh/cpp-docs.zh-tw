---
title: "編譯器錯誤 C2540 | Microsoft Docs"
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
  - "C2540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2540"
ms.assetid: 92c805a3-2dd9-46ca-a63d-3845c18ecc95
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非常數運算式當做陣列界限  
  
 陣列必須有常數的界限。  
  
 下列範例會產生 C2540：  
  
```  
// C2540.cpp  
void func(int n, int pC[]) {  
   int i = ((int [n])pC)[1];   // C2540  
}  
  
void func2(int n, int pC[]) {  
   int i = (pC)[1];   // OK  
}  
  
int main() {  
   int pC[100];  
   func(100, pC);  
   func2(100, pC);  
}  
```