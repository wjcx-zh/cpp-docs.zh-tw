---
title: "omp_get_max_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_max_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_max_threads OpenMP function"
ms.assetid: f47c3725-3e40-469f-8bc8-a1e47f264cc3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# omp_get_max_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

傳回一個整數，等於或大於應該是儲備如果不需要在平行區域的執行緒數目[num\_threads](../../../parallel/openmp/reference/num-threads.md)已在該點定義程式碼中。  
  
## 語法  
  
```  
int omp_get_max_threads( )  
```  
  
## 備註  
 如需詳細資訊，請參閱 [3.1.3 omp\_get\_max\_threads Function](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。  
  
## 範例  
  
```  
// omp_get_max_threads.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_num_threads(8);  
    printf_s("%d\n", omp_get_max_threads( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
  
    #pragma omp parallel num_threads(3)  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
}  
```  
  
  **8**  
**8**  
**8**  
**8**  
**8**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)