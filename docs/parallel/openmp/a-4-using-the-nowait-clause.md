---
title: "A.4   Using the nowait Clause | Microsoft Docs"
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
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.4   Using the nowait Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果有多個獨立的迴圈放在平行區域內，您可以使用`nowait`子句 \([區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上\) 以避免隱含的障盾結尾的`for`指示詞，如下所示：  
  
```  
#pragma omp parallel  
{  
    #pragma omp for nowait  
        for (i=1; i<n; i++)  
             b[i] = (a[i] + a[i-1]) / 2.0;  
    #pragma omp for nowait  
        for (i=0; i<m; i++)  
            y[i] = sqrt(z[i]);  
}  
```