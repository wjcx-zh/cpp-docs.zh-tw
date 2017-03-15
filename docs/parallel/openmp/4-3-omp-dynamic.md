---
title: "4.3 OMP_DYNAMIC | Microsoft Docs"
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
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.3 OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_DYNAMIC** 環境變數啟用或停用動態調整執行緒可供執行平行的區域數目，除非明確地啟用或停用呼叫動態調整 **omp\_set\_dynamic** 程式庫常式。  其值必須是 **，則為 TRUE** 或 **，則為 FALSE**。  
  
 如果設定為 \[  **，則為 TRUE**，用於執行平行區域的執行緒數目可加以調整，以執行階段環境，利用系統資源。  如果設定為 \[  **，則為 FALSE**，動態調整已停用。  預設情況是由實作定義。  
  
 範例：  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## 交互參照：  
  
-   如需有關平行區域的詳細資訊，請參閱 [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。  
  
-   **omp\_set\_dynamic** 函式，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。