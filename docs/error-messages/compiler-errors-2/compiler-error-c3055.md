---
title: "編譯器錯誤 C3055 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3055"
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 符號必須先使用在 'threadprivate' 指示詞中，然後才能夠被參考  
  
 符號已被參考並接著用於 [threadprivate](../../parallel/openmp/reference/threadprivate.md) 子句中，這不是允許的做法。  
  
 下列範例會產生 C3055：  
  
```  
// C3055.cpp // compile with: /openmp int x, y; int z = x; #pragma omp threadprivate(x, y)   // C3055 void test() { #pragma omp parallel copyin(x, y) { x = y; } }  
```  
  
 可能的解決方式：  
  
```  
// C3055b.cpp // compile with: /openmp /LD int x, y, z; #pragma omp threadprivate(x, y) void test() { #pragma omp parallel copyin(x, y) { x = y; } }  
```