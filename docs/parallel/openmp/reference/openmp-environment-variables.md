---
title: OpenMP 環境變數
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363878"
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數

提供指向OpenMP API中使用的環境變數的連結。

OpenMP 標準的可視化C++實現包括以下環境變數。 這些環境變數在程式啟動時讀取,並在運行時忽略對其值的修改(例如,使用[_putenv,_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

|環境變數|描述|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|在`for`或`parallel for`指令中指定[計劃子句](openmp-clauses.md#schedule)時`schedule(runtime)`修改其行為。|
|[OMP_NUM_THREADS](#omp-num-threads)|設置並行區域中的最大線程數,除非被[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)覆蓋。|
|[OMP_DYNAMIC](#omp-dynamic)|指定 OpenMP 執行時是否可以調整並列區域中的線程數。|
|[OMP_NESTED](#omp-nested)|指定是否啟用巢狀, 並啟用巢狀性或關閉`omp_set_nested`|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

指定 OpenMP 執行時是否可以調整並列區域中的線程數。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

`OMP_DYNAMIC`環境變數可以由[omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函數覆蓋。

OpenMP 標準的視覺C++實現的預設值`OMP_DYNAMIC=FALSE`為 。

有關詳細資訊,請參閱[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>範例

以下命令將`OMP_DYNAMIC`環境變數設定為 TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

以下命令顯示環境變數的`OMP_DYNAMIC`目前設定:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

指定是否啟用巢狀, 並啟用巢狀性或關閉`omp_set_nested`

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

環境`OMP_NESTED`變數可以由[omp_set_nested](openmp-functions.md#omp-set-nested)函數覆蓋。

OpenMP 標準的視覺C++實現的預設值`OMP_DYNAMIC=FALSE`為 。

有關詳細資訊,請參閱[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>範例

以下命令將`OMP_NESTED`環境變數設定為 TRUE:

```cmd
set OMP_NESTED=TRUE
```

以下命令顯示環境變數的`OMP_NESTED`目前設定:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

設置並行區域中的最大線程數,除非被[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)覆蓋。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>參數

*num*<br/>
並行區域中所需的最大線程數,在 Visual C++實現中最多 64 個線程。

### <a name="remarks"></a>備註

`OMP_NUM_THREADS`環境變數可以由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函數或[num_threads](openmp-clauses.md#num-threads)覆蓋。

OpenMP 標準`num`的 可視化C++實現的預設值是虛擬處理器的數量,包括超線程 CPU。

有關詳細資訊,請參閱[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>範例

以下指令將`OMP_NUM_THREADS`環境變數設定為`16`:

```cmd
set OMP_NUM_THREADS=16
```

以下命令顯示環境變數的`OMP_NUM_THREADS`目前設定:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

在`for`或`parallel for`指令中指定[計劃子句](openmp-clauses.md#schedule)時`schedule(runtime)`修改其行為。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>參數

*大小*<br/>
( 選擇性的 )指定反覆運算的大小。 *大小*必須為正整數。 預設值為`1`,除非*類型*為靜態。 *當類型*`runtime`為時無效。

*型別*<br/>
計畫型`dynamic`態 ,或`guided``runtime`、`static`或或 。

### <a name="remarks"></a>備註

OpenMP 標準的視覺C++實現的預設值`OMP_SCHEDULE=static,0`為 。

有關詳細資訊,請參閱[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>範例

以下命令設定`OMP_SCHEDULE`環境變數:

```cmd
set OMP_SCHEDULE="guided,2"
```

以下命令顯示環境變數的`OMP_SCHEDULE`目前設定:

```cmd
set OMP_SCHEDULE
```
