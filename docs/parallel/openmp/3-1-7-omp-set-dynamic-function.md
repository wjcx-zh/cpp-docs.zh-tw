---
title: "3.1.7 omp_set_dynamic Function | Microsoft Docs"
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
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.7 omp_set_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_set\_dynamic** 函式啟用或停用動態調整執行緒可供執行平行區域的數目。  格式如下：  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 如果 *dynamic\_threads* 會評估為非零的值，用於執行後續的平行區域的執行緒數目可能會自動調整以執行階段環境，利用系統資源。  因此，根據使用者指定的執行緒數目是執行緒計數上限。  在執行平行區域小組中的執行緒數目平行該段期間會保持固定和報告的 **omp\_get\_num\_threads** 函式。  
  
 如果 *dynamic\_threads* 會評估為 0，停用動態調整。  
  
 這個函式具有前文所述，從程式的一部分呼叫時的效果，  **omp\_in\_parallel** 函式會傳回零。  如果從程式的一部分呼叫，  **omp\_in\_parallel** 函數會傳回非零值，這個函式的行為是未定義。  
  
 呼叫 **omp\_set\_dynamic** 的優先順序必高於 **OMP\_DYNAMIC** 環境變數。  
  
 動態調整執行緒的預設值是由實作定義。  如此一來，取決於特定的正確執行的執行緒數目的使用者程式碼應該明確停用動態的執行緒。  實作並不需要提供動態調整執行緒數目，但它們必須提供介面以支援跨所有平台的可攜性。  
  
## 交互參照：  
  
-   **omp\_get\_num\_threads** 函式，請參閱[一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 在 37\] 頁面上。  
  
-   **OMP\_DYNAMIC** 環境變數，請參閱 [4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)在 49\] 頁面上。  
  
-   **omp\_in\_parallel** 函式，請參閱[一節 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 在頁面上 38。