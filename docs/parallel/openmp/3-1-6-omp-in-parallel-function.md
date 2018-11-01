---
title: 3.1.6 omp_in_parallel 函式
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482039"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函式

**Omp_in_parallel**函式會傳回非零值，如果它動態程度以平行方式執行的平行區域內呼叫; 否則它會傳回 0。 格式如下：

```
#include <omp.h>
int omp_in_parallel(void);
```

此函數會傳回非零值，以平行方式，包括序列化的巢狀的區域執行的區域中呼叫時。