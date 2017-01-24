---
title: "編譯器錯誤 C3014 | Microsoft Docs"
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
  - "C3014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3014"
ms.assetid: af1c5b0c-dbf9-4274-b06a-c6c2cdcf2a52
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP 'directive' 指示詞後面應該跟著 for 迴圈  
  
 除 `for` 迴圈緊接 `#pragma omp for` 指示詞以外，其他全是錯誤。  
  
 下列範例會產生 C3014：  
  
```  
// C3014.cpp // compile with: /openmp int main() { int i = 0; #pragma omp parallel { #pragma omp for for (i = 0; i < 10; ++i)   // OK { } } #pragma omp parallel for for (i = 0; i < 10; ++i)   // OK { } #pragma omp parallel { #pragma omp for {   // C3014 for (i = 0; i < 10; ++i) { } } } #pragma omp parallel for {   // C3014 for (i = 0; i < 10; ++i) { } } #pragma omp parallel { #pragma omp for i *= 2;   // C3014 for (i = 0; i < 10; ++i) { } } #pragma omp parallel for i *= 2;   // C3014 for (i = 0; i < 10; ++i) { } }  
```