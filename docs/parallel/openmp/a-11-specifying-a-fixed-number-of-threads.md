---
title: "A.11   Specifying a Fixed Number of Threads | Microsoft Docs"
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
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.11   Specifying a Fixed Number of Threads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有些程式會依賴固定、 預先指定的執行緒數目才能正確執行。  動態調整執行緒數目的預設設定是由實作環境，因為這類程式可以選擇關閉動態的執行緒功能，並設定明確地以確保可攜性的執行緒數目。  下列範例會示範如何執行這項操作使用`omp_set_dynamic` \([區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39\] 頁面上\)，以及`omp_set_num_threads` \([區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 在 36\] 頁面上\)：  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 在這個範例中，程式會 16 的執行緒執行它時，才正確執行。  如果實作就不支援 16 的執行緒，此範例的行為是由實作定義。  
  
 請注意，執行在平行區域的執行緒數目在平行區域，不論動態設定的執行緒時保持不變。  動態執行緒機制可以決定要使用平行區域的開頭的執行緒數量，而且它仍保持固定區域的持續期間。