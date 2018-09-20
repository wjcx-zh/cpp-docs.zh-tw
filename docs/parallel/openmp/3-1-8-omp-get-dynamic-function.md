---
title: 3.1.8 omp_get_dynamic 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c30f49eaf91353d6a7cd9bd26e0e10e95cb6acd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426779"
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