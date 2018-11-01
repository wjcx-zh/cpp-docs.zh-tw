---
title: A.25 copyprivate 資料屬性子句範例
ms.date: 11/04/2016
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
ms.openlocfilehash: 6c3c174780023f17cc2aa47a54bff14fccf99306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493882"
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25 copyprivate 資料屬性子句範例

**範例 1︰** `copyprivate`子句 ([一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)上 32) 可用來廣播由單一執行緒直接在其他執行緒的私用變數的所有執行個體所取得的值。

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

如果是例行*init*稱為從序列的區域，其行為不會影響是否存在指示詞。 若要在呼叫之後*get_values*常式已執行一個執行緒，沒有任何執行緒所指定的私用物件之前離開建構， *b*， *x*，並*y*所有執行緒中變成以定義讀取的值。

**範例 2:** 相較於先前的範例，假設讀取只能由特定的執行緒，假設主要執行緒。 在此情況下，`copyprivate`子句不能直接進行廣播，但它可以用來提供暫時的共用物件的存取權。

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

**範例 3︰** 假設在平行區域內所需的鎖定物件的數目不容易判斷之前輸入它。 `copyprivate`子句可以用來提供配置該平行區域內的共用的鎖定物件的存取權。

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