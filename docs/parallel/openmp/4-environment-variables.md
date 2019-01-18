---
title: 4. 環境變數
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 5d08031c252d1f3c45fc45c021d24476b393fe33
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397325"
---
# <a name="4-environment-variables"></a>4.環境變數

此章節會描述 OpenMP C 和 c + + API 的環境變數 （或類似平台特定的機制），以控制平行處理程式碼的執行。  環境變數名稱必須是大寫。 指派給它們的值不區分大小寫，且可能有前置和尾端空白字元。  修改程式啟動之後的值都會被忽略。

環境變數如下所示：

- [OMP_SCHEDULE](#41-omp_schedule)設定執行階段排程類型與區塊大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)設定執行期間要使用的執行緒數目。
- [OMP_DYNAMIC](#43-omp_dynamic)啟用或停用動態調整執行緒的數目。
- [OMP_NESTED](#44-omp_nested)啟用或停用巢狀平行處理原則。

在這一章中的範例只示範如何在 Unix C 殼層 (csh) 環境中可能會設定這些變數。 在 Korn 殼層和 DOS 環境中，動作如下：

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` 僅適用於`for`並`parallel for`有排程類型的指示詞`runtime`。 在執行階段，就可以設定所有這類迴圈的排程類型與區塊大小。 設定這個環境變數，任何可辨識的排程類型，並選擇性*chunk_size*。

針對`for`並`parallel for`以外的其他已排程類型的指示詞`runtime`，`OMP_SCHEDULE`會被忽略。 這個環境變數的預設值是由實作定義。 如果選擇性*chunk_size*設定，此值必須是正數。 如果*chunk_size*未設定，會假設的值為 1，除非排程是`static`。 針對`static`排程，預設區塊大小設定為迴圈的反覆項目空間除以套用到迴圈的執行緒數目。

範例：

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交互參照

- [針對](2-4-1-for-construct.md)指示詞
- [針對平行](2-5-1-parallel-for-construct.md)指示詞

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS`環境變數設定的預設執行期間要使用的執行緒數目。 `OMP_NUM_THREADS` 如果明確地藉由呼叫來變更該數字，則會忽略`omp_set_num_threads`程式庫常式。 它也會忽略如果沒有明確`num_threads`上的子句`parallel`指示詞。

值`OMP_NUM_THREADS`環境變數必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動有關`OMP_NUM_THREADS`環境變數和動態調整的執行緒，請參閱 2.3 節。

若要使用的執行緒數目是實作定義如果：

- `OMP_NUM_THREADS`未指定環境變數，
- 指定的值不是正整數，或
- 值大於最大的系統可支援的執行緒數目。

範例：

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交互參照

- [num_threads](2-3-parallel-construct.md)子句
- [omp_set_num_threads](3-1-1-omp-set-num-threads-function.md)函式
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) function

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC`環境變數啟用或停用動態調整可用的平行區域執行的執行緒數目。 `OMP_DYNAMIC` 動態調整是明確地啟用或停用藉由呼叫時，會忽略`omp_set_dynamic`程式庫常式。 其值必須是`TRUE`或`FALSE`。

如果`OMP_DYNAMIC`設為`TRUE`，根據執行階段環境，以最佳方式使用系統資源，您可以調整用於執行平行區域的執行緒數目。  如果`OMP_DYNAMIC`設為`FALSE`，動態調整已停用。 預設條件是由實作定義。

範例：

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交互參照

- [平行區域](2-3-parallel-construct.md)
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) function

## <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED`環境變數啟用或停用巢狀平行處理原則，除非巢狀平行處理原則已啟用或停用藉由呼叫`omp_set_nested`程式庫常式。 如果`OMP_NESTED`設為`TRUE`，巢狀平行處理原則已啟用。 如果`OMP_NESTED`設為`FALSE`巢狀平行處理原則已停用。 預設值為 `FALSE`。

範例：

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交互參照

- [omp_set_nested](3-1-9-omp-set-nested-function.md) function
