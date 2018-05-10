---
title: 2.3 parallel 建構 |Microsoft 文件
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
ms.openlocfilehash: 121454f6a98901a6c1b695a80c6ec774737b95e0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="23-parallel-construct"></a>2.3 parallel 建構
下列指示詞定義平行的區域，而是由多個執行緒以平行方式執行程式的區域。 這是開始平行執行的基本結構。  
  
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
  
 當執行緒發現平行建構時，其中一個在下列情況時，會建立小組的執行緒：  
  
-   否**如果**子句。  
  
-   **如果**運算式評估為非零值。  
  
 此執行緒會變成主執行緒的小組，0，執行緒數目，所有執行緒在小組中，包括主執行緒中，以平行方式都執行區域。 如果值**如果**運算式為零，序列化的地區。  
  
 若要判斷所要求的執行緒數目，下列規則會被視為順序。 第一個符合的條件的規則將會套用：  
  
1.  如果**num_threads**子句已存在，則整數運算式的值是所要求的執行緒數目。  
  
2.  如果**omp_set_num_threads**已呼叫程式庫函式，則是最近執行的呼叫中引數的值是所要求的執行緒數目。  
  
3.  如果環境變數**OMP_NUM_THREADS**定義，則這個環境變數的值是所要求的執行緒數目。  
  
4.  如果使用上述的方法，然後要求的執行緒數目是由實作定義。  
  
 如果**num_threads**出現子句時，則它會取代所要求的執行緒數目**omp_set_num_threads**程式庫函式或**OMP_NUM_THREADS**環境變數僅針對它套用到平行區域。 後續的平行區域不會影響它。  
  
 執行平行區域的執行緒數目也會根據已啟用動態調整執行緒數目。 如果已停用動態調整，要求的執行緒數目會執行平行區域。 如果動態調整已啟用要求的執行緒數目是最大的可能執行平行區域的執行緒數目。  
  
 如果已停用動態調整執行緒數目，並要求平行區域的執行緒數目超過可以提供執行階段系統的數字時遇到在平行區域時，程式的行為是實作定義。 實作，例如，中斷執行程式，或它可能會序列化平行區域。  
  
 **Omp_set_dynamic**程式庫函式和**OMP_DYNAMIC**環境變數可以用來啟用和停用動態調整執行緒數目。  
  
 實體處理器的實際裝載在任何指定時間的執行緒數目是由實作定義。 一旦建立，在小組中的執行緒數目會維持不變的平行區域的持續期間。 它可由使用者明確或是自動由執行階段系統從一個平行區域之間變更。  
  
 每個執行緒所執行的陳述式包含在平行區域的動態範圍內，而且每個執行緒可以執行的路徑不同於其他執行緒的陳述式。 發生在平行區域的語彙範圍外的指示詞被指被遺棄的指示詞。  
  
 沒有隱含的屏障在平行區域的結尾。 小組的主要執行緒會繼續執行在平行區域的結尾。  
  
 如果小組執行平行區域中的執行緒遇到另一個平行建構，它會建立新的小組，而且它會變成該新小組的主機。 根據預設，會序列化巢狀平行區域。 如此一來，依預設，巢狀平行區域是由一個執行緒所組成小組執行。 預設行為可能會變更，請使用執行階段程式庫函數**omp_set_nested**或環境變數**OMP_NESTED**。 不過，在一個小組執行巢狀平行區域的執行緒數目是由實作定義。  
  
 若要限制**平行**指示詞如下：  
  
-   最多一個**如果**子句可指示詞上出現。  
  
-   是未指定任何側邊效果 if 內是否運算式或**num_threads**運算式發生。  
  
-   A**擲回**執行平行區域必須內造成才能繼續在相同的結構化區塊，動態範圍內執行，且必須由相同的執行緒擲回例外狀況攔截到。  
  
-   只有一個**num_threads**子句可指示詞上出現。 **Num_threads**運算式會評估內容以外的平行區域中，並且必須評估為正整數值。  
  
-   評估順序**如果**和**num_threads**子句是未指定。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   **私用**， **firstprivate**，**預設**，**共用**， **copyin**，和**減少**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。  
  
-   **OMP_NUM_THREADS**環境變數[區段 4.2](../../parallel/openmp/4-2-omp-num-threads.md)在 48 頁面上。  
  
-   **omp_set_dynamic**程式庫函式，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。  
  
-   **OMP_DYNAMIC**環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。  
  
-   **omp_set_nested**函式，請參閱[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。  
  
-   **OMP_NESTED**環境變數，請參閱[區段 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 頁面上。  
  
-   **omp_set_num_threads**程式庫函式，請參閱[區段 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 36 頁面上。