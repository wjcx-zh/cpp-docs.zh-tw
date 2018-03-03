---
title: "使用清單中排清的指示詞 A.13 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6c9d0736-07c2-47b1-a216-5293f03b6397
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da5a7f10abe03364e4de9bdd2bd0258ea8a5e1a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a13---using-the-flush-directive-with-a-list"></a>A.13 使用 flush 指示詞並搭配清單
下列範例會使用`flush`點對點同步處理的執行緒組之間的特定物件的指示詞：  
  
```  
int   sync[NUMBER_OF_THREADS];  
float work[NUMBER_OF_THREADS];  
#pragma omp parallel private(iam,neighbor) shared(work,sync)  
{  
    iam = omp_get_thread_num();  
    sync[iam] = 0;  
    #pragma omp barrier  
  
    // Do computation into my portion of work array   
    work[iam] = ...;  
  
    //  Announce that I am done with my work  
    // The first flush ensures that my work is  
    // made visible before sync.  
    // The second flush ensures that sync is made visible.  
    #pragma omp flush(work)  
    sync[iam] = 1;  
    #pragma omp flush(sync)  
  
    // Wait for neighbor  
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;  
    while (sync[neighbor]==0)   
    {  
        #pragma omp flush(sync)  
    }  
  
    // Read neighbor's values of work array   
    ... = work[neighbor];  
}  
```