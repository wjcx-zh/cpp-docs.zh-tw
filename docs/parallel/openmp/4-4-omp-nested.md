---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453611"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED`環境變數啟用或停用巢狀平行處理原則，除非巢狀平行處理原則已啟用或停用藉由呼叫`o` **mp_set_nested**程式庫常式。 如果設定為 **，則為 TRUE**，啟用巢狀平行處理原則; 如果設為**FALSE**巢狀平行處理原則已停用。 預設值是**FALSE**。

範例：

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>交叉參考：

- `omp_set_nested` 函式，請參閱 <<c0> [ 一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。