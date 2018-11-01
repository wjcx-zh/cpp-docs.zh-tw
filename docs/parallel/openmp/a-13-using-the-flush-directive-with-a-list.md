---
title: A.13 使用 flush 指示詞並搭配清單
ms.date: 11/04/2016
ms.assetid: 6c9d0736-07c2-47b1-a216-5293f03b6397
ms.openlocfilehash: 8decdf0f7495c381037f2aa4c51e707ddc738d94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664070"
---
# <a name="a13---using-the-flush-directive-with-a-list"></a>A.13 使用 flush 指示詞並搭配清單

下列範例會使用`flush`點對點同步處理的執行緒配對之間的特定物件的指示詞：

```
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```