---
title: 4.2 OMP_NUM_THREADS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6b4208d7fe7d453dd1f701d820a85fce5cd68ba
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
**OMP_NUM_THREADS**環境變數設定預設在執行期間，所使用的執行緒數目，除非明確地變更該數字藉由呼叫**omp_set_num_threads**程式庫常式或明確**num_threads**子句**平行**指示詞。  
  
 值**OMP_NUM_THREADS**環境變數必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動有關**OMP_NUM_THREADS**環境變數和動態調整的執行緒，請參閱區段 2.3 8 頁。  
  
 如果未不指定任何值，如**OMP_NUM_THREADS**環境變數，或如果指定的值不是正整數，或如果值大於最大執行緒數目系統可以支援，要使用的執行緒數目是由實作定義。  
  
 範例：  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **num_threads**子句，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上。  
  
-   **omp_set_num_threads**函式，請參閱[區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。  
  
-   **omp_set_dynamic**函式，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。