---
title: "編譯器錯誤 C3010 | Microsoft Docs"
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
  - "C3010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3010"
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'label' : 不允許跳出 OpenMP 結構化區塊  
  
 程式碼不能跳入或跳出 OpenMP 區塊。  
  
 下列範例會產生 C3010：  
  
```  
// C3010.c // compile with: /openmp int main() { #pragma omp parallel { #pragma omp parallel { goto lbl3; } } lbl3:;   // C3010 }  
```