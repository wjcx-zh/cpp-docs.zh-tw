---
title: 3.1.5 omp_get_num_procs 函式
ms.date: 11/04/2016
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
ms.openlocfilehash: 3c515381bbd9bb654ef1f41a9ecab1bc138ca946
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531218"
---
# <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs 函式

`omp_get_num_procs`函式會傳回呼叫的函式的時間位於程式可以使用的處理器數目。 格式如下：

```
#include <omp.h>
int omp_get_num_procs(void);
```