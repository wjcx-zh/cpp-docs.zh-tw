---
title: "編譯器錯誤 C3040 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3040"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3040"
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3040
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': 'reduction' 子句中的變數類型與削減運算子 'operator' 不相容  
  
 [reduction](../../parallel/openmp/reference/reduction.md) 子句中的變數不能和削減運算子一起使用。  
  
 下列範例會產生 C3040：  
  
```  
// C3040.cpp // compile with: /openmp /c #include "omp.h" double d; int main() { #pragma omp parallel reduction(&:d)   // C3040 ; #pragma omp parallel reduction(-:d)  // OK ; }  
```