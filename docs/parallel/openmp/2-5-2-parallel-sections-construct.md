---
title: "2.5.2 parallel sections Construct | Microsoft Docs"
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
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5.2 parallel sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**平行章節** 指示詞會提供指定的快顯表單 **平行** 包含只會有一個區域 **章節**指示詞。  是要明確指定相同的語意**平行** 指示詞後面緊跟著 **章節**指示詞。  語法**平行章節**指示詞時，如下所示：  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block  ]  
   ...  
}  
```  
  
 *子句* 可接受的子句內 **平行** 和 **章節** 指示詞，除非  **\[不等待**子句。  
  
## 交互參照：  
  
-   **平行** 指示詞，請參閱  [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。  
  
-   **章節** 指示詞，請參閱 [章節 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) 在 14\] 頁面上。