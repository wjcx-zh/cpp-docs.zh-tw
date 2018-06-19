---
title: 2.4.3 單一建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db3f9ca834fb3f35c95732698fd02e16f31b4225
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690578"
---
# <a name="243-single-construct"></a>2.4.3 single 建構
**單一**指示詞會識別建構，可指定相關聯的結構化的區塊由小組 （不一定是主執行緒） 中的一個執行緒執行。 語法**單一**指示詞時，如下所示：  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 子句可以是下列其中一項：  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **copyprivate (** *變數清單* **)**  
  
 **nowait**  
  
 沒有隱含的屏障之後**單一**建構，除非**nowait**指定子句。  
  
 若要限制**單一**指示詞如下：  
  
-   只有一個**nowait**子句可以出現在**單一**指示詞。  
  
-   **Copyprivate**子句必須配合**nowait**子句。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **私用**， **firstprivate**，和**copyprivate**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。