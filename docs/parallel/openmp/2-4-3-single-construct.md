---
title: 2.4.3 single 建構
ms.date: 11/04/2016
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
ms.openlocfilehash: 7dda98ee83ee08adc29830a9c4ada71a208705fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466361"
---
# <a name="243-single-construct"></a>2.4.3 single 建構

**單一**指示詞會識別指定小組 （不一定是主要執行緒） 中只有一個執行緒執行相關聯的結構化的區塊的建構。 語法**單一**指示詞時，如下所示：

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句可以是下列其中一項：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**copyprivate (** *變數清單* **)**

**nowait**

沒有隱含的障礙之後,**單一**建構，除非**nowait**指定子句。

若要限制**單一**指示詞如下所示：

- 只有一個**nowait**子句可能會出現在**單一**指示詞。

- **Copyprivate**子句不能搭配**nowait**子句。

## <a name="cross-references"></a>交叉參考：

- **私用**， **firstprivate**，以及**copyprivate**子句，請參閱[一節 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 25 頁上。