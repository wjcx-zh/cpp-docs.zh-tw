---
title: "編譯器錯誤 C2815 | Microsoft Docs"
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
  - "C2815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2815"
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator delete' : 第一個型式參數必須是 'void \*'，但使用的是 'param'  
  
 任何使用者定義的 [operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md) 函式都必須使用 `void *` 型別做為第一個型式參數。  
  
 下列範例會產生 C2815：  
  
```  
// C2815.cpp  
// compile with: /c  
class CMyClass {  
public:  
   void mf1(int *a);  
   void operator delete(CMyClass *);   // C2815  
   void operator delete(void *);   
};  
```