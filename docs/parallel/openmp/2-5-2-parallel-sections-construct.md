---
title: "2.5.2 parallel sections 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 086552c72e37822920e0afa213c7966befa052f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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