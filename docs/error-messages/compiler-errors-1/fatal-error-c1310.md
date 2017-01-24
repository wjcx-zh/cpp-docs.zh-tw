---
title: "嚴重錯誤 C1310 | Microsoft Docs"
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
  - "C1310"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1310"
ms.assetid: ac48aa51-8023-42fe-b844-3f8bf228fbef
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1310
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

特性指引最佳化不適用於 OpenMP  
  
 您不能使用 [\/LTCG:PGI](../../build/reference/ltcg-link-time-code-generation.md) 連結任何以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯的模組。  
  
 下列範例會產生 C1310：  
  
```  
// C1310.cpp // compile with: /openmp /GL /link /LTCG:PGI // C1310 expected int main() { int i = 0, j = 10; #pragma omp parallel { #pragma omp for for (i = 0; i < 0; i++) --j; } }  
```