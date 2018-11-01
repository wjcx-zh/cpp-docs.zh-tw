---
title: 3.2.3 omp_set_lock 和 omp_set_nest_lock 函式
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617655"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函式

所有這些函式會封鎖執行此函式，直到指定的鎖定可用，然後設定 鎖定的執行緒。 如果已解除鎖定使用簡單的鎖定。 如果已解除鎖定，或執行函式的執行緒已擁有使用可巢狀鎖定。 格式如下：

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

簡單的鎖定，以引數`omp_set_lock`函式必須指向未初始化的鎖定的變數。 鎖定擁有權會授與執行函式的執行緒。

可巢狀鎖定的引數`omp_set_nest_lock`函式必須指向未初始化的鎖定的變數。 巢狀的計數會遞增，而執行緒會授與存取，或保留的鎖定擁有權。