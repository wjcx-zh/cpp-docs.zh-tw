---
title: "4.1 OMP_SCHEDULE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 330e5ea576e3cd779a7c17c21d00b6459f5e7043
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE
**OMP_SCHEDULE**僅適用於**如**和**平行的**有排程類型的指示詞**執行階段**。 所有這類迴圈的排程類型和區塊大小可以藉由設定這個環境變數，任何可辨識的排程類型，並選擇性設定在執行階段*chunk_size*。  
  
 如**如**和**平行的**以外，具有排程類型的指示詞**執行階段**， **OMP_SCHEDULE**會被忽略。 這個環境變數的預設值是由實作定義。 如果選擇性*chunk_size*設定，值必須是正數。 如果*chunk_size*未設定，會假設 1 的值，除非是**靜態**排程。 如**靜態**排程，預設區塊大小設定為迴圈反覆項目空間數目除以 套用到迴圈的執行緒數目。  
  
 範例：  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **如**指示詞，請參閱[區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁面上。  
  
-   **針對平行**指示詞，請參閱[區段 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md)在 16 頁面上。