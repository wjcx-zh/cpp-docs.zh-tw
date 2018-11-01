---
title: 3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式
ms.date: 11/04/2016
ms.assetid: d334907d-94f7-4bbf-b20e-41d53484cbff
ms.openlocfilehash: 02f739ab2834db7eca9b051e6659644c39b51e84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666185"
---
# <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式

這些函式確定所指，鎖定變數*鎖定*未初始化。 格式如下：

```
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

它是呼叫其中一個鎖定變數未初始化或已解除鎖定使用這些常式不相容。