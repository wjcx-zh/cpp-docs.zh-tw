---
title: "A.12   Using the atomic Directive | Microsoft Docs"
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
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.12   Using the atomic Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例會避免競爭情形 \(同時更新中項目的 *x* 由多個執行緒\) 藉由使用`atomic`指示詞 \([區段 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) 在 19\] 頁面上\)：  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 使用的優點`atomic`指示詞，在本例中是可讓兩個不同的項目 x 平行發生的更新。  如果`critical`指示詞 \([區段 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) 18\] 頁面上\) 所有更新的項目則相反地，使用 *x* 就會執行，以序列方式 \(雖然不在任何保證順序\)。  
  
 請注意， `atomic`指示詞只能套用於緊接它的 c 或 C\+\+ 的陳述式。  因此，項目 *y* 不會在這個範例會以原子方式更新。