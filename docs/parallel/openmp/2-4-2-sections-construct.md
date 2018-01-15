---
title: "2.4.2 sections 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e5b755e95e9bbbb78d6ab13cd09732f9c9aee3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
 **私用 (** *變數清單* **)**  
  
 **firstprivate (** *變數清單* **)**  
  
 **lastprivate (** *變數清單* **)**  
  
 **減少 (** *運算子* **:***變數清單* **)**   
  
 **nowait**  
  
 每個區段的開頭**區段**指示詞，雖然**區段**指示詞是選擇性的第一個區段。 **區段**指示詞必須出現的語彙範圍內**區段**指示詞。 結尾沒有隱含的屏障**區段**建構，除非**nowait**指定。  
  
 若要限制**區段**指示詞如下：  
  
-   A**區段**指示詞不能出現的語彙範圍外**區段**指示詞。  
  
-   只有一個**nowait**子句可以出現在**區段**指示詞。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **私用**， **firstprivate**， **lastprivate**，和**減少**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。