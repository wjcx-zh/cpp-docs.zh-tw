---
title: "A.5   Using the critical Directive | Microsoft Docs"
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
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.5   Using the critical Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例包含數個`critical`指示詞 \([一節 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) 18\] 頁面上\)。  本範例會示範一項工作是從佇列取出並處理佇列的模型。  若要防止多個執行緒取消佇列，相同的工作，清除佇列的操作必須在`critical`一節。  在這個範例中的兩個佇列都是獨立的因為受到`critical`指示詞，以不同名稱、  *xaxis* 和 *yaxis*。  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```