---
title: A.5 使用 critical 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444563"
---
# <a name="a5---using-the-critical-directive"></a>A.5 使用 critical 指示詞

下列範例包含數個`critical`指示詞 ([一節 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 頁上)。 此範例說明工作是從佇列中清除並處理的佇列模型。 若要防範清除佇列中的相同工作的多個執行緒，清除佇列作業必須是在`critical`一節。 因為兩個佇列，在此範例中是獨立的它們會受到`critical`指示詞，以不同的名稱， *xaxis*並*yaxis*。

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```