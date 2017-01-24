---
title: "2.5.1 parallel for Construct | Microsoft Docs"
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
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5.1 parallel for Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**平行的** 指示詞是以 **平行** 包含只會有一個區域 **的**指示詞。  語法**平行的**指示詞時，如下所示：  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-line  
   for-loop  
```  
  
 這個指示詞可讓所有子句的**平行**指示詞以及**的**指示詞，除非`nowait`子句之後，加上相同的意義和限制。  是要明確指定相同的語意**平行** 指示詞後面緊跟著 **的**指示詞。  
  
## 交互參照：  
  
-   **平行** 指示詞，請參閱  [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8\] 頁面上。  
  
-   **對於** 指示詞，請參閱 [一節 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。  
  
-   資料屬性的子句，請參閱[2.7.2 Data\-Sharing Attribute Clauses](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25\] 頁面上。