---
title: 2.5.2 parallel sections 建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402326"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections 建構

**各節的平行**指示詞來指定提供快顯表單**平行**包含只有一個區域**各節**指示詞。 語意都完全相同，若要明確指定**平行**指示詞後面緊跟著**各節**指示詞。 語法**平行處理區段**指示詞時，如下所示：

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是其中一個接受子句**平行**並**各節**指示詞，除了**nowait**子句。

## <a name="cross-references"></a>交叉參考：

- **平行**指示詞，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。

- **章節**指示詞，請參閱[一節 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)在 14 頁面上。