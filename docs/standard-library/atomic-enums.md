---
title: '&lt;atomic&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: f41c5b238f74e85bc18e9ff5c3aa6a0050fe27e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376914"
---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt; 列舉

## <a name="memory_order-enum"></a><a name="memory_order_enum"></a>memory_order枚舉

為記憶體位置上的同步處理作業提供符號名稱。 這些作業會影響一個執行緒的指派如何在其他執行緒中變成可見。

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>Enta

|||
|-|-|
|`memory_order_relaxed`|不需要任何順序。|
|`memory_order_consume`|載入作業做為記憶體位置上的消耗行為。|
|`memory_order_acquire`|載入作業做為記憶體位置上的取得行為。|
|`memory_order_release`|儲存作業做為記憶體位置上的釋放作業。|
|`memory_order_acq_rel`|合併 `memory_order_acquire` 與 `memory_order_release`。|
|`memory_order_seq_cst`|合併 `memory_order_acquire` 與 `memory_order_release`。 標記為 `memory_order_seq_cst` 的記憶體存取必須是循序一致。|

## <a name="see-also"></a>另請參閱

[\<原子>](../standard-library/atomic.md)
