---
title: "3.1.3 omp_get_max_threads Function | Microsoft Docs"
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
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.3 omp_get_max_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_get\_max\_threads** 函式傳回一個整數，保證至少會用來形成一個團隊，如果沒有在平行區域的執行緒數目一樣大 **num\_threads** 子句是要在程式碼中遇到該點。  格式如下：  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 下列的值表示的最小值 **omp\_get\_max\_threads**：  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 請注意，如果在後續的平行區域會使用 **num\_threads** 子句來要求特定數目的執行緒上的最小值的結果保證 **omp\_get\_max\_threads** 沒有長的存放。  
  
 **Omp\_get\_max\_threads** 函式的傳回值可以用來動態配置足夠的儲存空間，在後續的平行區域所組成的小組中的所有執行緒。  
  
## 交互參照：  
  
-   **omp\_get\_num\_threads** 函式，請參閱[一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 在 37\] 頁面上。  
  
-   **omp\_set\_num\_threads** 函式，請參閱[一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 在 36\] 頁面上。  
  
-   **omp\_set\_dynamic** 函式，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。  
  
-   **num\_threads** 子句，請參閱 [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。