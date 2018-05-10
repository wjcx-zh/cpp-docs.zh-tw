---
title: OpenMP 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-functions"></a>OpenMP 函式
提供用於 OpenMP API 函式的連結。  
  
 OpenMP 標準的 Visual c + + 實作會包含下列功能。  
  
|功能|描述|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|未初始化的鎖定。|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|未初始化可巢狀的鎖定。|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|傳回值，指出是否可以調整執行階段的後續平行區域中的可用執行緒數目。|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|傳回一個整數，等於或大於此數目，就可以使用，如果沒有在平行區域的執行緒數目[num_threads](../../../parallel/openmp/reference/num-threads.md)在該點定義在程式碼中。|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|傳回值，指出是否已啟用巢狀平行處理原則。|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|傳回函式呼叫時的可用處理器的數目。|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|在平行區域傳回執行緒的數目。|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|傳回其執行緒小組內的執行緒執行的執行緒數目。|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|傳回處理器時脈週期之間的秒數。|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|傳回從某個時間點所經過時間的秒鐘值。|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|傳回非零，如果是從呼叫的平行區域內。|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化簡單鎖定。|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化的鎖定。|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|指出可以調整的執行階段的後續平行區域中的可用執行緒數目。|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|區塊執行緒執行，直到鎖定可用為止。|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|區塊執行緒執行，直到鎖定可用為止。|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|啟用巢狀平行處理原則。|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在後續的平行區域，設定執行緒的數目，除非被[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|嘗試設定鎖定，但不會封鎖執行緒的執行。|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|嘗試設定可巢狀的鎖定，但不會封鎖執行緒的執行。|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|釋放鎖定。|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|釋出可巢狀的鎖定。|  
  
## <a name="see-also"></a>另請參閱  
 [程式庫參考](../../../parallel/openmp/reference/openmp-library-reference.md)