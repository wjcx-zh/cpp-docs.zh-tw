---
title: "4.3 OMP_DYNAMIC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 103067b28990854fb6522c19f4349a9607d65bab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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