---
title: 4.2 OMP_NUM_THREADS
ms.date: 11/04/2016
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
ms.openlocfilehash: 88ddfc226b8ae905e026e2f0979e07581d1ae83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668204"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

**OMP_NUM_THREADS**環境變數設定預設要在執行期間，所使用的執行緒數目，除非明確呼叫變更該數字**omp_set_num_threads**程式庫常式或藉由明確**num_threads**子句**平行**指示詞。

值**OMP_NUM_THREADS**環境變數必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動**OMP_NUM_THREADS**環境變數和動態調整的執行緒，請參閱第 8 頁 2.3 節。

如果未不指定任何值，如**OMP_NUM_THREADS**環境變數，或如果指定的值不是正整數，或如果值大於最大執行緒數目，系統可以支援，要使用的執行緒數目是由實作定義。

範例：

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>交叉參考：

- **num_threads**子句，請參閱 < [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。

- **omp_set_num_threads**函式，請參閱 <<c2> [ 一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。

- **omp_set_dynamic**函式，請參閱 <<c2> [ 一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。