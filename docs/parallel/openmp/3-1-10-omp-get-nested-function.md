---
title: 3.1.10 omp_get_nested 函式
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519906"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函式

`omp_get_nested`函式會傳回非零值，如果巢狀平行處理原則已啟用而 0 會停用。 如需有關巢狀平行處理原則的詳細資訊，請參閱節 3.1.9 在 40 頁面上。 格式如下：

```
#include <omp.h>
int omp_get_nested(void);
```

如果實作不會實作巢狀平行處理原則，則此函式一律會傳回 0。