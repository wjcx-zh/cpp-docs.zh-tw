---
title: "3.1.9 omp_set_nested Function | Microsoft Docs"
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
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.9 omp_set_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_set\_nested** 函式啟用或停用巢狀的平行處理原則。  格式如下：  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 如果*巢狀*會評估為 0，巢狀化平行處理原則已停用，這是預設值，並序列化和目前的執行緒執行的巢狀的平行區域。  如果*巢狀*會評估為非零的值，巢狀的平行處理原則啟用，巢狀的平行區域可以部署額外的執行緒，以形成巢狀的小組。  
  
 這個函式具有前文所述，從程式的一部分呼叫時的效果，  **omp\_in\_parallel** 函式會傳回零。  如果從程式的一部分呼叫，  **omp\_in\_parallel** 函數會傳回非零值，這個函式的行為是未定義。  
  
 這個呼叫的優先順序必高於 **OMP\_NESTED** 環境變數。  
  
 巢狀的平行處理原則啟用時，用來執行巢狀的平行區域的執行緒數目是由實作定義。  如此一來，OpenMP 相容的實作允許序列化巢狀的平行區域，即使在巢狀的平行處理原則已啟用。  
  
## 交互參照：  
  
-   **OMP\_NESTED** 環境變數，請參閱 [4.4 節](../../parallel/openmp/4-4-omp-nested.md)在 49\] 頁面上。  
  
-   **omp\_in\_parallel** 函式，請參閱[一節 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 在頁面上 38。