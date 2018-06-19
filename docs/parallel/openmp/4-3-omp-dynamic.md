---
title: 4.3 OMP_DYNAMIC |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686668"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
**OMP_DYNAMIC**環境變數啟用或停用動態調整可用的平行區域執行的執行緒數目，除非明確地啟用或停用藉由呼叫動態調整**omp_set_dynamic**程式庫常式。 其值必須是**TRUE**或**FALSE**。  
  
 如果設定為**TRUE**，可調整用於執行平行區域的執行緒數目，由執行階段環境，以充分利用系統資源。  如果設定為**FALSE**，已停用動態調整。 預設條件是由實作定義。  
  
 範例：  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>交叉參考：  
  
-   如需有關平行區域的詳細資訊，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上。  
  
-   **omp_set_dynamic**函式，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。