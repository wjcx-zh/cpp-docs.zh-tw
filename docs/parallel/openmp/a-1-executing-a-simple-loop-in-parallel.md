---
title: "A.1   Executing a Simple Loop in Parallel | Microsoft Docs"
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
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.1   Executing a Simple Loop in Parallel
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例示範如何使用平行處理簡單的迴圈，使用`parallel for`指示詞 \([一節 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) 在頁面上 16\)。  迴圈反覆運算變數是預設的情況下，私用的因此並不需要明確指定私用的子句中。  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```