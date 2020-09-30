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
ms.openlocfilehash: 660d786148738c8ce998ad5d78645efdb444ea47
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503702"
---
# <a name="openmp-functions"></a>OpenMP 函式

提供 OpenMP API 中使用之函式的連結。

OpenMP 標準的 Visual C++ 執行包含下列函數和資料類型。

針對環境執行：

|函式|描述|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|設定即將進行的平列區域中的執行緒數目，除非由 [num_threads](openmp-clauses.md#num-threads) 子句覆寫。|
|[omp_get_num_threads](#omp-get-num-threads)|傳回平列區域中的執行緒數目。|
|[omp_get_max_threads](#omp-get-max-threads)|如果沒有 [num_threads](openmp-clauses.md#num-threads) 的平列區域是在程式碼中的那一點定義的，則會傳回等於或大於可以使用的執行緒數目的整數。|
|[omp_get_thread_num](#omp-get-thread-num)|傳回執行緒線上程小組內執行的執行緒數目。|
|[omp_get_num_procs](#omp-get-num-procs)|傳回呼叫函數時可使用的處理器數目。|
|[omp_in_parallel](#omp-in-parallel)|如果從平列區域內呼叫，則傳回非零。|
|[omp_set_dynamic](#omp-set-dynamic)|指出即將推出的平列區域中可用的執行緒數目可依執行時間調整。|
|[omp_get_dynamic](#omp-get-dynamic)|傳回值，這個值表示執行時間是否可以調整即將存在之平列區域中可用的執行緒數目。|
|[omp_set_nested](#omp-set-nested)|啟用嵌套平行處理原則。|
|[omp_get_nested](#omp-get-nested)|傳回值，這個值會指出是否已啟用嵌套平行處理原則。|

針對鎖定：

|函式|描述|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|初始化簡單鎖定。|
|[omp_init_nest_lock](#omp-init-nest-lock)|初始化鎖定。|
|[omp_destroy_lock](#omp-destroy-lock)|取消初始化鎖定。|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|取消初始化 nestable 鎖定。|
|[omp_set_lock](#omp-set-lock)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_set_nest_lock](#omp-set-nest-lock)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_unset_lock](#omp-unset-lock)|釋放鎖定。|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|釋放 nestable 鎖定。|
|[omp_test_lock](#omp-test-lock)|嘗試設定鎖定，但不會封鎖執行緒執行。|
|[omp_test_nest_lock](#omp-test-nest-lock)|嘗試設定 nestable 鎖定，但不會封鎖執行緒執行。|

|資料類型|描述|
|---------|-----------|
|`omp_lock_t`|一種類型，可保存鎖定的狀態、鎖定是否可用，或執行緒是否擁有鎖定。|
|`omp_nest_lock_t`|一種類型，其中包含有關鎖定的下列其中一項資訊：鎖定是否可用，以及擁有鎖定之執行緒的識別和嵌套計數。|

針對計時常式：

|函式|描述|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|傳回某個時間點所經過時間的值（以秒為單位）。|
|[omp_get_wtick](#omp-get-wtick)|傳回處理器時鐘刻度之間的秒數。|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a> omp_destroy_lock

取消初始化鎖定。

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_lock_t`使用[omp_init_lock](#omp-init-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函數](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_init_lock](#omp-init-lock) `omp_destroy_lock` 。

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a> omp_destroy_nest_lock

取消初始化 nestable 鎖定。

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_nest_lock_t`使用[omp_init_nest_lock](#omp-init-nest-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函數](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_init_nest_lock](#omp-init-nest-lock) `omp_destroy_nest_lock` 。

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a> omp_get_dynamic

傳回值，這個值表示執行時間是否可以調整即將存在之平列區域中可用的執行緒數目。

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>傳回值

非零值表示執行緒將會動態調整。

### <a name="remarks"></a>備註

動態調整執行緒是以 [omp_set_dynamic](#omp-set-dynamic) 和 [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)指定。

如需詳細資訊，請參閱 [3.1.7 omp_set_dynamic](../3-run-time-library-functions.md#317-omp_set_dynamic-function)函式。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_set_dynamic](#omp-set-dynamic) `omp_get_dynamic` 。

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a> omp_get_max_threads

如果沒有 [num_threads](openmp-clauses.md#num-threads) 的平列區域是在程式碼中的那一點定義的，則會傳回等於或大於可以使用的執行緒數目的整數。

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.3 omp_get_max_threads](../3-run-time-library-functions.md#313-omp_get_max_threads-function)函式。

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a> omp_get_nested

傳回值，這個值會指出是否已啟用嵌套平行處理原則。

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>傳回值

非零值表示已啟用嵌套平行處理原則。

### <a name="remarks"></a>備註

使用 [omp_set_nested](#omp-set-nested) 和 [OMP_NESTED](openmp-environment-variables.md#omp-nested)來指定嵌套平行處理原則。

如需詳細資訊，請參閱 [3.1.10 omp_get_nested](../3-run-time-library-functions.md#3110-omp_get_nested-function)函式。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_set_nested](#omp-set-nested) `omp_get_nested` 。

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a> omp_get_num_procs

傳回呼叫函數時可使用的處理器數目。

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.5 omp_get_num_procs](../3-run-time-library-functions.md#315-omp_get_num_procs-function)函式。

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a> omp_get_num_threads

傳回平列區域中的執行緒數目。

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.2 omp_get_num_threads](../3-run-time-library-functions.md#312-omp_get_num_threads-function)函式。

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a> omp_get_thread_num

傳回執行緒線上程小組內執行的執行緒數目。

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.4 omp_get_thread_num](../3-run-time-library-functions.md#314-omp_get_thread_num-function)函式。

### <a name="example"></a>範例

如需使用的範例，請參閱 [平行](openmp-directives.md#parallel) `omp_get_thread_num` 。

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a> omp_get_wtick

傳回處理器時鐘刻度之間的秒數。

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.3.2 omp_get_wtick](../3-run-time-library-functions.md#332-omp_get_wtick-function)函式。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_get_wtime](#omp-get-wtime) `omp_get_wtick` 。

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a> omp_get_wtime

傳回某個時間點所經過時間的值（以秒為單位）。

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>傳回值

傳回以秒為單位的值，從部分任意但一致的點開始算起。

### <a name="remarks"></a>備註

該點在程式執行期間會保持一致，因此可能會產生後續的比較。

如需詳細資訊，請參閱 [3.3.1 omp_get_wtime](../3-run-time-library-functions.md#331-omp_get_wtime-function)函式。

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a> omp_in_parallel

如果從平列區域內呼叫，則傳回非零。

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.6 omp_in_parallel](../3-run-time-library-functions.md#316-omp_in_parallel-function)函式。

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a> omp_init_lock

初始化簡單鎖定。

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
類型為 `omp_lock_t` 的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.1 omp_init_lock 和 omp_init_nest_lock 函數](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)。

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a> omp_init_nest_lock

初始化鎖定。

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
類型為 `omp_nest_lock_t` 的變數。

### <a name="remarks"></a>備註

初始的嵌套計數為零。

如需詳細資訊，請參閱 [3.2.1 omp_init_lock 和 omp_init_nest_lock 函數](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)。

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a> omp_set_dynamic

指出即將推出的平列區域中可用的執行緒數目可依執行時間調整。

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
值，這個值表示執行時間是否可以調整即將存在之平列區域中可用的執行緒數目。 若為非零值，執行時間可以調整執行緒的數目，如果為零，則執行時間不會動態調整執行緒數目。

### <a name="remarks"></a>備註

執行緒數目絕不會超過 [omp_set_num_threads](#omp-set-num-threads) 或 [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)所設定的值。

使用 [omp_get_dynamic](#omp-get-dynamic) 來顯示目前的設定 `omp_set_dynamic` 。

的設定 `omp_set_dynamic` 會覆寫 [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) 環境變數的設定。

如需詳細資訊，請參閱 [3.1.7 omp_set_dynamic](../3-run-time-library-functions.md#317-omp_set_dynamic-function)函式。

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a> omp_set_lock

封鎖執行緒執行，直到鎖定可用為止。

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_lock_t`使用[omp_init_lock](#omp-init-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.3 omp_set_lock 和 omp_set_nest_lock 函數](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions)。

### <a name="examples"></a>範例

如需使用的範例，請參閱 [omp_init_lock](#omp-init-lock) `omp_set_lock` 。

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a> omp_set_nest_lock

封鎖執行緒執行，直到鎖定可用為止。

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_nest_lock_t`使用[omp_init_nest_lock](#omp-init-nest-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.3 omp_set_lock 和 omp_set_nest_lock 函數](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions)。

### <a name="examples"></a>範例

如需使用的範例，請參閱 [omp_init_nest_lock](#omp-init-nest-lock) `omp_set_nest_lock` 。

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a> omp_set_nested

啟用嵌套平行處理原則。

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
非零值會啟用嵌套平行處理原則，而零則會停用嵌套平行處理原則。

### <a name="remarks"></a>備註

您可以使用 `omp_set_nested` 或藉由設定 [OMP_NESTED](openmp-environment-variables.md#omp-nested) 環境變數來開啟 OMP 的嵌套平行處理原則。

的設定 `omp_set_nested` 會覆寫環境變數的設定 `OMP_NESTED` 。

啟用環境變數可能會中斷其他的操作程式，因為當嵌套平列區域時，執行緒的數目會以指數方式增加。 例如，recurses 6 次且將 OMP 執行緒數目設定為4的函式，需要 4096 (4 到 6) 執行緒的能力。 除了 i/o 系結的應用程式，應用程式的效能通常會線上程數目超過處理器時降低。

使用 [omp_get_nested](#omp-get-nested) 來顯示目前的設定 `omp_set_nested` 。

如需詳細資訊，請參閱 [3.1.9 omp_set_nested](../3-run-time-library-functions.md#319-omp_set_nested-function)函式。

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a> omp_set_num_threads

設定即將進行的平列區域中的執行緒數目，除非由 [num_threads](openmp-clauses.md#num-threads) 子句覆寫。

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>參數

*num_threads*<br/>
平列區域中的執行緒數目。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.1.1 omp_set_num_threads](../3-run-time-library-functions.md#311-omp_set_num_threads-function)函式。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_get_num_threads](#omp-get-num-threads) `omp_set_num_threads` 。

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a> omp_test_lock

嘗試設定鎖定，但不會封鎖執行緒執行。

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_lock_t`使用[omp_init_lock](#omp-init-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.5 omp_test_lock 和 omp_test_nest_lock 函數](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions)。

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a> omp_test_nest_lock

嘗試設定 nestable 鎖定，但不會封鎖執行緒執行。

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
`omp_nest_lock_t`使用[omp_init_nest_lock](#omp-init-nest-lock)初始化之類型的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.5 omp_test_lock 和 omp_test_nest_lock 函數](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions)。

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a> omp_unset_lock

釋放鎖定。

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
型別的變數，此變數 `omp_lock_t` 是使用由執行緒所擁有並在函式中執行的 [omp_init_lock](#omp-init-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函數](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions)。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_init_lock](#omp-init-lock) `omp_unset_lock` 。

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a> omp_unset_nest_lock

釋放 nestable 鎖定。

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*鎖*<br/>
型別的變數，此變數 `omp_nest_lock_t` 是使用由執行緒所擁有並在函式中執行的 [omp_init_nest_lock](#omp-init-nest-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函數](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions)。

### <a name="example"></a>範例

如需使用的範例，請參閱 [omp_init_nest_lock](#omp-init-nest-lock) `omp_unset_nest_lock` 。
