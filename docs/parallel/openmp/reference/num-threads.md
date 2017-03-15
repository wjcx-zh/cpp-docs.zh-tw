---
title: "num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_threads OpenMP clause"
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

設定執行緒小組中的執行緒數目。  
  
## 語法  
  
```  
num_threads(num)  
```  
  
## 備註  
 其中，  
  
 `num`  
 執行緒的數目  
  
## 備註  
 `num_threads`子句有相同的功能[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函式。  
  
 `num_threads`適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## 範例  
 請參閱[parallel](../../../parallel/openmp/reference/parallel.md)的使用範例， `num_threads`子句。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)