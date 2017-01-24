---
title: "parallel | Microsoft Docs"
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
  - "parallel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parallel OpenMP directive"
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# parallel
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

定義在平行區域，也就是將由多個執行緒同時執行的程式碼。  
  
## 語法  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## 備註  
 其中，  
  
 `clause` \(選擇項\)  
 零個或多個子句。  請參閱 ＜ 備註 ＞ 一節清單所支援的子句的**平行**。  
  
## 備註  
 **平行**指示詞可支援下列 OpenMP 子句：  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num\_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [shared](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **平行**也可與[sections](../../../parallel/openmp/reference/sections-openmp.md)和[for](../../../parallel/openmp/reference/for-openmp.md)指示詞。  
  
 如需詳細資訊，請參閱 [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## 範例  
 下列範例會示範如何設定執行緒數目，以及定義在平行區域。  預設情況下，執行緒的數目等於電腦上的邏輯處理器數目。  比方說，如果您已經有一個已啟用超執行緒的實體處理器的電腦時，會有兩個邏輯處理器，因此，兩個執行緒。  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
  **從執行緒 0 的 hello**  
**從執行緒 1 的 hello**  
**您好，執行緒 2**  
**您好，從執行緒 3**   
## 註解  
 請注意，輸出的順序可能會有所不同不同的電腦。  
  
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)