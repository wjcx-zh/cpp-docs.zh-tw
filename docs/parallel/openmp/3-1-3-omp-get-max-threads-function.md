---
title: 3.1.3 omp_get_max_threads 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c439dc0203fa3435c62e9669da40b5b092556492
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400818"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函式

**Omp_get_max_threads**函式傳回一個整數，保證在至少會用來組成一個小組，如果在平行區域，而不需要的執行緒數目一樣大**num_threads**子句能夠在此時所發現的程式碼中。 格式如下：

```
#include <omp.h>
int omp_get_max_threads(void);
```

下列的值表示下限**omp_get_max_threads**:

```

threads-used-for-next-team
<= omp_get_max_threads

```

請注意，如果在後續的平行區域會使用**num_threads**子句來要求特定數目的執行緒上下限的結果保證**omp_get_max_threads**不長的保留。

**Omp_get_max_threads**函式的傳回值可用來動態配置足夠的儲存體小組在後續的平行區域中的所有執行緒。

## <a name="cross-references"></a>交叉參考：

- **omp_get_num_threads**函式，請參閱 <<c2> [ 一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 頁上。

- **omp_set_num_threads**函式，請參閱 <<c2> [ 一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。

- **omp_set_dynamic**函式，請參閱 <<c2> [ 一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。

- **num_threads**子句，請參閱 < [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。