---
title: "編譯器錯誤 C3017 | Microsoft Docs"
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
  - "C3017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3017"
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP 'for' 陳述式中的終止測試格式不當  
  
 OpenMP 陳述式中的 `for` 迴圈必須完整且明確地指定。  
  
 下列範例會產生 C3017：  
  
```  
// C3017.cpp // compile with: /openmp int main() { int i = 0, j = 10; #pragma omp parallel { #pragma omp for for (i = 0; i; ++i)   // C3017 // Try the following line instead: // for (i = 0; i < 10; ++i) ; } }  
```