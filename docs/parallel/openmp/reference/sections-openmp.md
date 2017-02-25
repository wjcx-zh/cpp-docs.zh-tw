---
title: "sections (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "section"
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sections OpenMP directive"
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# sections (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

識別分割為所有的執行緒之間的程式碼區段。  
  
## 語法  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## 備註  
 其中，  
  
 `clause` \(選擇項\)  
 零個或多個子句。  請參閱 ＜ 備註 ＞ 一節清單所支援的子句的**章節**。  
  
## 備註  
 **章節** 指示詞可以包含零或更多 **一節**指示詞。  
  
 **章節**指示詞可支援下列 OpenMP 子句：  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 如果**平行**指定了， `clause`可以任何子句所接受**平行**或**章節**指示詞，除非`nowait`。  
  
 如需詳細資訊，請參閱 [2.4.2 sections Construct](../../../parallel/openmp/2-4-2-sections-construct.md)。  
  
## 範例  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
  **從執行緒 0 的 hello**  
**從執行緒 0 的 hello**   
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)