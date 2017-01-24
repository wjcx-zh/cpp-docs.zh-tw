---
title: "4.2 OMP_NUM_THREADS | Microsoft Docs"
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
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.2 OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_NUM\_THREADS** 環境變數的序列值設定在執行期間，使用執行緒預設數目，除非該數字明確地變更藉由呼叫 **omp\_set\_num\_threads** 程式庫常式或明確 **num\_threads** 上的子句**平行**指示詞。  
  
 值為 **OMP\_NUM\_THREADS** 環境變數必須是正整數。  其效果，取決於是否啟用動態調整執行緒的數目。  為一組完整的規則之間互動之相關 **OMP\_NUM\_THREADS** 環境變數和動態調整執行緒，請參閱網頁 8 2.3 節。  
  
 如果未指定值的 **OMP\_NUM\_THREADS** 環境變數，或如果指定的值不是正整數，或如果值大於最大的系統所支援的執行緒數目，若要使用的執行緒數目是由實作定義。  
  
 範例：  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## 交互參照：  
  
-   **num\_threads** 子句，請參閱 [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。  
  
-   **omp\_set\_num\_threads** 函式，請參閱[一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 在 36\] 頁面上。  
  
-   **omp\_set\_dynamic** 函式，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。