---
title: "master | Microsoft Docs"
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
  - "master"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "master OpenMP directive"
ms.assetid: 559ed974-e02a-486e-a23f-31556429b2c4
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# master
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定只有主版的 threadshould 執行程式的一個區段。  
  
## 語法  
  
```  
#pragma omp master  
{  
   code_block  
}  
```  
  
## 備註  
 **主要**指示詞可支援任何 OpenMP 子句。  
  
 [single](../../../parallel/openmp/reference/single.md)指示詞可讓您指定一段程式碼應該會在單一執行緒，不一定是主執行緒上執行。  
  
 如需詳細資訊，請參閱 [2.6.1 master Construct](../../../parallel/openmp/2-6-1-master-construct.md)。  
  
## 範例  
  
```  
// omp_master.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
  
int main( )   
{  
    int a[5], i;  
  
    #pragma omp parallel  
    {  
        // Perform some computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] = i * i;  
  
        // Print intermediate results.  
        #pragma omp master  
            for (i = 0; i < 5; i++)  
                printf_s("a[%d] = %d\n", i, a[i]);  
  
        // Wait.  
        #pragma omp barrier  
  
        // Continue with the computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] += i;  
    }  
}  
```  
  
  **\[0\] \= 0**  
**\[1\] \= 1**  
**\[2\] \= 4**  
**\[3\] \= 9**  
**\[4\] \= 16**   
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)