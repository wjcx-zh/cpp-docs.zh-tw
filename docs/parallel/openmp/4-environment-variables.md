---
title: 4. 環境變數
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882848"
---
# <a name="4-environment-variables"></a>4. 環境變數

本章說明 OpenMP C 和C++ API 環境變數（或類似的平臺特定機制），以控制平行程式碼的執行。  環境變數的名稱必須是大寫。 指派給它們的值不區分大小寫，而且可能有開頭和尾端的空白字元。  在程式啟動後對值所做的修改會被忽略。

環境變數如下所示：

- [OMP_SCHEDULE](#41-omp_schedule)設定執行時間排程類型和區塊大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)設定要在執行期間使用的執行緒數目。
- [OMP_DYNAMIC](#43-omp_dynamic)啟用或停用執行緒數目的動態調整。
- [OMP_NESTED](#44-omp_nested)啟用或停用嵌套的平行處理原則。

本章節中的範例只會示範如何在 Unix C shell （csh）環境中設定這些變數。 在 Korn shell 和 DOS 環境中，動作很類似：

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh  
`export OMP_SCHEDULE="dynamic"`

造成  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` 僅適用于具有排程類型 `runtime`的 `for` 和 `parallel for` 指示詞。 所有這類迴圈的排程類型和區塊大小都可以在執行時間設定。 將此環境變數設定為任何可辨識的排程類型，以及選擇性的*chunk_size*。

對於具有 `runtime`以外之排程類型的 `for` 和 `parallel for` 指示詞，`OMP_SCHEDULE` 會被忽略。 此環境變數的預設值為「執行定義」。 如果設定了選擇性的*chunk_size* ，此值必須是正數。 如果未設定*chunk_size* ，則會假設為1的值，除非 `static`排程。 若為 `static` 排程，預設的區塊大小會設定為迴圈反覆運算空間，除以套用至迴圈的執行緒數目。

範例：

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交互參考

- [for](2-directives.md#241-for-construct)指示詞
- [parallel for](2-directives.md#251-parallel-for-construct)指示詞

## <a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS` 環境變數會設定要在執行期間使用的預設執行緒數目。 如果藉由呼叫 `omp_set_num_threads` 程式庫常式明確變更該數位，則會忽略 `OMP_NUM_THREADS`。 如果 `parallel` 指示詞上有明確的 `num_threads` 子句，也會予以忽略。

`OMP_NUM_THREADS` 環境變數的值必須是正整數。 其效果取決於是否已啟用執行緒數目的動態調整。 如需有關 `OMP_NUM_THREADS` 環境變數與執行緒動態調整之間互動的一組完整規則，請參閱[2.3 區段](2-directives.md#23-parallel-construct)。

在下列情況中，要使用的執行緒數目是執行定義的：

- 未指定 `OMP_NUM_THREADS` 環境變數，
- 指定的值不是正整數，或
- 值大於系統可支援的執行緒數目上限。

範例：

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交互參考

- [num_threads](2-directives.md#23-parallel-construct)子句
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)函式
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)函式

## <a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC` 環境變數會啟用或停用動態調整平列區域執行可用的執行緒數目。 藉由呼叫 `omp_set_dynamic` 程式庫常式明確地啟用或停用動態調整時，會忽略 `OMP_DYNAMIC`。 其值必須 `TRUE` 或 `FALSE`。

如果 `OMP_DYNAMIC` 設定為 `TRUE`，則執行時間環境可能會調整用於執行平列區域的執行緒數目，以充分利用系統資源。  如果 `OMP_DYNAMIC` 設定為 `FALSE`，則會停用動態調整。 預設條件為「執行定義」。

範例：

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交互參考

- [平列區域](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)函式

## <a name="44-omp_nested"></a>4.4 OMP_NESTED

除非藉由呼叫 `omp_set_nested` 程式庫常式來啟用或停用嵌套平行處理原則，否則 `OMP_NESTED` 環境變數會啟用或停用嵌套的平行處理原則。 如果 `OMP_NESTED` 設定為 `TRUE`，則會啟用嵌套的平行處理原則。 如果 `OMP_NESTED` 設定為 `FALSE`，則會停用嵌套的平行處理原則。 預設值是 `FALSE`。

範例：

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交互參考

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)函式
