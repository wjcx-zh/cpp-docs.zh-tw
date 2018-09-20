---
title: 3.1.2 omp_get_num_threads 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 512c09b0cf71a7fd9c7438b6f9cceb9f16126718
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424974"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 函式

**Omp_get_num_threads**函式傳回的執行緒數目目前在小組執行平行從中呼叫它的區域中。 格式如下：

```
#include <omp.h>
int omp_get_num_threads(void);
```

**Num_threads**子句**omp_set_num_threads**函式，而**OMP_NUM_THREADS**環境變數來控制小組中的執行緒數目。

如果使用者有沒有已明確設定的執行緒數目，預設值是由實作定義。 此函式繫結至最接近的封閉式**平行**指示詞。 如果呼叫從序列一部分的程式，或在已序列化的巢狀平行區域，則此函數會傳回 1。

## <a name="cross-references"></a>交叉參考：

- **OMP_NUM_THREADS**環境變數，請參閱[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 48 頁上。

- **num_threads**子句，請參閱 < [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。

- **平行**建構，請參閱 < [2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。