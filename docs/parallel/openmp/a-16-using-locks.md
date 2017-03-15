---
title: "A.16   Using Locks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.16   Using Locks
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在下列範例中，\(如[區段 3.2](../../parallel/openmp/3-2-lock-functions.md) 在頁面上 41\) 鎖定函式的引數必須具有型別附註 `omp_lock_t`，並沒有必要清除它。  鎖定函式會造成執行緒在等待第一的關鍵區段的項目處於閒置狀態，但同時等候第二個項目執行其他工作。  `omp_set_lock`函式區塊，但`omp_test_lock`函式則否，讓工作在 skip\(\) 進行中。  
  
## 範例  
  
### 程式碼  
  
```  
// omp_using_locks.c  
// compile with: /openmp /c  
#include <stdio.h>  
#include <omp.h>  
  
void work(int);  
void skip(int);  
  
int main() {  
   omp_lock_t lck;  
   int id;  
  
   omp_init_lock(&lck);  
   #pragma omp parallel shared(lck) private(id)  
   {  
      id = omp_get_thread_num();  
  
      omp_set_lock(&lck);  
      printf_s("My thread id is %d.\n", id);  
  
      // only one thread at a time can execute this printf  
      omp_unset_lock(&lck);  
  
      while (! omp_test_lock(&lck)) {  
         skip(id);   // we do not yet have the lock,  
                     // so we must do something else   
      }  
      work(id);     // we now have the lock  
                    // and can do the work   
      omp_unset_lock(&lck);  
   }  
   omp_destroy_lock(&lck);  
}  
```