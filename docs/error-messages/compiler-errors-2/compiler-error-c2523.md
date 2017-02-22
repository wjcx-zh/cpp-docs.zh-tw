---
title: "編譯器錯誤 C2523 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2523"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2523"
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2523
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::~identifier' : destructor\/finalizer 標記不相符  
  
 解構函式的名稱必須是以否定號 \(`~`\) 開始的類別名稱。  建構函式和解構函式是唯一和類別名稱相同的成員。  
  
 下列範例會產生 C2523：  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```