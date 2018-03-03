---
title: "使用鎖定 A.16 |Microsoft 文件"
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
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 612abe97de27b179f710b2b09811535829885c5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a16---using-locks"></a>A.16 使用鎖定
在下列範例中，(如[第 3.2 節](../../parallel/openmp/3-2-lock-functions.md)41 頁面上) 鎖定函式的引數必須有型別附註`omp_lock_t`，以及是否有不需要清除它。  鎖定函式會造成執行緒等候第一個關鍵區段的項目處於閒置狀態，但可以執行其他工作，等待第二個項目。  `omp_set_lock`函式區塊，但`omp_test_lock`函式不存在，完成 skip() 中允許的工作。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
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