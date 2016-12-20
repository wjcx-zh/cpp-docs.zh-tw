---
title: "編譯器警告 (層級 1) C4020 | Microsoft Docs"
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
  - "C4020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4020"
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 實質參數太多  
  
 函式呼叫 \(Function Call\) 中的實質參數個數超過函式原型 \(Prototype\) 或定義的型式參數個數。  編譯器根據此函式的呼叫慣例 \(Calling Convention\) 來傳遞額外的實質參數。  
  
 下列範例會產生 C4020：  
  
```  
// C4020.c  
// compile with: /W1 /c  
void f(int);  
int main() {  
   f(1,2);   // C4020  
}  
```  
  
 可能的解決方案：  
  
```  
// C4020b.c  
// compile with: /c  
void f(int);  
int main() {  
   f(1);  
}  
```