---
title: A.28 使用 num_threads 子句
ms.date: 11/04/2016
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
ms.openlocfilehash: 99dd327d0a97f561107ffaa6a6ed1435e3772a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492270"
---
# <a name="a28---use-of-numthreads-clause"></a>A.28 使用 num_threads 子句

下列範例示範`num_threads`子句 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)上第 8 頁)。 平行區域最多 10 個執行緒的執行。

```
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```