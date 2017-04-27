---
title: "&lt;atomic&gt; 列舉 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 94167b5068e3fb1370528d42c80d338a486cd68e
ms.lasthandoff: 02/24/2017

---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt; 列舉
  
##  <a name="memory_order_enum"></a> memory_order 列舉  
 為記憶體位置上的同步處理作業提供符號名稱。 這些作業會影響一個執行緒的指派如何在其他執行緒中變成可見。  
  
```
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```  
  
### <a name="remarks"></a>備註  
  
|||  
|-|-|  
|`memory_order_relaxed`|不需要任何順序。|  
|`memory_order_consume`|載入作業做為記憶體位置上的消耗行為。|  
|`memory_order_acquire`|載入作業做為記憶體位置上的取得行為。|  
|`memory_order_release`|儲存作業做為記憶體位置上的釋放作業。|  
|`memory_order_acq_rel`|合併 `memory_order_acquire` 與 `memory_order_release`。|  
|`memory_order_seq_cst`|合併 `memory_order_acquire` 與 `memory_order_release`。 標記為 `memory_order_seq_cst` 的記憶體存取必須是循序一致。|  
  
## <a name="see-also"></a>另請參閱  
 [\<atomic>](../standard-library/atomic.md)




