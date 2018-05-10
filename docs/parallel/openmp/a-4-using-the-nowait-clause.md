---
title: 使用 nowait 子句 A.4 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1de6b5e86d600ee1b3c2fa2c29fe014f9cb768
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="a4---using-the-nowait-clause"></a>A.4 使用 nowait 子句
如果有多個獨立的迴圈的平行區域內，您可以使用`nowait`子句 ([區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁面上) 若要避免隱含的屏障結尾`for`指示詞，如下所示：  
  
```  
#pragma omp parallel  
{  
    #pragma omp for nowait  
        for (i=1; i<n; i++)  
             b[i] = (a[i] + a[i-1]) / 2.0;  
    #pragma omp for nowait  
        for (i=0; i<m; i++)  
            y[i] = sqrt(z[i]);  
}  
```