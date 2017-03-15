---
title: "omp_init_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_init_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_init_lock OpenMP function"
ms.assetid: 7a65e3e2-2e31-4645-964c-c1e82e2a4d0e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# omp_init_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

初始化簡單的鎖定。  
  
## 語法  
  
```  
void omp_init_lock(  
   omp_lock_t *lock  
);  
```  
  
#### 參數  
 `lock`  
 型別的變數[omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md)。  
  
## 備註  
 如需詳細資訊，請參閱 [3.2.1 omp\_init\_lock and omp\_init\_nest\_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。  
  
## 範例  
  
```  
// omp_init_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_lock_t my_lock;  
  
int main() {  
   omp_init_lock(&my_lock);  
  
   #pragma omp parallel num_threads(4)  
   {  
      int tid = omp_get_thread_num( );  
      int i, j;  
  
      for (i = 0; i < 5; ++i) {  
         omp_set_lock(&my_lock);  
         printf_s("Thread %d - starting locked region\n", tid);  
         printf_s("Thread %d - ending locked region\n", tid);  
         omp_unset_lock(&my_lock);  
      }  
   }  
  
   omp_destroy_lock(&my_lock);  
}  
```  
  
  **0\-正在啟動的執行緒鎖定區域**  
**0\-結束鎖定的執行緒 \(地區\)**  
**0\-正在啟動的執行緒鎖定區域**  
**0\-結束鎖定的執行緒 \(地區\)**  
**0\-正在啟動的執行緒鎖定區域**  
**0\-結束鎖定的執行緒 \(地區\)**  
**0\-正在啟動的執行緒鎖定區域**  
**0\-結束鎖定的執行緒 \(地區\)**  
**0\-正在啟動的執行緒鎖定區域**  
**0\-結束鎖定的執行緒 \(地區\)**  
**執行緒 1\-正在啟動鎖定區域**  
**執行緒 1\-結束鎖定區域**  
**執行緒 1\-正在啟動鎖定區域**  
**執行緒 1\-結束鎖定區域**  
**執行緒 1\-正在啟動鎖定區域**  
**執行緒 1\-結束鎖定區域**  
**執行緒 1\-正在啟動鎖定區域**  
**執行緒 1\-結束鎖定區域**  
**執行緒 1\-正在啟動鎖定區域**  
**執行緒 1\-結束鎖定區域**  
**執行緒 2\-正在啟動鎖定區域**  
**執行緒 2\-結束鎖定區域**  
**執行緒 2\-正在啟動鎖定區域**  
**執行緒 2\-結束鎖定區域**  
**執行緒 2\-正在啟動鎖定區域**  
**執行緒 2\-結束鎖定區域**  
**執行緒 2\-正在啟動鎖定區域**  
**執行緒 2\-結束鎖定區域**  
**執行緒 2\-正在啟動鎖定區域**  
**執行緒 2\-結束鎖定區域**  
**3\-正在啟動的執行緒鎖定區域**  
**鎖定的執行緒 3\-結束 \(地區\)**  
**3\-正在啟動的執行緒鎖定區域**  
**鎖定的執行緒 3\-結束 \(地區\)**  
**3\-正在啟動的執行緒鎖定區域**  
**鎖定的執行緒 3\-結束 \(地區\)**  
**3\-正在啟動的執行緒鎖定區域**  
**鎖定的執行緒 3\-結束 \(地區\)**  
**3\-正在啟動的執行緒鎖定區域**  
**鎖定的執行緒 3\-結束 \(地區\)**   
## 請參閱  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)