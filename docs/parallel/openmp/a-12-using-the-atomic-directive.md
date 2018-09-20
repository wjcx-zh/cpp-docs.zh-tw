---
title: A.12 使用 atomic 指示詞 |Microsoft Docs
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
ms.openlocfilehash: 04daed582cfe87f6e4803b30919af3e07037de7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378744"
---
# <a name="a12---using-the-atomic-directive"></a>A.12 使用 atomic 指示詞

下列範例可避免競爭情形 (同時更新項目的*x*由多個執行緒) 使用`atomic`指示詞 ([一節 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) 19 頁上):

```
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

使用的優點`atomic`指示詞在此範例中是它可讓兩個不同的項目平行 x 的更新。 如果`critical`指示詞 ([2.6.2 區段](../../parallel/openmp/2-6-2-critical-construct.md)第 18 頁上) 所使用，則所有更新的元素*x*循序 （但不在任何保證順序），就會執行。

請注意，`atomic`指示詞只適用於 C 或 c + + 陳述式緊接著下。  如此一來，項目*y*不在此範例中會以不可分割方式更新。