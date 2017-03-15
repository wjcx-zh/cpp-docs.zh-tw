---
title: "A.15   Determining the Number of Threads Used | Microsoft Docs"
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
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.15   Determining the Number of Threads Used
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

請假想下列不正確 \(如[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 在 37\] 頁面上\)：  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 `omp_get_num_threads()`序列\] 部分的程式碼中呼叫傳回 1，所以*非分頁* \= 1 在前面的範例。  如果要判斷要部署的平行區域的執行緒數目，呼叫應該在平行區域內。  
  
 下列範例會示範如何重新寫入這個程式，但不包括查詢的執行緒數目:  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```