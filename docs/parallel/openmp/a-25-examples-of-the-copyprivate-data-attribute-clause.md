---
title: "A.25   Examples of the copyprivate Data Attribute Clause | Microsoft Docs"
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
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.25   Examples of the copyprivate Data Attribute Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**範例 1：** `copyprivate`子句 \([一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) 在 32\] 頁面上\) 可以用來廣播由單一執行緒直接於另一個執行緒的私用變數的所有執行個體所取得的值。  
  
```  
float x, y;  
#pragma omp threadprivate(x, y)  
  
void init( )   
{  
    float a;  
    float b;  
  
    #pragma omp single copyprivate(a,b,x,y)  
    {  
        get_values(a,b,x,y);  
    }  
  
    use_values(a, b, x, y);  
}  
```  
  
 如果例行*初始化*呼叫序列的區域，其行為不會受到指示詞的目前狀態。  若要在呼叫之後 *get\_values* 常式皆執行一個執行緒，沒有執行緒離開之前所指定的私用物件的建構 ，  *b*，  *x*，和  *y* 所有的執行緒中有定義變得有讀取的值。  
  
 **範例 2：** 相對於前一個範例中，假設 \[讀取必須由特定的執行緒，說出的主執行緒。  如此一來， `copyprivate`子句不能用來直接進行廣播，但是它可以用來提供暫時的共用物件的存取權。  
  
```  
float read_next( )   
{  
    float * tmp;  
    float return_val;  
  
    #pragma omp single copyprivate(tmp)  
    {  
        tmp = (float *) malloc(sizeof(float));  
    }  
  
    #pragma omp master  
    {  
        get_float( tmp );  
    }  
  
    #pragma omp barrier  
    return_val = *tmp;  
    #pragma omp barrier  
  
    #pragma omp single  
    {  
       free(tmp);  
    }  
  
    return return_val;  
}  
```  
  
 **範例 3：** 假設放在平行區域內所需的鎖定物件的數目不容易判斷才能輸入。  `copyprivate`子句可以用來提供該平行區域內所配置的共用的鎖定物件的存取權。  
  
```  
#include <omp.h>  
  
omp_lock_t *new_lock()  
{  
    omp_lock_t *lock_ptr;  
  
    #pragma omp single copyprivate(lock_ptr)  
    {  
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));  
        omp_init_lock( lock_ptr );  
    }  
  
    return lock_ptr;  
}  
```