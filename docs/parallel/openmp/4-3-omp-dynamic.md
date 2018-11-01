---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488555"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

**OMP_DYNAMIC**環境變數啟用或停用動態調整的執行緒可供執行的平行區域數目，除非明確地啟用或停用藉由呼叫動態調整**omp_set_dynamic**程式庫常式。 其值必須是**真**或是**FALSE**。

如果設定為 **，則為 TRUE**，由執行階段環境，以充分利用系統資源，您可以調整用於執行平行區域的執行緒數目。  如果設定為**FALSE**，動態調整已停用。 預設條件是由實作定義。

範例：

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>交叉參考：

- 如需有關平行區域的詳細資訊，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。

- **omp_set_dynamic**函式，請參閱 <<c2> [ 一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。