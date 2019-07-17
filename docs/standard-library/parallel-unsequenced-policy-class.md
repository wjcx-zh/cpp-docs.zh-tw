---
title: parallel_unsequenced_policy 類別
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268780"
---
# <a name="parallelunsequencedpolicy-class"></a>parallel_unsequenced_policy 類別

釐清平行演算法多載，並指出平行演算法的執行可能會平行處理和向量化，以用做為唯一的類型。

## <a name="syntax"></a>語法

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>備註

使用平行演算法的執行期間`execution::parallel_unsequenced_policy`原則，如果未攔截到例外狀況，透過結束時項目存取函式的引動過程`terminate()`都應該呼叫。
