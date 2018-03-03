---
title: "2.4.3 單一建構 |Microsoft 文件"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc551986f149bda668c438ac5f51d01d530c51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="243-single-construct"></a>2.4.3 single 建構
**單一**指示詞會識別建構，可指定相關聯的結構化的區塊由小組 （不一定是主執行緒） 中的一個執行緒執行。 語法**單一**指示詞時，如下所示：  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 子句可以是下列其中一項：  
  
 **私用 (** *變數清單* **)**  
  
 **firstprivate (** *變數清單* **)**  
  
 **copyprivate (** *變數清單* **)**  
  
 **nowait**  
  
 沒有隱含的屏障之後**單一**建構，除非**nowait**指定子句。  
  
 若要限制**單一**指示詞如下：  
  
-   只有一個**nowait**子句可以出現在**單一**指示詞。  
  
-   **Copyprivate**子句必須配合**nowait**子句。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **私用**， **firstprivate**，和**copyprivate**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。