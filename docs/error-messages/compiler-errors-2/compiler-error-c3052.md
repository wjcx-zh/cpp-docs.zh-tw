---
title: "編譯器錯誤 C3052 | Microsoft Docs"
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
  - "C3052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3052"
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 變數未出現在 default\(none\) 子句下的資料共用子句中  
  
 如果使用了 [default\(none\)](../../parallel/openmp/reference/default-openmp.md)，任何用在結構化區塊中的變數都必須明確地指定為 [shared](../../parallel/openmp/reference/shared-openmp.md) 或 [private](../../parallel/openmp/reference/private-openmp.md)。  
  
 下列範例會產生 C3052：  
  
```  
// C3052.cpp // compile with: /openmp /c int main() { int n1 = 1; #pragma omp parallel default(none) // shared(n1) private(n1) { n1 = 0;   // C3052 use either a shared or private clause } }  
```