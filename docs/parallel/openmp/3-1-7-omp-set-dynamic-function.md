---
title: 3.1.7 omp_set_dynamic 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1e22a1eb9aff32bfaf07350daf1cb397e18eb3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函式
**Omp_set_dynamic**函式啟用或停用動態調整可用的平行區域執行的執行緒數目。 格式如下：  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 如果*dynamic_threads*評估為非零值，執行後續的平行區域所使用的執行緒數目可能會自動調整執行階段環境充分利用系統資源。 因此，使用者所指定的執行緒數目是最大執行緒計數。 執行平行區域小組中的執行緒數目平行該段期間會保持固定，以及所報告**omp_get_num_threads**函式。  
  
 如果*dynamic_threads*判斷值為 0，已停用動態調整。  
  
 此函式可從程式的一部分呼叫時，上面所述的效果其中**omp_in_parallel**函式會傳回零。 如果從程式的一部分呼叫其中**omp_in_parallel**函式會傳回非零值，這個函式的行為是未定義。  
  
 呼叫**omp_set_dynamic**的優先順序高於**OMP_DYNAMIC**環境變數。  
  
 動態調整的執行緒的預設值是由實作定義。 如此一來，使用者程式碼相依於特定數目的執行緒正確執行應該明確地停用動態執行緒。 實作不需要提供了可動態調整執行緒數目，但必須是為了可攜性支援所有平台提供的介面。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **omp_get_num_threads**函式，請參閱[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上。  
  
-   **OMP_DYNAMIC**環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。  
  
-   **omp_in_parallel**函式，請參閱[區段 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)在 38 頁面上。