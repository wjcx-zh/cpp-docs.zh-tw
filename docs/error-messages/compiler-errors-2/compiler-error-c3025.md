---
title: "編譯器錯誤 C3025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3025"
ms.assetid: 4442f5a3-d9ea-4873-b1fb-e7e5bd3cbe5e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clause': 需要整數運算式  
  
 子句需要整數運算式，但提供的是非整數運算式。  
  
## 範例  
 下列範例會產生 C3025。  
  
```  
// C3025.cpp // compile with: /openmp /link vcomps.lib #include <stdio.h> #include "omp.h" float f = 2.0F; int main() { int i = 0; // OK puts("Test with int"); #pragma omp parallel for num_threads(i) for (i = 1; i <= 2; ++i) printf_s("Hello World - thread %d - iteration %d\n", omp_get_thread_num(), i); puts("Test with float"); #pragma omp parallel for num_threads(f)   // C3025 for (i = 1; i <= 2; ++i) printf_s("Hello World - thread %d - iteration %d\n", omp_get_thread_num(), i); }  
```