---
title: 4. 環境變數
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370259"
---
# <a name="4-environment-variables"></a>4. 環境變數

本章介紹 OpenMP C 和C++控制並行代碼執行的 API 環境變數(或類似特定於平臺的機制)。  環境變數的名稱必須為大寫。 分配給它們的值不區分大小寫,並且可能具有前導空格和尾隨空格。  程序啟動後對值的修改將被忽略。

環境變數如下所示:

- [OMP_SCHEDULE](#41-omp_schedule)設置運行時計劃類型和區塊大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)設置執行期間要使用的線程數。
- [OMP_DYNAMIC](#43-omp_dynamic)啟用或禁用線程數的動態調整。
- [OMP_NESTED](#44-omp_nested)啟用或禁用嵌套並行性。

本章中的示例僅演示如何在 Unix C 外殼 (csh) 環境中設置這些變數。 在 Korn 外殼和 DOS 環境中,操作類似:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

Dos:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`僅適用於具有`for`計畫`parallel for`類型的`runtime`和指令。 可在運行時設置所有此類循環的計劃類型和區塊大小。 將此環境變數設置為任何已識別的計畫類型和可選*chunk_size。*

將`for`忽略`parallel for`具有計畫類型`runtime`而不是`OMP_SCHEDULE`的和指令。 此環境變數的預設值是實現定義。 如果設置了可選*chunk_size,* 則該值必須為正。 如果未設置*chunk_size,* 則假定值為 1,`static`但計劃為 時除外。 對於`static`計劃,預設區塊大小設置為迴圈反覆運算空間除以應用於迴圈的線程數。

範例：

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交叉參考

- [指令](2-directives.md#241-for-construct)
- [指令的併行](2-directives.md#251-parallel-for-construct)

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

環境`OMP_NUM_THREADS`變數設置執行期間要使用的預設線程數。 `OMP_NUM_THREADS`如果透過呼叫庫例程顯式更改該號碼,`omp_set_num_threads`則忽略該編號。 如果指令上有顯式`num_threads`子句`parallel`, 也會忽略它。

`OMP_NUM_THREADS`環境變數的值必須為正整數。 其效果取決於是否啟用了線程數的動態調整。 有關`OMP_NUM_THREADS`環境變數和線程動態調整之間互動的一套全面規則,請參閱[第 2.3 節](2-directives.md#23-parallel-construct)。

在以下情況下,要使用的線程數是實現定義的:

- 未`OMP_NUM_THREADS`指定環境變數,
- 指定的值不是正整數或
- 該值大於系統可以支援的最大線程數。

範例：

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交叉參考

- [num_threads](2-directives.md#23-parallel-construct)條款
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)功能
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)功能

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

環境`OMP_DYNAMIC`變數啟用或禁用可用於執行並列區域的線程數的動態調整。 `OMP_DYNAMIC`當透過呼叫庫例程顯式啟用或禁用動態調整時,`omp_set_dynamic`將忽略。 其值必須為`TRUE``FALSE`或 。

如果`OMP_DYNAMIC`設置`TRUE`為 ,則用於執行並行區域的線程數可能由運行時環境調整,以最佳使用系統資源。  如果`OMP_DYNAMIC`設置為`FALSE`,則禁用動態調整。 默認條件為實現定義。

範例：

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交叉參考

- [平行區域](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)功能

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4 OMP_NESTED

除非`OMP_NESTED`通過調`omp_set_nested`用 庫例程啟用或禁用嵌套並行性,否則環境變數將啟用或禁用嵌套並行性。 如果`OMP_NESTED`設置`TRUE`為 ,則啟用嵌套並行性。 如果`OMP_NESTED`設置`FALSE`為 ,則嵌套並行性將禁用。 預設值是 `FALSE`。

範例：

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交叉參考

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)功能
