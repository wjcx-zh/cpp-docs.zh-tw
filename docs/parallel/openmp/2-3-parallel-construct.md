---
title: 2.3 parallel 建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4be5bdc40f69cfa0a326ffa6a7f8465e401cfd33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448229"
---
# <a name="23-parallel-construct"></a>2.3 parallel 建構

下列指示詞定義在平行區域，是由多個執行緒以平行方式執行程式的區域。 這是開始平行執行的基本建構。

```
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是下列其中之一：

**if(** *scalar-expression* **)**

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**default(shared &#124; none)**

**shared(** *variable-list* **)**

**copyin(** *variable-list* **)**

**reduction(** *operator* **:**  *variable-list* **)**

**num_threads(** *integer-expression* **)**

執行緒遇到平行建構，如果其中一個下列的情況下，則為 true 時會建立的執行緒小組：

- 否**如果**出現子句時。

- **如果**運算式會評估為非零值。

此執行緒會成為小組成員，0，執行緒數目的主要執行緒和小組成員，包括主要執行緒中中的所有執行緒以平行方式都執行的區域。 如果值**如果**運算式為零，序列化的區域。

若要判斷要求的執行緒數目，下列規則會被視為順序。 第一個符合其條件的規則將會套用：

1. 如果**num_threads**子句已存在，則整數運算式的值是所要求的執行緒數目。

1. 如果**omp_set_num_threads**已呼叫程式庫函式，則是最近執行的呼叫中引數的值是所要求的執行緒數目。

1. 如果環境變數**OMP_NUM_THREADS**定義，則此環境變數的值是所要求的執行緒數目。

1. 如果已使用任何上述方法，然後要求的執行緒數目是由實作定義。

如果**num_threads**出現子句時，則它會取代所要求的執行緒數目**omp_set_num_threads**程式庫函式或**OMP_NUM_THREADS**環境變數只會針對它套用到平行區域。 後續的平行區域不會影響它。

執行平行區域的執行緒數目也取決於已啟用動態調整執行緒數目。 如果已停用動態調整，要求的執行緒數目會執行平行的區域。 如果動態調整已啟用要求的執行緒數目是可能執行平行區域的執行緒數目上限。

如果在平行區域為止已停用動態調整執行緒數目，而要求的平行區域的執行緒數目超過執行階段系統可以提供的數字，該程式的行為是實作定義。 實作可能，比方說，中斷執行程式，或它可以將平行區域進行序列化。

**Omp_set_dynamic**程式庫函式並**OMP_DYNAMIC**環境變數可用來啟用和停用動態調整執行緒數目。

實體處理器實際上裝載在任何指定時間的執行緒數目是由實作定義。 建立之後，在小組中的執行緒數目會維持不變，平行區域的持續期間。 明確的使用者或自動執行階段系統從一個平行區域到另一個，就可以進行變更。

每個執行緒中，執行包含在平行區域的動態範圍內的陳述式，並每個執行緒可以執行的陳述式的路徑不同於其他執行緒。 發生在平行區域的語彙範圍外的指示詞被指被遺棄的指示詞。

沒有隱含的障礙，在平行區域的結尾。 只有小組的主要執行緒會繼續執行在平行區域的結尾。

如果小組執行平行的區域中的執行緒發生另一個平行建構，它會建立新的小組，它會變成該新的小組的主要。 根據預設，會序列化巢狀平行區域。 如此一來，根據預設，巢狀平行區域是由一個執行緒所組成的小組執行。 可能會使用執行階段程式庫函式來變更預設行為**omp_set_nested**或環境變數**OMP_NESTED**。 不過，在小組執行巢狀平行區域的執行緒數目是由實作定義。

若要限制**平行**指示詞如下所示：

- 最多一個**如果**子句可以出現在指示詞。

- 並未指定任何是否端效果置於 if 運算式或**num_threads**運算式就會發生。

- A**擲回**執行在平行區域必須造成才能繼續在相同的結構化區塊，動態範圍內執行，且必須由相同的執行緒擲回例外狀況攔截到。

- 只有一個**num_threads**子句可以出現在指示詞。 **Num_threads**運算式會評估平行區域中，內容之外，並且必須評估為正整數值。

- 評估順序**如果**並**num_threads**子句並未指定。

## <a name="cross-references"></a>交叉參考：

- **私用**， **firstprivate**，**預設**，**共用**， **copyin**，以及**減少**子句，請參閱[一節 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 25 頁上。

- **OMP_NUM_THREADS**環境變數[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 48 頁上。

- **omp_set_dynamic**程式庫函式，請參閱 <<c2> [ 一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。

- **OMP_DYNAMIC**環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。

- **omp_set_nested**函式，請參閱 <<c2> [ 一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。

- **OMP_NESTED**環境變數，請參閱[一節 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 頁面上。

- **omp_set_num_threads**程式庫函式，請參閱 <<c2> [ 一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。