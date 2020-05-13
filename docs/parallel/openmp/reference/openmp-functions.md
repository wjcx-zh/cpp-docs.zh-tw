---
title: OpenMP 函式
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317128"
---
# <a name="openmp-functions"></a>OpenMP 函式

提供指向OpenMP API 中使用的函數的連結。

OpenMP 標準的可視化C++實現包括以下功能和數據類型。

對環境執行:

|函式|描述|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|設置即將到來的並行區域中的線程數,除非被[num_threads](openmp-clauses.md#num-threads)子句覆蓋。|
|[omp_get_num_threads](#omp-get-num-threads)|返回並行區域中的線程數。|
|[omp_get_max_threads](#omp-get-max-threads)|返回等於或大於在代碼中未[num_threads](openmp-clauses.md#num-threads)的並行區域時可用的線程數的整數。|
|[omp_get_thread_num](#omp-get-thread-num)|返回在其線程團隊中執行的線程的線程數。|
|[omp_get_num_procs](#omp-get-num-procs)|返回調用函數時可用的處理器數。|
|[omp_in_parallel](#omp-in-parallel)|如果從並行區域內調用,則返回非零。|
|[omp_set_dynamic](#omp-set-dynamic)|指示可以按運行時調整即將顯示的並列區域中的可用線程數。|
|[omp_get_dynamic](#omp-get-dynamic)|返回一個值,指示未來並行區域中可用的線程數是否可以按運行時進行調整。|
|[omp_set_nested](#omp-set-nested)|啟用嵌套並行性。|
|[omp_get_nested](#omp-get-nested)|返回指示是否啟用嵌套並行性的值。|

對於鎖:

|函式|描述|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|初始化一個簡單的鎖。|
|[omp_init_nest_lock](#omp-init-nest-lock)|初始化鎖。|
|[omp_destroy_lock](#omp-destroy-lock)|取消初始化鎖。|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|取消初始化可嵌套鎖。|
|[omp_set_lock](#omp-set-lock)|阻止線程執行,直到鎖可用。|
|[omp_set_nest_lock](#omp-set-nest-lock)|阻止線程執行,直到鎖可用。|
|[omp_unset_lock](#omp-unset-lock)|釋放鎖。|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|釋放可嵌套鎖。|
|[omp_test_lock](#omp-test-lock)|嘗試設置鎖,但不阻止線程執行。|
|[omp_test_nest_lock](#omp-test-nest-lock)|嘗試設置可嵌套鎖,但不阻止線程執行。|

|資料類型|描述|
|---------|-----------|
|`omp_lock_t`|一種類型,用於保存鎖的狀態、鎖是否可用或線程是否擁有鎖。|
|`omp_nest_lock_t`|一種類型,它保存有關鎖的以下資訊之一:鎖是否可用,以及擁有鎖和嵌套計數的線程的標識。|

對於計時例程:

|函式|描述|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|返回從某個點開始的時間的秒數的值。|
|[omp_get_wtick](#omp-get-wtick)|返回處理器時鐘刻度之間的秒數。|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

取消初始化鎖。

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_lock_t`omp_init_lock 初始化的類型變數[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.2omp_destroy_lock和omp_destroy_nest_lock函數](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

有關使用`omp_destroy_lock`的示例,請參閱[omp_init_lock。](#omp-init-lock)

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

取消初始化可嵌套鎖。

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_nest_lock_t`omp_init_nest_lock初始化的類型變數。 [omp_init_nest_lock](#omp-init-nest-lock)

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.2omp_destroy_lock和omp_destroy_nest_lock函數](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

有關使用`omp_destroy_nest_lock`的示例,請參閱[omp_init_nest_lock。](#omp-init-nest-lock)

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

返回一個值,指示未來並行區域中可用的線程數是否可以按運行時進行調整。

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>傳回值

非零值表示線程將被動態調整。

### <a name="remarks"></a>備註

使用[omp_set_dynamic](#omp-set-dynamic)和[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)指定線程的動態調整。

有關詳細資訊,請參閱[3.1.7 omp_set_dynamic函數](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>範例

有關使用`omp_get_dynamic`的示例,請參閱[omp_set_dynamic。](#omp-set-dynamic)

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

返回等於或大於在代碼中未[num_threads](openmp-clauses.md#num-threads)的並行區域時可用的線程數的整數。

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.3 omp_get_max_threads函數](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。

### <a name="example"></a>範例

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

返回指示是否啟用嵌套並行性的值。

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>傳回值

非零值表示已啟用嵌套並行性。

### <a name="remarks"></a>備註

嵌套並行[性指定omp_set_nested](#omp-set-nested)和[OMP_NESTED。](openmp-environment-variables.md#omp-nested)

有關詳細資訊,請參閱[3.1.10 omp_get_nested函數](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。

### <a name="example"></a>範例

有關使用`omp_get_nested`的示例,請參閱[omp_set_nested。](#omp-set-nested)

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

返回調用函數時可用的處理器數。

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.5 omp_get_num_procs函數](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)。

### <a name="example"></a>範例

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

返回並行區域中的線程數。

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.2 omp_get_num_threads函數](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)。

### <a name="example"></a>範例

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

返回在其線程團隊中執行的線程的線程數。

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.4 omp_get_thread_num函數](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)。

### <a name="example"></a>範例

有關[parallel](openmp-directives.md#parallel)`omp_get_thread_num`使用的示例,請參閱並行。

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

返回處理器時鐘刻度之間的秒數。

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.3.2 omp_get_wtick函數](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md)。

### <a name="example"></a>範例

有關使用`omp_get_wtick`的示例,請參閱[omp_get_wtime。](#omp-get-wtime)

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

返回從某個點開始的時間的秒數的值。

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>傳回值

返回從任意但一致的點經過的時間數秒的值。

### <a name="remarks"></a>備註

在程序執行期間,該點將保持一致,從而可以進行後續比較。

有關詳細資訊,請參閱[3.3.1 omp_get_wtime函數](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。

### <a name="example"></a>範例

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

如果從並行區域內調用,則返回非零。

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.6 omp_in_parallel函數](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md)。

### <a name="example"></a>範例

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

初始化一個簡單的鎖。

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
類型為 `omp_lock_t` 的變數。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.1 omp_init_lock和omp_init_nest_lock函數](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

### <a name="example"></a>範例

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

初始化鎖。

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
類型為 `omp_nest_lock_t` 的變數。

### <a name="remarks"></a>備註

初始嵌套計數為零。

有關詳細資訊,請參閱[3.2.1 omp_init_lock和omp_init_nest_lock函數](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

### <a name="example"></a>範例

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>omp_set_dynamic

指示可以按運行時調整即將顯示的並列區域中的可用線程數。

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
指示即將推出的並行區域中的可用線程數是否可以由運行時調整的值。 如果為非零,運行時可以調整線程數(如果為零)運行時不會動態調整線程數。

### <a name="remarks"></a>備註

線程數永遠不會超過[omp_set_num_threads](#omp-set-num-threads)或[OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)設置的值。

使用[omp_get_dynamic](#omp-get-dynamic)顯示`omp_set_dynamic`的 當前設定。

的`omp_set_dynamic`設置將覆蓋[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)環境變數的設置。

有關詳細資訊,請參閱[3.1.7 omp_set_dynamic函數](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>範例

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

阻止線程執行,直到鎖可用。

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_lock_t`omp_init_lock 初始化的類型變數[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.3 omp_set_lock和omp_set_nest_lock函數](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

有關使用`omp_set_lock`的示例,請參閱[omp_init_lock。](#omp-init-lock)

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

阻止線程執行,直到鎖可用。

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_nest_lock_t`omp_init_nest_lock初始化的類型變數。 [omp_init_nest_lock](#omp-init-nest-lock)

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.3 omp_set_lock和omp_set_nest_lock函數](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

有關使用`omp_set_nest_lock`的示例,請參閱[omp_init_nest_lock。](#omp-init-nest-lock)

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>omp_set_nested

啟用嵌套並行性。

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
非零值支援嵌套並行性,而零禁用嵌套並行性。

### <a name="remarks"></a>備註

可以使用 或`omp_set_nested`設定[OMP_NESTED](openmp-environment-variables.md#omp-nested)環境變數打開 OMP 嵌套並行性。

的`omp_set_nested`設置將覆蓋環境變數的`OMP_NESTED`設置。

啟用環境變數可能會破壞其他操作程式,因為嵌套並行區域時線程數呈指數級增長。 例如,將 OMP 線程數設置為 4 時重新詛咒六次的函數需要 4,096 個(4 到 6 個線程的功率)。 除了 I/O 綁定應用程式外,如果線程數多於處理器,則應用程式的性能通常會降低。

使用[omp_get_nested](#omp-get-nested)`omp_set_nested`顯示的 當前設定。

有關詳細資訊,請參閱[3.1.9 omp_set_nested函數](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。

### <a name="example"></a>範例

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>omp_set_num_threads

設置即將到來的並行區域中的線程數,除非被[num_threads](openmp-clauses.md#num-threads)子句覆蓋。

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>參數

*num_threads*<br/>
並行區域中的線程數。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.1.1 omp_set_num_threads函數](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。

### <a name="example"></a>範例

有關使用`omp_set_num_threads`的示例,請參閱[omp_get_num_threads。](#omp-get-num-threads)

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

嘗試設置鎖,但不阻止線程執行。

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_lock_t`omp_init_lock 初始化的類型變數[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.5 omp_test_lock和omp_test_nest_lock函數](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

### <a name="example"></a>範例

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

嘗試設置可嵌套鎖,但不阻止線程執行。

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用`omp_nest_lock_t`omp_init_nest_lock初始化的類型變數。 [omp_init_nest_lock](#omp-init-nest-lock)

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.5 omp_test_lock和omp_test_nest_lock函數](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

### <a name="example"></a>範例

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

釋放鎖。

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
類型變數`omp_lock_t`,用[omp_init_lock](#omp-init-lock)初始化,由線程擁有並在函數中執行。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.4 omp_unset_lock和omp_unset_nest_lock函數](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

有關使用`omp_unset_lock`的示例,請參閱[omp_init_lock。](#omp-init-lock)

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

釋放可嵌套鎖。

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
使用omp_init_nest_lock初始化`omp_nest_lock_t`的類型變數,由線程[omp_init_nest_lock](#omp-init-nest-lock)擁有並在函數中執行。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[3.2.4 omp_unset_lock和omp_unset_nest_lock函數](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

有關使用`omp_unset_nest_lock`的示例,請參閱[omp_init_nest_lock。](#omp-init-nest-lock)
