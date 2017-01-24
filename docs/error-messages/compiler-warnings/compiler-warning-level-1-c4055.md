---
title: "編譯器警告 (層級 1) C4055 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4055"
ms.assetid: f04b13ca-88a7-4f2b-8065-42e73e5ac353
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversion': 從資料指標 'type1' 到函式指標 'type2'  
  
 資料指標轉型 \(可能不正確\) 成函式指標。 這在 \/Za 下是層級 1 警告，在 \/Ze 下是層級 4 警告。  
  
 下列範例會產生 C4055：  
  
```  
// C4055.c // compile with: /Za /W1 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```  
  
 這在 \/Ze 下是層級 4 警告。  
  
```  
// C4055b.c // compile with: /W4 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```