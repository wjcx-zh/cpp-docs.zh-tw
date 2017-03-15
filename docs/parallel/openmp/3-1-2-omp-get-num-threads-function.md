---
title: "3.1.2 omp_get_num_threads Function | Microsoft Docs"
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
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.2 omp_get_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_get\_num\_threads** 函式會傳回執行緒的數目目前小組執行平行從中呼叫它的區域中。  格式如下：  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 **Num\_threads** 子句中，  **omp\_set\_num\_threads** 函式，以及 **OMP\_NUM\_THREADS** 環境變數控制小組中的執行緒數目。  
  
 如果使用者有沒有被明確設定的執行緒數目，預設值是由實作定義。  這個函式繫結至最接近的封入**平行**指示詞。  如果呼叫從序列一部分的程式，或從已序列化的巢狀的平行區域，這個函式會傳回 1。  
  
## 交互參照：  
  
-   **OMP\_NUM\_THREADS** 環境變數，請參閱[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 在 48\] 頁面上。  
  
-   **num\_threads** 子句，請參閱 [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。  
  
-   **平行** 建構，請參閱  [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。