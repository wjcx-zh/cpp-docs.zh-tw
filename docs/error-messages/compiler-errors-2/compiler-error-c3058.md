---
title: "編譯器錯誤 C3058 | Microsoft Docs"
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
  - "C3058"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3058"
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3058
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol'：符號使用在 'copyin' 子句之前未宣告為 'threadprivate'  
  
 必須先將符號宣告為 [threadprivate](../../parallel/openmp/reference/threadprivate.md)，才能用於 [copyin](../../parallel/openmp/reference/copyin.md) 子句。  
  
 下列範例會產生 C3058：  
  
```  
// C3058.cpp // compile with: /openmp int x, y, z; #pragma omp threadprivate(x, z) void test() { #pragma omp parallel copyin(x, y)   // C3058 { } }  
```  
  
 可能的解決方式：  
  
```  
// C3058b.cpp // compile with: /openmp /LD int x, y, z; #pragma omp threadprivate(x, y) void test() { #pragma omp parallel copyin(x, y) { } }  
```