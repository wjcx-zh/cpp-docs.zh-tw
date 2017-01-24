---
title: "A.8   Specifying Parallel Sections | Microsoft Docs"
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
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.8   Specifying Parallel Sections
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在下列範例中，\(如[章節 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) 在 14\] 頁面上\) 函式 *xaxis*，  *yaxis*，以及  *zaxis* 可同時執行。  第一個`section`指示詞是選擇性的。  請注意，所有`section`指示詞必須出現在語彙範圍的`parallel``sections`建構。  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```