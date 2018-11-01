---
title: A.16 使用鎖定
ms.date: 11/04/2016
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
ms.openlocfilehash: 6afb94660acdc79ea5a7eb61d3bf7e21fd70d751
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458977"
---
# <a name="a16---using-locks"></a>A.16 使用鎖定

在下列範例中，(如[第 3.2 節](../../parallel/openmp/3-2-lock-functions.md)41 頁上) 的鎖定函式的引數應該有型別附註`omp_lock_t`，以及是否有要排清它不需要。  鎖定函式會造成執行緒等候第一個重要區段中，項目處於閒置狀態，但執行其他工作在等候第二個項目時。  `omp_set_lock`函式區塊，但`omp_test_lock`函式不是，不允許在 skip （） 進行的工作。

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