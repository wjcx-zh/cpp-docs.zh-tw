---
title: 3.1.1 omp_set_num_threads 函式
ms.date: 11/04/2016
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
ms.openlocfilehash: 20b6b6ced2b4031696f1d019604842ae9b91bda2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663277"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函式

`omp_set_num_threads`函式會設定要用於後續的平行區域不會指定執行緒的預設數目`num_threads`子句。 格式如下：

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads*必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動有關`omp_set_num_threads`函式，並動態調整的執行緒，請參閱第 8 頁 2.3 節。

此函式已從程式的一部分呼叫時，上面所述的效果，`omp_in_parallel`函式會傳回零。 如果呼叫程式的一部分，`omp_in_parallel`函式會傳回非零值，這個函式的行為是未定義。

這個呼叫的優先順序高於`OMP_NUM_THREADS`環境變數。 可能會藉由呼叫建立的執行緒數目的預設值`omp_set_num_threads`或藉由設定`OMP_NUM_THREADS`環境變數，您可以明確覆寫單一**平行**藉由指定指示詞`num_threads`子句。

## <a name="cross-references"></a>交叉參考：

- `omp_set_dynamic` 函式，請參閱 <<c0> [ 一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。

- `omp_get_dynamic` 函式，請參閱 <<c0> [ 一節 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md)在 40 頁面上。

- `OMP_NUM_THREADS` 環境變數，請參閱[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 48，頁和第 8 頁上 2.3 節。

- `num_threads` 子句中，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)上第 8 頁