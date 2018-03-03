---
title: "Copyprivate Data 屬性子句 A.25 範例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cdf7598e00bab72966fe79454567b0a59dcbaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25 copyprivate 資料屬性子句範例
**範例 1:** `copyprivate`子句 ([區段 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)在頁面上 32) 可用來廣播由單一執行緒直接私用變數中的其他執行緒的所有執行個體所取得的值。  
  
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
  
 如果常式*init*稱為序列的區域，其行為不會受到指示詞是否存在。 若要在呼叫之後*get_values*常式由一個執行緒已執行、 沒有執行緒保留之前所指定的私用物件建構， *b*， *x*，和*y*中所有執行緒變成定義讀取的值。  
  
 **範例 2:**相較於上述範例中，假設讀取必須由特定的執行緒，假設主要執行緒執行。 在此情況下，`copyprivate`子句不能直接執行廣播，但是它可以用來提供存取權是共用的暫存物件。  
  
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
  
 **範例 3:**假設在平行區域內所需的鎖定物件的數目不容易判斷之前輸入它。 `copyprivate`子句可以用來提供共用的鎖定物件所配置的平行區域內的存取權。  
  
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