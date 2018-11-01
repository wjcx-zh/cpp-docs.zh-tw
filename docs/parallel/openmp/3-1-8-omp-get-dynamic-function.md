---
title: 3.1.8 omp_get_dynamic 函式
ms.date: 11/04/2016
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
ms.openlocfilehash: d9476894e5aff4cc7bb9c67fbbeb14d185b65f5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566422"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函式

**Omp_get_dynamic**函式會傳回非零值，如果執行緒的動態調整已啟用，否則傳回 0。 格式如下：

```
#include <omp.h>
int omp_get_dynamic(void);
```

如果實作不會實作動態調整執行緒數目，此函式一律會傳回 0。

## <a name="cross-references"></a>交叉參考：

- 如需執行緒的動態調整的說明，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。