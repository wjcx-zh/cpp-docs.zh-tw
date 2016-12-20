---
title: "omp_set_dynamic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_dynamic OpenMP function"
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_set_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示執行階段可以調整後續的平行區域中可用的執行緒數量。  
  
## 語法  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## 備註  
 其中，  
  
 `val`  
 值，指出是否可以由執行階段調整後續的平行區域中可用的執行緒數量。  如果不為零，執行階段可以調整執行緒數目，如果是零，執行階段會動態調整執行緒數目。  
  
## 備註  
 執行緒數目，將不會超過所設定的值[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)。  
  
 使用[omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)以顯示目前設定的`omp_set_dynamic`。  
  
 將`omp_set_dynamic`將會覆寫的設定值[OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)環境變數。  
  
 如需詳細資訊，請參閱 [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## 範例  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
  **1**  
**1**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)