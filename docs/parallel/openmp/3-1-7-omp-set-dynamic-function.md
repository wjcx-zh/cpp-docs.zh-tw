---
title: 3.1.7 omp_set_dynamic 函式
ms.date: 11/04/2016
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
ms.openlocfilehash: 641b2ecfdb19aec9387aa299d22a041f25b22929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492933"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函式

**Omp_set_dynamic**函式啟用或停用動態調整的執行緒可供執行的平行區域數目。 格式如下：

```
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*會評估為非零的值，用於執行後續的平行區域的執行緒數目可能會自動調整的執行階段環境，以充分利用系統資源。 如此一來，使用者所指定的執行緒數目會是最大執行緒計數。 小組執行平行的區域中的執行緒數目該平行區域期間保持固定，並回報**omp_get_num_threads**函式。

如果*dynamic_threads*會評估為 0，已停用動態調整。

此函式會產生結果上面所述，從程式的一部分呼叫時所在**omp_in_parallel**函式會傳回零。 如果呼叫程式的一部分從何處**omp_in_parallel**函式會傳回非零值，這個函式的行為是未定義。

呼叫**omp_set_dynamic**的優先順序高於**OMP_DYNAMIC**環境變數。

執行緒的動態調整的預設值是由實作定義。 如此一來，使用者程式碼相依於特定數目的執行緒有正確的執行應該明確地停用動態的執行緒。 實作並不需要提供的功能，以動態調整執行緒數目，但他們必須提供介面以支援跨所有平台的可攜性。

## <a name="cross-references"></a>交叉參考：

- **omp_get_num_threads**函式，請參閱 <<c2> [ 一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 頁上。

- **OMP_DYNAMIC**環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。

- **omp_in_parallel**函式，請參閱 <<c2> [ 一節 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 38 頁面上。