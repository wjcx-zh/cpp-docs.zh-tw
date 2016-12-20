---
title: "編譯器錯誤 C3035 | Microsoft Docs"
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
  - "C3035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3035"
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP 'ordered' 指示詞必須與 'ordered' 子句一起直接繫結到 'for' 或 'parallel for' 指示詞  
  
 已排序的子句格式錯誤。  
  
 下列範例會產生 C3035：  
  
```  
// C3035.cpp // compile with: /openmp /link vcomps.lib int main() { int n = 0, x, i; #pragma omp parallel private(n) { #pragma omp ordered   // C3035 // Try the following line instead: // #pragma omp for ordered for (i = 0 ; i < 10 ; ++i) ; } }  
```