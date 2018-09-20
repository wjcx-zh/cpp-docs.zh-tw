---
title: A.3 使用平行區域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82bc1655584af300cb2d36a62250595839d74551
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413077"
---
# <a name="a3---using-parallel-regions"></a>A.3 使用平行區域

`parallel`指示詞 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上) 可用於粗略平行處理程式。 在下列範例中，每個執行緒在平行區域決定全域陣列的哪個部分`x`作，根據執行緒數目：

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```