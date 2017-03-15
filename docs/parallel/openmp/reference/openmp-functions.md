---
title: "OpenMP Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Functions
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供用於 OpenMP API 函式的連結。  
  
 Visual C\+\+ 實作標準 OpenMP 包括下列功能。  
  
|Function|描述|  
|--------------|--------|  
|[omp\_destroy\_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|未初始化鎖定。|  
|[omp\_destroy\_nest\_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|未初始化的 nestable 鎖定。|  
|[omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|傳回值，指出是否執行階段可以調整後續的平行區域中可用的執行緒數量。|  
|[omp\_get\_max\_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|傳回一個整數，等於或大於應該是儲備如果不需要在平行區域的執行緒數目[num\_threads](../../../parallel/openmp/reference/num-threads.md)已在該點定義程式碼中。|  
|[omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md)|傳回值，指出是否已啟用巢狀的平行處理原則。|  
|[omp\_get\_num\_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|傳回時，可以使用這個函數被呼叫的處理器數目。|  
|[omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|傳回在平行區域中的執行緒數目。|  
|[omp\_get\_thread\_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|傳回其執行緒小組中的執行緒執行的執行緒數目。|  
|[omp\_get\_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|傳回處理器的時脈週期之間的秒數。|  
|[omp\_get\_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|傳回某個時間點之間所經歷的時間 \(秒\) 值。|  
|[omp\_in\_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|傳回非零值，如果在平行區域中呼叫。|  
|[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化簡單的鎖定。|  
|[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化鎖定。|  
|[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|表示執行階段可以調整後續的平行區域中可用的執行緒數量。|  
|[omp\_set\_lock](../../../parallel/openmp/reference/omp-set-lock.md)|封鎖執行緒執行，直到鎖定可用為止。|  
|[omp\_set\_nest\_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|封鎖執行緒執行，直到鎖定可用為止。|  
|[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)|可讓巢狀的平行處理。|  
|[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在後續的平行區域，設定執行緒數目，除非藉由覆寫[num\_threads](../../../parallel/openmp/reference/num-threads.md)子句。|  
|[omp\_test\_lock](../../../parallel/openmp/reference/omp-test-lock.md)|嘗試設定鎖定，但不會封鎖執行緒的執行。|  
|[omp\_test\_nest\_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|嘗試設定 nestable 的鎖定，但不會封鎖執行緒的執行。|  
|[omp\_unset\_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|釋放鎖定。|  
|[omp\_unset\_nest\_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|釋出 nestable 的鎖定。|  
  
## 請參閱  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)