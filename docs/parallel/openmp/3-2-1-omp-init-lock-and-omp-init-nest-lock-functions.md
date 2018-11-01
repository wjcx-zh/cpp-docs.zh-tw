---
title: 3.2.1 omp_init_lock 和 omp_init_nest_lock 函式
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472771"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函式

這些函式提供初始化鎖定的唯一方法。 每個函式會初始化參數相關聯鎖定*鎖定*用於後續的呼叫。 格式如下：

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

已解除鎖定的初始狀態 （也就是沒有任何執行緒擁有鎖定）。 可巢狀鎖定中，初始的巢狀計數為零。 它是呼叫其中一個已經初始化的鎖定變數的這些常式不相容。