---
title: "3.1.3 omp_get_max_threads 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e021f0873aa94f53a1218a3278a744a0c7740e65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函式
**Omp_get_max_threads**函式傳回一個整數，保證至少會用來組成一個小組，如果沒有在平行區域的執行緒數目一樣大**num_threads**子句即將此時所發現的程式碼中。 格式如下：  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 下列的值表示下限**omp_get_max_threads**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 請注意，如果在後續的平行區域使用**num_threads**子句來要求特定數目的執行緒上下限的結果保證**omp_get_max_threads**任何長的保留。  
  
 **Omp_get_max_threads**函式的傳回值可用來動態配置足夠的儲存體小組格式在後續的平行區域中的所有執行緒。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **omp_get_num_threads**函式，請參閱[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上。  
  
-   **omp_set_num_threads**函式，請參閱[區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。  
  
-   **omp_set_dynamic**函式，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。  
  
-   **num_threads**子句，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上。