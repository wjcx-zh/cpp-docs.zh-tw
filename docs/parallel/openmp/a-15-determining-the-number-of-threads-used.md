---
title: A.15 判斷使用的執行緒數目
ms.date: 11/04/2016
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
ms.openlocfilehash: bd5e897eeab35ec73c061d2ae02a4b85772e1255
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525817"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15 判斷使用的執行緒數目

請考慮下列不正確的範例 (如[一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 頁上):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`序列一節的程式碼，呼叫傳回 1，因此*np*一律會等於前一個範例 1。 若要判斷將會針對平行區域部署的執行緒數目，請呼叫應該在平行區域內。

下列範例示範如何重寫此程式，但不包含查詢的執行緒數目：

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```