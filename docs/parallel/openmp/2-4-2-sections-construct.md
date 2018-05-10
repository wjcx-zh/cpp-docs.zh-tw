---
title: 2.4.2 sections 建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20b24c5b7d2458294da6280acb2ba7e8be5961fb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="242-sections-construct"></a>2.4.2 sections 建構
**區段**指示詞會識別 noniterative 工作共用建構，可指定一組建構將會分割為個執行緒在一個小組。 每個區段在小組中的執行緒所執行一次。 語法**區段**指示詞時，如下所示：  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block ]  
...  
}  
```  
  
 子句可以是下列其中一項：  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **lastprivate(** *variable-list* **)**  
  
 **reduction(** *operator* **:**  *variable-list* **)**  
  
 **nowait**  
  
 每個區段的開頭**區段**指示詞，雖然**區段**指示詞是選擇性的第一個區段。 **區段**指示詞必須出現的語彙範圍內**區段**指示詞。 結尾沒有隱含的屏障**區段**建構，除非**nowait**指定。  
  
 若要限制**區段**指示詞如下：  
  
-   A**區段**指示詞不能出現的語彙範圍外**區段**指示詞。  
  
-   只有一個**nowait**子句可以出現在**區段**指示詞。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **私用**， **firstprivate**， **lastprivate**，和**減少**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。