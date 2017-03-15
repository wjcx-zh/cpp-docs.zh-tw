---
title: "4.4 OMP_NESTED | Microsoft Docs"
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
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.4 OMP_NESTED
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`OMP_NESTED`環境變數啟用或停用巢狀的平行處理原則，除非巢狀的平行處理原則已啟用或停用，藉由呼叫`o`**mp\_set\_nested** 程式庫常式。  如果設定為 \[  **，則為 TRUE**，巢狀的平行處理原則已啟用; 如果設定為 \[  **，則為 FALSE**、 巢狀的平行處理原則已停用。  預設值是 **，則為 FALSE**。  
  
 範例：  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## 交互參照：  
  
-   `omp_set_nested`函式，請參閱[一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 在 40\] 頁面上。