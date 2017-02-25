---
title: "omp_get_num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_num_threads OpenMP function"
ms.assetid: e7c3cea1-44ac-435d-866e-2b7bc477e807
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# omp_get_num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

傳回在平行區域中的執行緒數目。  
  
## 語法  
  
```  
int omp_get_num_threads( );  
```  
  
## 備註  
 如需詳細資訊，請參閱 [3.1.2 omp\_get\_num\_threads Function](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)。  
  
## 範例  
  
```  
// omp_get_num_threads.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()  
{  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_num_threads( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_num_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_num_threads( ));  
  
    #pragma omp parallel num_threads(3)  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_num_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_num_threads( ));  
}  
```  
  
  **1**  
**4**  
**1**  
**3**  
**1**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)