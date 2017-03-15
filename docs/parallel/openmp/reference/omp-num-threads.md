---
title: "OMP_NUM_THREADS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_NUM_THREADS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NUM_THREADS OpenMP environment variable"
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在平行區域中，設定執行緒的最大數目，除非藉由覆寫[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num\_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
## 語法  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## 備註  
 其中，  
  
 `num`  
 您想在平行區域中，最多可在 Visual C\+\+ 實作 64 的執行緒最大數目。  
  
## 備註  
 **OMP\_NUM\_THREADS** 可藉由覆寫環境變數[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函式或[num\_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
 預設值為`num`在 Visual C\+\+ 中實作 OpenMP 標準是虛擬處理器，包括超執行緒 Cpu 的數目。  
  
 如需詳細資訊，請參閱 [4.2 OMP\_NUM\_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。  
  
## 範例  
 下列指令集 **OMP\_NUM\_THREADS** 為 16 的環境變數：  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 下列命令會顯示目前設定的 **OMP\_NUM\_THREADS** 環境變數：  
  
```  
set OMP_NUM_THREADS  
```  
  
## 請參閱  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)