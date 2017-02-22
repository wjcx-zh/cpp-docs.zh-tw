---
title: "omp_set_num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_num_threads OpenMP function"
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# omp_set_num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在後續的平行區域，設定執行緒數目，除非藉由覆寫[num\_threads](../../../parallel/openmp/reference/num-threads.md)子句。  
  
## 語法  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## 備註  
 其中，  
  
 `num_threads`  
 在平行區域中的執行緒數目。  
  
## 備註  
 如需詳細資訊，請參閱 [3.1.1 omp\_set\_num\_threads Function](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。  
  
## 範例  
 請參閱[omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)的使用範例， `omp_set_num_threads`。  
  
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)