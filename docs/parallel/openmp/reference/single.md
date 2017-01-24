---
title: "single | Microsoft Docs"
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
  - "Single"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single OpenMP directive"
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# single
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

讓您指定一段程式碼應該會在單一執行緒，不一定是主執行緒上執行。  
  
## 語法  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### 參數  
 `clause` \(選擇項\)  
 零個或多個子句。  請參閱 ＜ 備註 ＞ 一節清單所支援的子句的**單一**。  
  
## 備註  
 **單一**指示詞可支援下列 OpenMP 子句：  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 [master](../../../parallel/openmp/reference/master.md)指示詞可讓您指定一段程式碼應該只在主執行緒上執行。  
  
 如需詳細資訊，請參閱 [2.4.3 single Construct](../../../parallel/openmp/2-4-3-single-construct.md)。  
  
## 範例  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
  **讀取輸入**  
**計算結果**  
**計算結果**  
**寫入輸出**   
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)