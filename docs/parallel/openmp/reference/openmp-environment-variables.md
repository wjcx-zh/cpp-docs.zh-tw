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
ms.openlocfilehash: 3f9117c531bdf0c5a0c94e0b18a055591f431036
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503750"
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數

提供 OpenMP API 中使用的環境變數連結。

OpenMP 標準的 Visual C++ 執行包含下列環境變數。 這些環境變數會在程式啟動時讀取，而在執行時間會忽略其值的修改 (例如，使用 [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)) 。

|環境變數|描述|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|當或指示詞中指定時，修改 [schedule](openmp-clauses.md#schedule) 子句的行為 `schedule(runtime)` `for` `parallel for` 。|
|[OMP_NUM_THREADS](#omp-num-threads)|除非 [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 或 [num_threads](openmp-clauses.md#num-threads)覆寫，否則設定平列區域中的執行緒數目上限。|
|[OMP_DYNAMIC](#omp-dynamic)|指定 OpenMP 執行時間是否可以調整平列區域中的執行緒數目。|
|[OMP_NESTED](#omp-nested)|指定是否啟用嵌套平行處理原則，除非已啟用或停用嵌套平行處理原則 `omp_set_nested` 。|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a> OMP_DYNAMIC

指定 OpenMP 執行時間是否可以調整平列區域中的執行緒數目。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

`OMP_DYNAMIC`環境變數可以由[omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函數覆寫。

OpenMP 標準的 Visual C++ 實作為預設值 `OMP_DYNAMIC=FALSE` 。

如需詳細資訊，請參閱 [4.3 OMP_DYNAMIC](../4-environment-variables.md#43-omp_dynamic)。

### <a name="example"></a>範例

下列命令會將 `OMP_DYNAMIC` 環境變數設為 TRUE：

```cmd
set OMP_DYNAMIC=TRUE
```

下列命令會顯示環境變數的目前設定 `OMP_DYNAMIC` ：

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a> OMP_NESTED

指定是否啟用嵌套平行處理原則，除非已啟用或停用嵌套平行處理原則 `omp_set_nested` 。

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

`OMP_NESTED`環境變數可以由[omp_set_nested](openmp-functions.md#omp-set-nested)函數覆寫。

OpenMP 標準的 Visual C++ 實作為預設值 `OMP_DYNAMIC=FALSE` 。

如需詳細資訊，請參閱 [4.4 OMP_NESTED](../4-environment-variables.md#44-omp_nested)。

### <a name="example"></a>範例

下列命令會將 `OMP_NESTED` 環境變數設為 TRUE：

```cmd
set OMP_NESTED=TRUE
```

下列命令會顯示環境變數的目前設定 `OMP_NESTED` ：

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a> OMP_NUM_THREADS

除非 [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) 或 [num_threads](openmp-clauses.md#num-threads)覆寫，否則設定平列區域中的執行緒數目上限。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>參數

*num*<br/>
您想要在平列區域中的執行緒數目上限，最大值為64（在 Visual C++ 的執行中）。

### <a name="remarks"></a>備註

`OMP_NUM_THREADS`環境變數可以由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函數或[num_threads](openmp-clauses.md#num-threads)覆寫。

`num`在 OpenMP 標準的 Visual C++ 中，的預設值是虛擬處理器的數目，包括超執行緒 cpu。

如需詳細資訊，請參閱 [4.2 OMP_NUM_THREADS](../4-environment-variables.md#42-omp_num_threads)。

### <a name="example"></a>範例

下列命令會將 `OMP_NUM_THREADS` 環境變數設定為 `16` ：

```cmd
set OMP_NUM_THREADS=16
```

下列命令會顯示環境變數的目前設定 `OMP_NUM_THREADS` ：

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a> OMP_SCHEDULE

當或指示詞中指定時，修改 [schedule](openmp-clauses.md#schedule) 子句的行為 `schedule(runtime)` `for` `parallel for` 。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>參數

*size*<br/>
 (選擇性) 指定反覆運算的大小。 *大小* 必須是正整數。 預設值為 `1` ，但 *類型* 為靜態時除外。 當 *類型* 為時無效 `runtime` 。

*type*<br/>
排程的種類，可能是 `dynamic` 、 `guided` 、 `runtime` 或 `static` 。

### <a name="remarks"></a>備註

OpenMP 標準的 Visual C++ 實作為預設值 `OMP_SCHEDULE=static,0` 。

如需詳細資訊，請參閱 [4.1 OMP_SCHEDULE](../4-environment-variables.md#41-omp_schedule)。

### <a name="example"></a>範例

下列命令會設定 `OMP_SCHEDULE` 環境變數：

```cmd
set OMP_SCHEDULE="guided,2"
```

下列命令會顯示環境變數的目前設定 `OMP_SCHEDULE` ：

```cmd
set OMP_SCHEDULE
```
