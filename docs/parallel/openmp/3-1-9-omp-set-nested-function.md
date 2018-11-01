---
title: 3.1.9 omp_set_nested 函式
ms.date: 11/04/2016
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
ms.openlocfilehash: 683c2cf684aa7212b8323fda9f748812fa9c3359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648002"
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函式

**Omp_set_nested**函式啟用或停用巢狀平行處理原則。 格式如下：

```
#include <omp.h>
void omp_set_nested(int nested);
```

如果*巢狀*判斷值為 0，巢狀平行處理原則已停用，這是預設值，以及巢狀平行區域會經過序列化，並由目前的執行緒執行。 如果*巢狀*會評估為非零的值，已啟用巢狀平行處理原則，以及巢狀平行區域可以部署額外的執行緒，以形成巢狀的小組。

此函式會產生結果上面所述，從程式的一部分呼叫時所在**omp_in_parallel**函式會傳回零。 如果呼叫程式的一部分從何處**omp_in_parallel**函式會傳回非零值，這個函式的行為是未定義。

這個呼叫的優先順序高於**OMP_NESTED**環境變數。

啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義。 如此一來，OpenMP 相容的實作都可以序列化巢狀平行區域，即使已啟用巢狀平行處理原則。

## <a name="cross-references"></a>交叉參考：

- **OMP_NESTED**環境變數，請參閱[一節 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 頁面上。

- **omp_in_parallel**函式，請參閱 <<c2> [ 一節 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 38 頁面上。