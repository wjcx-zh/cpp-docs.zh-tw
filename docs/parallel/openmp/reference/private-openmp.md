---
title: "private (OpenMP) | Microsoft Docs"
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
  - "private"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "private OpenMP clause"
ms.assetid: 772904a2-1345-4562-90e6-eb4dc85aea1a
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# private (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定每個執行緒都應該有自己的執行個體的變數。  
  
## 語法  
  
```  
private(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 若要在每個執行緒中有執行個體變數。  
  
## 備註  
 **私用**適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 如需詳細資訊，請參閱 [2.7.2.1 private](../../../parallel/openmp/2-7-2-1-private.md)。  
  
## 範例  
  
```  
// openmp_private.c  
// compile with: /openmp  
#include <windows.h>  
#include <assert.h>  
#include <stdio.h>  
#include <omp.h>  
  
#define NUM_THREADS 4  
#define SLEEP_THREAD 1  
#define NUM_LOOPS 2  
  
enum Types {  
   ThreadPrivate,  
   Private,  
   FirstPrivate,  
   LastPrivate,  
   Shared,  
   MAX_TYPES  
};  
  
int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};  
int nThreadPrivate;  
  
#pragma omp threadprivate(nThreadPrivate)  
#pragma warning(disable:4700)  
  
int main() {  
   int nPrivate = NUM_THREADS;  
   int nFirstPrivate = NUM_THREADS;  
   int nLastPrivate = NUM_THREADS;  
   int nShared = NUM_THREADS;  
   int nRet = 0;  
   int i;  
   int j;  
   int nLoop = 0;  
  
   nThreadPrivate = NUM_THREADS;  
   printf_s("These are the variables before entry "  
           "into the parallel region.\n");  
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);  
   printf_s("      nPrivate = %d\n", nPrivate);  
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);  
   printf_s("  nLastPrivate = %d\n", nLastPrivate);  
   printf_s("       nShared = %d\n\n", nShared);  
   omp_set_num_threads(NUM_THREADS);  
  
   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)  
   {  
      #pragma omp for schedule(static) lastprivate(nLastPrivate)  
      for (i = 0 ; i < NUM_THREADS ; ++i) {  
         for (j = 0 ; j < NUM_LOOPS ; ++j) {  
            int nThread = omp_get_thread_num();  
            assert(nThread < NUM_THREADS);  
  
            if (nThread == SLEEP_THREAD)  
               Sleep(100);  
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;  
            nSave[nThread][Private][j] = nPrivate;  
            nSave[nThread][Shared][j] = nShared;  
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;  
            nSave[nThread][LastPrivate][j] = nLastPrivate;  
            nThreadPrivate = nThread;  
            nPrivate = nThread;  
            nShared = nThread;  
            nLastPrivate = nThread;  
            --nFirstPrivate;  
         }  
      }  
   }  
  
   for (i = 0 ; i < NUM_LOOPS ; ++i) {  
      for (j = 0 ; j < NUM_THREADS ; ++j) {  
         printf_s("These are the variables at entry of "  
                  "loop %d of thread %d.\n", i + 1, j);  
         printf_s("nThreadPrivate = %d\n",  
                  nSave[j][ThreadPrivate][i]);  
         printf_s("      nPrivate = %d\n",  
                  nSave[j][Private][i]);  
         printf_s(" nFirstPrivate = %d\n",  
                  nSave[j][FirstPrivate][i]);  
         printf_s("  nLastPrivate = %d\n",  
                  nSave[j][LastPrivate][i]);  
         printf_s("       nShared = %d\n\n",  
                  nSave[j][Shared][i]);  
      }  
   }  
  
   printf_s("These are the variables after exit from "  
            "the parallel region.\n");  
   printf_s("nThreadPrivate = %d (The last value in the "  
            "master thread)\n", nThreadPrivate);  
   printf_s("      nPrivate = %d (The value prior to "  
            "entering parallel region)\n", nPrivate);  
   printf_s(" nFirstPrivate = %d (The value prior to "  
            "entering parallel region)\n", nFirstPrivate);  
   printf_s("  nLastPrivate = %d (The value from the "  
            "last iteration of the loop)\n", nLastPrivate);  
   printf_s("       nShared = %d (The value assigned, "  
            "from the delayed thread, %d)\n\n",  
            nShared, SLEEP_THREAD);  
}  
```  
  
  **這些都是在平行區域項目之前的變數。  nThreadPrivate \= 4**  
 **nPrivate \= 4**  
 **nFirstPrivate \= 4**  
 **nLastPrivate \= 4**  
 **nShared \= 4**  
**這些都是引線的在迴圈 \(loop\) 1 0 的項目變數。  nThreadPrivate \= 4**  
 **nPrivate \= 1310720**  
 **nFirstPrivate \= 4**  
 **nLastPrivate \= 1245104**  
 **nShared \= 3**  
**這些都是執行緒的在迴圈 \(loop\) 1 1 的項目變數。  nThreadPrivate \= 4**  
 **nPrivate \= 4488**  
 **nFirstPrivate \= 4**  
 **nLastPrivate \= 19748**  
 **nShared \= 0**  
**這些都是在進入迴圈 \(loop\) 1 執行緒 2 的變數。  nThreadPrivate \= 4**  
 **nPrivate \=\-132514848**  
 **nFirstPrivate \= 4**  
 **nLastPrivate \=\-513199792**  
 **nShared \= 4**  
**這些都是在進入迴圈 \(loop\) 1 執行緒 3 的變數。  nThreadPrivate \= 4**  
 **nPrivate \= 1206年**  
 **nFirstPrivate \= 4**  
 **nLastPrivate \= 1204年**  
 **nShared \= 2**  
**這些都是引線的在迴圈 \(loop\) 2 0 的項目變數。  nThreadPrivate \= 0**  
 **nPrivate \= 0**  
 **nFirstPrivate \= 3**  
 **nLastPrivate \= 0**  
 **nShared \= 0**  
**這些都是執行緒的在迴圈 \(loop\) 2 1 的項目變數。  nThreadPrivate \= 1**  
 **nPrivate \= 1**  
 **nFirstPrivate \= 3**  
 **nLastPrivate \= 1**  
 **nShared \= 1**  
**這些都是在進入迴圈 \(loop\) 2 執行緒 2 的變數。  nThreadPrivate \= 2**  
 **nPrivate \= 2**  
 **nFirstPrivate \= 3**  
 **nLastPrivate \= 2**  
 **nShared \= 2**  
**這些都是在進入迴圈 \(loop\) 2 執行緒 3 的變數。  nThreadPrivate \= 3**  
 **nPrivate \= 3**  
 **nFirstPrivate \= 3**  
 **nLastPrivate \= 3**  
 **nShared \= 3**  
**這些是在平行區域從結束之後的變數。  nThreadPrivate \= 0 \(在主執行緒中的最後一個值\)**  
 **nPrivate \= 4 \(值之後再進行輸入平行區域\)**  
 **nFirstPrivate \= 4 \(值之後再進行輸入平行區域\)**  
 **nLastPrivate \= 3 \(從最後一次迴圈重複的值\)**  
 **nShared \= 的 1 \(指定值，從延遲的執行緒 1\)**    
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)