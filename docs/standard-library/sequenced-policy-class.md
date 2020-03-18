---
title: sequenced_policy 類別
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444924"
---
# <a name="sequenced_policy-class"></a>sequenced_policy 類別

用來做為唯一的類型來區分平行演算法多載，並要求平行演算法的執行可能不會平行處理。

## <a name="syntax"></a>語法

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>備註

在使用 `execution::sequenced_policy` 原則執行平行演算法期間，如果專案存取函式的調用透過未攔截的例外狀況結束，則應該呼叫 `terminate()`。
