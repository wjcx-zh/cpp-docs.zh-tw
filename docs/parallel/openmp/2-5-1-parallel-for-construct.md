---
title: "2.5.1 parallel for 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dcd763b68a78e11c3c33bf3d750a26e88ad02ee
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
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