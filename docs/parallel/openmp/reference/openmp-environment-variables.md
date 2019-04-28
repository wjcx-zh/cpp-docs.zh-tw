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
ms.openlocfilehash: 73fb11db14df22e5df95fdec556ccdfc16a935e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362630"
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數

提供連結 OpenMP API 中使用的環境變數。

視覺效果C++實作的 OpenMP 標準包含下列環境變數。 這些環境變數會在程式啟動時讀取和修改其值會被忽略，在執行階段 (例如，使用[_putenv、 _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

|環境變數|描述|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|修改的行為[排程](openmp-clauses.md#schedule)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。|
|[OMP_NUM_THREADS](#omp-num-threads)|在平行區域中，設定執行緒數目上限，但覆寫[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或是[num_threads](openmp-clauses.md#num-threads)。|
|[OMP_DYNAMIC](#omp-dynamic)|指定執行階段的 OpenMP 是否可調整的平行區域中的執行緒數目。|
|[OMP_NESTED](#omp-nested)|指定是否巢狀平行處理原則已啟用，除非已啟用或停用巢狀平行處理原則`omp_set_nested`。|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

指定執行階段的 OpenMP 是否可調整的平行區域中的執行緒數目。

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

`OMP_DYNAMIC`環境變數可以覆寫[omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函式。

視覺效果中的預設值C++實作的 OpenMP 標準`OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱 < [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>範例

下列命令`OMP_DYNAMIC`環境變數設為 TRUE:

```
set OMP_DYNAMIC=TRUE
```

下列命令會顯示目前的設定`OMP_DYNAMIC`環境變數：

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

指定是否巢狀平行處理原則已啟用，除非已啟用或停用巢狀平行處理原則`omp_set_nested`。

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>備註

`OMP_NESTED`環境變數可以覆寫[omp_set_nested](openmp-functions.md#omp-set-nested)函式。

視覺效果中的預設值C++實作的 OpenMP 標準`OMP_DYNAMIC=FALSE`。

如需詳細資訊，請參閱 < [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>範例

下列命令`OMP_NESTED`環境變數設為 TRUE:

```
set OMP_NESTED=TRUE
```

下列命令會顯示目前的設定`OMP_NESTED`環境變數：

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

在平行區域中，設定執行緒數目上限，但覆寫[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或是[num_threads](openmp-clauses.md#num-threads)。

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>參數

*num*<br/>
您想要在平行區域中，最多 64 視覺效果中的執行緒數目上限C++實作。

### <a name="remarks"></a>備註

`OMP_NUM_THREADS`環境變數可以覆寫[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函式或由[num_threads](openmp-clauses.md#num-threads)。

預設值`num`視覺效果中C++實作的 OpenMP 標準是虛擬處理器，包括超執行緒 Cpu 的數目。

如需詳細資訊，請參閱 < [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>範例

下列命令`OMP_NUM_THREADS`環境變數，以`16`:

```
set OMP_NUM_THREADS=16
```

下列命令會顯示目前的設定`OMP_NUM_THREADS`環境變數：

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

修改的行為[排程](openmp-clauses.md#schedule)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>參數

*size*<br/>
（選擇性）指定反覆項目的大小。 *大小*必須是正整數。 預設值是`1`，除非*型別*是靜態的。 不是有效的 when*型別*是`runtime`。

*type*<br/>
此種類的排程，請`dynamic`， `guided`， `runtime`，或`static`。

### <a name="remarks"></a>備註

視覺效果中的預設值C++實作的 OpenMP 標準`OMP_SCHEDULE=static,0`。

如需詳細資訊，請參閱 < [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>範例

下列命令`OMP_SCHEDULE`環境變數：

```
set OMP_SCHEDULE="guided,2"
```

下列命令會顯示目前的設定`OMP_SCHEDULE`環境變數：

```
set OMP_SCHEDULE
```
