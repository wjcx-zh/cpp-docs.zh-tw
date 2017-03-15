---
title: "for (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for OpenMP directive"
ms.assetid: 8b54e034-9db2-4c1a-a2b1-72e14e930506
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# for (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

使完成的工作執行緒之間分割為在平行區域內的迴圈。  
  
## 語法  
  
```  
#pragma omp [parallel] for [clauses]  
   for_statement  
```  
  
## 備註  
 其中，  
  
 `clause` \(選擇項\)  
 零個或多個子句。  請參閱 ＜ 備註 ＞ 一節清單所支援的子句的**的**。  
  
 `for_statement`  
 答： for 迴圈。  如果使用者的程式碼，就會產生未定義的行為迴圈變成 index 變數。  
  
## 備註  
 **的**指示詞可支援下列 OpenMP 子句：  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [&#91;不等待](../../../parallel/openmp/reference/nowait.md)  
  
-   [排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [縮小](../../../parallel/openmp/reference/reduction.md)  
  
-   [排程](../../../parallel/openmp/reference/schedule.md)  
  
 如果**平行**指定了， `clause`可以任何子句所接受**平行**或**的**指示詞，除非 **\[不等待**。  
  
 如需詳細資訊，請參閱 [2.4.1 建構](../../../parallel/openmp/2-4-1-for-construct.md)。  
  
## 範例  
  
```  
// omp_for.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <math.h>  
#include <omp.h>  
  
#define NUM_THREADS 4  
#define NUM_START 1  
#define NUM_END 10  
  
int main() {  
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;  
   int nThreads = 0, nTmp = nStart + nEnd;  
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *   
                               unsigned(abs(nTmp))) / 2;  
   int nSumCalc = uTmp;  
  
   if (nTmp < 0)  
      nSumCalc = -nSumCalc;  
  
   omp_set_num_threads(NUM_THREADS);  
  
   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)  
   {  
      #pragma omp master  
      nThreads = omp_get_num_threads();  
  
      #pragma omp for  
      for (i=nStart; i<=nEnd; ++i) {  
            #pragma omp atomic  
            nSum += i;  
      }  
   }  
  
   if  (nThreads == NUM_THREADS) {  
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);  
      nRet = 0;  
   }  
   else {  
      printf_s("Expected %d OpenMP threads, but %d were used.\n",  
               NUM_THREADS, nThreads);  
      nRet = 1;  
   }  
  
   if (nSum != nSumCalc) {  
      printf_s("The sum of %d through %d should be %d, "  
               "but %d was reported!\n",  
               NUM_START, NUM_END, nSumCalc, nSum);  
      nRet = 1;  
   }  
   else  
      printf_s("The sum of %d through %d is %d\n",  
               NUM_START, NUM_END, nSum);  
}  
```  
  
  **4 OpenMP 執行緒所使用。  1 到 10 的總和是 55**    
## 請參閱  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)