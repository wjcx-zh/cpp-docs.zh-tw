---
title: 2.5.2 parallel sections 建構 |Microsoft 文件
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
ms.openlocfilehash: b6f7a84e322cb273733c6a724ee2563928df8362
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections 建構
**平行區段**指示詞提供快顯表單來指定**平行**包含只有一個區域**區段**指示詞。 語意都完全相同，若要明確指定**平行**指示詞後面緊跟著**區段**指示詞。 語法**平行區段**指示詞時，如下所示：  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 *子句*可以是其中一個子句接受**平行**和**區段**指示詞，除了**nowait**子句。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **平行**指示詞，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上。  
  
-   **區段**指示詞，請參閱[區段 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md)在 14 頁面上。