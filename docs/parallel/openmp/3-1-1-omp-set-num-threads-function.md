---
title: "3.1.1 omp_set_num_threads Function | Microsoft Docs"
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
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.1 omp_set_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_set_num_threads`函式會設定預設的執行緒數目来用於後續的平行區域未指定`num_threads`子句。  格式如下：  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 參數值 *num\_threads* 必須是正整數。  其效果，取決於是否啟用動態調整執行緒的數目。  為一組完整的規則之間互動之相關`omp_set_num_threads`函式，並動態調整執行緒，在 8\] 頁面上，請參閱 2.3 節。  
  
 這個函式具有前文所述，從程式的一部分呼叫時的效果， `omp_in_parallel`函式會傳回零。  如果從程式的一部分呼叫， `omp_in_parallel`函數會傳回非零值，這個函式的行為是未定義。  
  
 這個呼叫的優先順序必高於`OMP_NUM_THREADS`環境變數。  預設值，可能會藉由呼叫建立的執行緒數目的`omp_set_num_threads`或藉由設定`OMP_NUM_THREADS`環境變數，可明確地覆寫單一**平行**指示詞指定`num_threads`子句。  
  
## 交互參照：  
  
-   `omp_set_dynamic`函式，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。  
  
-   `omp_get_dynamic`函式，請參閱[一節 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) 在 40\] 頁面上。  
  
-   `OMP_NUM_THREADS`環境變數，請參閱[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 頁面 48，以及在頁面上 8 2.3 節。  
  
-   `num_threads`子句中，請參閱 [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在頁面上 8