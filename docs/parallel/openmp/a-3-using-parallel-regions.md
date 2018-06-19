---
title: 使用平行區域 A.3 |Microsoft 文件
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
ms.openlocfilehash: a38962043ecc29426cae3e33842957b68cf37087
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689892"
---
# <a name="a3---using-parallel-regions"></a>A.3 使用平行區域
`parallel`指示詞 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上) 可用於粗略平行的程式。 在下列範例中，每個執行緒在平行區域決定全域陣列的哪個部分`x`運作，根據執行緒數：  
  
```  
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)  
{  
    iam = omp_get_thread_num();  
    np =  omp_get_num_threads();  
    ipoints = npoints / np;  
    subdomain(x, iam, ipoints);  
}  
```