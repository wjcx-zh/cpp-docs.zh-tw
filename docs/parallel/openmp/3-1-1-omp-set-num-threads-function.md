---
title: 3.1.1 omp_set_num_threads 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99c82ff324cbf21612d2459511877d152e2757f5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688436"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函式
`omp_set_num_threads`函式會將預設要用於後續的平行區域未指定的執行緒數目`num_threads`子句。 格式如下：  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 參數的值*num_threads*必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動有關`omp_set_num_threads`函式和動態調整的執行緒，在 8 頁面上看到 2.3 節。  
  
 此函式可從程式的一部分呼叫時，上面所述的效果其中`omp_in_parallel`函式會傳回零。 如果從程式的一部分呼叫其中`omp_in_parallel`函式會傳回非零值，這個函式的行為是未定義。  
  
 這個呼叫的優先順序高於`OMP_NUM_THREADS`環境變數。 可能藉由呼叫建立的執行緒數目的預設值`omp_set_num_threads`或藉由設定`OMP_NUM_THREADS`環境變數，可以明確覆寫單一**平行**藉由指定指示詞`num_threads`子句。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   `omp_set_dynamic` 函式，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。  
  
-   `omp_get_dynamic` 函式，請參閱[區段 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md)在 40 頁面上。  
  
-   `OMP_NUM_THREADS` 環境變數，請參閱[區段 4.2](../../parallel/openmp/4-2-omp-num-threads.md)頁面 48，及區段 2.3 8 頁上。  
  
-   `num_threads` 子句中，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上