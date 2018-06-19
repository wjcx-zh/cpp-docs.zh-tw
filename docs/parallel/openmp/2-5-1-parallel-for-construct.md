---
title: 2.5.1 parallel for 建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2732c4f8713466d282346ea240bd3c41886ce0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687149"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for 建構
**平行的**指示詞是捷徑**平行**包含只有一個區域**如**指示詞。 語法**平行的**指示詞時，如下所示：  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop  
```  
  
 這個指示詞允許的所有子句**平行**指示詞和**如**指示詞，除了`nowait`子句，相同的意義和限制。 語意都完全相同，若要明確指定**平行**指示詞後面緊跟著**如**指示詞。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **平行**指示詞，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上。  
  
-   **如**指示詞，請參閱[區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁面上。  
  
-   資料屬性子句，請參閱[2.7.2 資料共用屬性子句](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。