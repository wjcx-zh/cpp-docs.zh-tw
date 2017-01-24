---
title: "A.3   Using Parallel Regions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.3   Using Parallel Regions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`parallel`指示詞 \([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在頁面上 8\) 可用於粗略粒狀資料單位的平行處理程式。  在下列範例中，每個執行緒在平行區域決定全域陣列的哪個部分`x` ，處理執行緒的數字為基礎：  
  
```  
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)  
{  
    iam = omp_get_thread_num();  
    np =  omp_get_num_threads();  
    ipoints = npoints / np;  
    subdomain(x, iam, ipoints);  
}  
```