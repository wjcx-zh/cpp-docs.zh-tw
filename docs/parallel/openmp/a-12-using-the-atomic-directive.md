---
title: 使用不可部分完成的指示詞 A.12 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d7a9843a0759b5a5bd558e07a2004f9ef1543
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="a12---using-the-atomic-directive"></a>A.12 使用 atomic 指示詞
下列範例可避免競爭情形 (同時更新項目的*x*由多個執行緒) 使用`atomic`指示詞 ([區段 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md)在 19 頁面上):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 使用的優點`atomic`指示詞，在此範例中，是可更新的平行 x 的兩個不同的項目。 如果`critical`指示詞 ([區段 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 頁) 所使用，則所有更新至的項目*x*循序 （但不在任何保證順序），就會執行。  
  
 請注意，`atomic`指示詞只適用於 C 或 c + + 陳述式緊接著下。  如此一來，項目*y*不會在此範例中以不可分割方式更新。