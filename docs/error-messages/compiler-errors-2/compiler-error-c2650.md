---
title: "編譯器錯誤 C2650 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2650"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2650"
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C2650
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 不可為虛擬函式  
  
 `new` 或 `delete` 運算子是宣告為 `virtual`。  這些運算子是 `static` 成員函式，而不能為 `virtual`。  
  
## 範例  
 下列範例會產生 C2650：  
  
```  
// C2650.cpp  
// compile with: /c  
class A {  
   virtual void* operator new( unsigned int );   // C2650  
   // try the following line instead  
   // void* operator new( unsigned int );  
};  
```