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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143284"
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數

提供 OpenMP API 中使用之環境變數的連結。

OpenMP 標準C++的視覺化執行包含下列環境變數。 這些環境變數會在程式啟動時讀取，並在執行時間忽略其值的修改（例如，使用[_putenv，_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)）。

|環境變數|描述|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|當 `for` 或 `parallel for` 指示詞中指定了 `schedule(runtime)` 時，修改[排程](openmp-clauses.md#schedule)子句的行為。|
|[OMP_NUM_THREADS](#omp-num-threads)|設定平列區域中的執行緒數目上限，除非[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)加以覆寫。|
|[OMP_DYNAMIC](#omp-dynamic)|指定 OpenMP 執行時間是否可以調整平列區域中的執行緒數目。|
|[OMP_NESTED](#omp-nested)|指定是否啟用嵌套的平行處理原則，除非已啟用或停用 `omp_set_nested`的嵌套平行處理原則。|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

指定 OpenMP 執行時間是否可以調整平列區域中的執行緒數目。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

[Omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函數可以覆寫 `OMP_DYNAMIC` 環境變數。

OpenMP 標準的視覺化C++執行中預設值為 `OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>範例

下列命令會將 `OMP_DYNAMIC` 環境變數設定為 TRUE：

```cmd
set OMP_DYNAMIC=TRUE
```

下列命令會顯示 `OMP_DYNAMIC` 環境變數的目前設定：

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

指定是否啟用嵌套的平行處理原則，除非已啟用或停用 `omp_set_nested`的嵌套平行處理原則。

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

[Omp_set_nested](openmp-functions.md#omp-set-nested)函數可以覆寫 `OMP_NESTED` 環境變數。

OpenMP 標準的視覺化C++執行中預設值為 `OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>範例

下列命令會將 `OMP_NESTED` 環境變數設定為 TRUE：

```cmd
set OMP_NESTED=TRUE
```

下列命令會顯示 `OMP_NESTED` 環境變數的目前設定：

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

設定平列區域中的執行緒數目上限，除非[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)加以覆寫。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>參數

*num*<br/>
您想要在平列區域中的執行緒數目上限，最多可達64（ C++在視覺效果的執行中）。

### <a name="remarks"></a>備註

`OMP_NUM_THREADS` 環境變數可以由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函數或[num_threads](openmp-clauses.md#num-threads)覆寫。

在 OpenMP standard 的視覺效果C++中，`num` 的預設值是虛擬處理器的數目，包括超執行緒 cpu。

如需詳細資訊，請參閱[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>範例

下列命令會將 `OMP_NUM_THREADS` 環境變數設定為 `16`：

```cmd
set OMP_NUM_THREADS=16
```

下列命令會顯示 `OMP_NUM_THREADS` 環境變數的目前設定：

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

當 `for` 或 `parallel for` 指示詞中指定了 `schedule(runtime)` 時，修改[排程](openmp-clauses.md#schedule)子句的行為。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>參數

*size*<br/>
選擇性指定反覆運算的大小。 *大小*必須是正整數。 預設值為 `1`，但*類型*為靜態時除外。 當*類型*為 `runtime`時無效。

*type*<br/>
排程的類型，`dynamic`、`guided`、`runtime`或 `static`。

### <a name="remarks"></a>備註

OpenMP 標準的視覺化C++執行中預設值為 `OMP_SCHEDULE=static,0`。

如需詳細資訊，請參閱[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>範例

下列命令會設定 `OMP_SCHEDULE` 環境變數：

```cmd
set OMP_SCHEDULE="guided,2"
```

下列命令會顯示 `OMP_SCHEDULE` 環境變數的目前設定：

```cmd
set OMP_SCHEDULE
```
