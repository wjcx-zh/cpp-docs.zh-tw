---
title: OpenMP 函式 |Microsoft Docs
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
ms.openlocfilehash: a5daa7737f63df437f31f349a85811befe0c8f5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425596"
---
# <a name="openmp-functions"></a>OpenMP 函式

提供在 OpenMP API 中使用的函式連結。

Visual c + + 實作的 openmp 標準包含下列函式。

|功能|描述|
|--------------|-----------------|
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|未初始化的鎖定。|
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|取消初始化可巢狀鎖定。|
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|傳回值，這個值，指出是否可以調整執行階段在後續的平行區域中可用的執行緒數目。|
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|傳回一個整數，等於或大於會時才可用在平行區域，而不需要的執行緒數目[num_threads](../../../parallel/openmp/reference/num-threads.md)此時程式碼中定義。|
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|傳回值，這個值，指出是否已啟用巢狀平行處理原則。|
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|傳回可在呼叫函式的處理器數目。|
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|傳回平行的區域中的執行緒數目。|
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|傳回其執行緒小組內的執行緒執行執行緒的數目。|
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|傳回處理器時鐘刻度之間的秒數。|
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|傳回值，以秒為單位的時間之間所經歷的某個時間點。|
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|傳回非零值，如果從在平行區域內呼叫。|
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化簡單的鎖定。|
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化的鎖定。|
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|指出可以調整的執行階段的後續的平行區域中可用的執行緒數目。|
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|啟用巢狀平行處理原則。|
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在後續的平行區域，設定執行緒數目，但覆寫[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。|
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|嘗試設定鎖定，但不會封鎖執行緒的執行。|
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|嘗試設定可巢狀鎖定，但不會封鎖執行緒的執行。|
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|釋放鎖定。|
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|釋出可巢狀鎖定。|

## <a name="see-also"></a>另請參閱

[程式庫參考](../../../parallel/openmp/reference/openmp-library-reference.md)