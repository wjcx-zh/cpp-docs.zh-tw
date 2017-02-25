---
title: "編譯器錯誤 C2577 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2577"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2577"
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2577
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : destructor\/finalizer 不可以有傳回型別  
  
 解構函式或完成項不能傳回 `void` 值或任何其他型別。  將 `return` 陳述式從解構函式定義上移除。  
  
## 範例  
 下列範例會產生 C2577。  
  
```  
// C2577.cpp  
// compile with: /c  
class A {  
public:  
   A() {}  
   ~A(){  
      return 0;   // C2577  
   }  
};  
```