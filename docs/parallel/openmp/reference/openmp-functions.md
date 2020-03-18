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
ms.openlocfilehash: 4508c683ff5d4bece290b7fef2bbd83ae8023eac
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416995"
---
# <a name="openmp-functions"></a>OpenMP 函式

提供 OpenMP API 中使用之函式的連結。

OpenMP 標準C++的視覺化執行包含下列函數和資料類型。

針對環境執行：

|函數|描述|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|設定近期平列區域中的執行緒數目，除非是由[num_threads](openmp-clauses.md#num-threads)子句覆寫。|
|[omp_get_num_threads](#omp-get-num-threads)|傳回平列區域中的執行緒數目。|
|[omp_get_max_threads](#omp-get-max-threads)|傳回大於或等於執行緒數目的整數，如果沒有[num_threads](openmp-clauses.md#num-threads)的平列區域定義于程式碼中的該點上，就可以使用。|
|[omp_get_thread_num](#omp-get-thread-num)|傳回執行緒在其執行緒小組內執行的執行緒數目。|
|[omp_get_num_procs](#omp-get-num-procs)|傳回呼叫函數時可用的處理器數目。|
|[omp_in_parallel](#omp-in-parallel)|如果從平列區域內呼叫，則傳回非零。|
|[omp_set_dynamic](#omp-set-dynamic)|表示可由執行時間調整即將到來的平列區域中可用的執行緒數目。|
|[omp_get_dynamic](#omp-get-dynamic)|傳回值，指出即將推出的平列區域中可用的執行緒數目是否可以由執行時間調整。|
|[omp_set_nested](#omp-set-nested)|啟用嵌套的平行處理原則。|
|[omp_get_nested](#omp-get-nested)|傳回值，指出是否已啟用嵌套平行處理原則。|

針對鎖定：

|函數|描述|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|初始化簡單鎖定。|
|[omp_init_nest_lock](#omp-init-nest-lock)|初始化鎖定。|
|[omp_destroy_lock](#omp-destroy-lock)|取消初始化鎖定。|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|取消初始化 nestable 鎖定。|
|[omp_set_lock](#omp-set-lock)|封鎖執行緒執行，直到有可用的鎖定為止。|
|[omp_set_nest_lock](#omp-set-nest-lock)|封鎖執行緒執行，直到有可用的鎖定為止。|
|[omp_unset_lock](#omp-unset-lock)|釋放鎖定。|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|釋放 nestable 鎖定。|
|[omp_test_lock](#omp-test-lock)|嘗試設定鎖定，但不會封鎖執行緒執行。|
|[omp_test_nest_lock](#omp-test-nest-lock)|嘗試設定 nestable 鎖定，但不會封鎖執行緒執行。|

|資料類型|描述|
|---------|-----------|
|`omp_lock_t`|一種類型，可保存鎖定的狀態、是否可以使用鎖定，或執行緒是否擁有鎖定。|
|`omp_nest_lock_t`|一種類型，保存有關鎖定的下列其中一項資訊：是否可以使用鎖定，以及擁有鎖定的執行緒識別和嵌套計數。|

針對計時常式：

|函數|描述|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|以秒為單位傳回某個時間點經過的值。|
|[omp_get_wtick](#omp-get-wtick)|傳回處理器時鐘刻度之間的秒數。|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

取消初始化鎖定。

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_lock_t` 的類型變數，其已使用[omp_init_lock](#omp-init-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函數](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

如需使用 `omp_destroy_lock`的範例，請參閱[omp_init_lock](#omp-init-lock) 。

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

取消初始化 nestable 鎖定。

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_nest_lock_t` 的類型變數，其已使用[omp_init_nest_lock](#omp-init-nest-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函數](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

如需使用 `omp_destroy_nest_lock`的範例，請參閱[omp_init_nest_lock](#omp-init-nest-lock) 。

## <a name="omp-get-dynamic"></a>omp_get_dynamic

傳回值，指出即將推出的平列區域中可用的執行緒數目是否可以由執行時間調整。

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>傳回值

非零值表示執行緒會以動態方式調整。

### <a name="remarks"></a>備註

執行緒的動態調整是以[omp_set_dynamic](#omp-set-dynamic)和[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)來指定。

如需詳細資訊，請參閱[3.1.7 omp_set_dynamic 函數](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>範例

如需使用 `omp_get_dynamic`的範例，請參閱[omp_set_dynamic](#omp-set-dynamic) 。

## <a name="omp-get-max-threads"></a>omp_get_max_threads

傳回大於或等於執行緒數目的整數，如果沒有[num_threads](openmp-clauses.md#num-threads)的平列區域定義于程式碼中的該點上，就可以使用。

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.3 omp_get_max_threads 函數](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。

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

## <a name="omp-get-nested"></a>omp_get_nested

傳回值，指出是否已啟用嵌套平行處理原則。

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>傳回值

非零值表示已啟用「嵌套平行處理原則」。

### <a name="remarks"></a>備註

使用[omp_set_nested](#omp-set-nested)和[OMP_NESTED](openmp-environment-variables.md#omp-nested)來指定嵌套的平行處理原則。

如需詳細資訊，請參閱[3.1.10 omp_get_nested 函數](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。

### <a name="example"></a>範例

如需使用 `omp_get_nested`的範例，請參閱[omp_set_nested](#omp-set-nested) 。

## <a name="omp-get-num-procs"></a>omp_get_num_procs

傳回呼叫函數時可用的處理器數目。

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.5 omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)函式。

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

## <a name="omp-get-num-threads"></a>omp_get_num_threads

傳回平列區域中的執行緒數目。

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.2 omp_get_num_threads 函數](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)。

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

## <a name="omp-get-thread-num"></a>omp_get_thread_num

傳回執行緒在其執行緒小組內執行的執行緒數目。

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.4 omp_get_thread_num 函數](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)。

### <a name="example"></a>範例

如需使用 `omp_get_thread_num`的範例，請參閱[parallel](openmp-directives.md#parallel) 。

## <a name="omp-get-wtick"></a>omp_get_wtick

傳回處理器時鐘刻度之間的秒數。

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.3.2 omp_get_wtick 函數](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md)。

### <a name="example"></a>範例

如需使用 `omp_get_wtick`的範例，請參閱[omp_get_wtime](#omp-get-wtime) 。

## <a name="omp-get-wtime"></a>omp_get_wtime

以秒為單位傳回某個時間點經過的值。

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>傳回值

傳回一個值，以秒為單位，從部分任意但一致的時間點開始算起。

### <a name="remarks"></a>備註

該點在程式執行期間會保持一致，因此可能會進行近期比較。

如需詳細資訊，請參閱[3.3.1 omp_get_wtime 函數](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。

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

## <a name="omp-in-parallel"></a>omp_in_parallel

如果從平列區域內呼叫，則傳回非零。

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.6 omp_in_parallel 函數](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md)。

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

## <a name="omp-init-lock"></a>omp_init_lock

初始化簡單鎖定。

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型為 `omp_lock_t` 的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.1 omp_init_lock 和 omp_init_nest_lock 函數](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

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

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

初始化鎖定。

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型為 `omp_nest_lock_t` 的變數。

### <a name="remarks"></a>備註

初始的嵌套計數為零。

如需詳細資訊，請參閱[3.2.1 omp_init_lock 和 omp_init_nest_lock 函數](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

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

## <a name="omp-set-dynamic"></a>omp_set_dynamic

表示可由執行時間調整即將到來的平列區域中可用的執行緒數目。

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>參數

*val*<br/>
值，指出執行時間是否可以調整即將推出的平列區域中可用的執行緒數目。 如果是非零值，執行時間可以調整執行緒的數目，如果為零，執行時間就不會動態調整執行緒的數目。

### <a name="remarks"></a>備註

執行緒的數目永遠不會超過[omp_set_num_threads](#omp-set-num-threads)或[OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)所設定的值。

使用 [ [omp_get_dynamic](#omp-get-dynamic) ] 顯示目前的 `omp_set_dynamic`設定。

`omp_set_dynamic` 的設定將會覆寫[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)環境變數的設定。

如需詳細資訊，請參閱[3.1.7 omp_set_dynamic 函數](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

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

## <a name="omp-set-lock"></a>omp_set_lock

封鎖執行緒執行，直到有可用的鎖定為止。

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_lock_t` 的類型變數，其已使用[omp_init_lock](#omp-init-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.3 omp_set_lock 和 omp_set_nest_lock 函數](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

如需使用 `omp_set_lock`的範例，請參閱[omp_init_lock](#omp-init-lock) 。

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

封鎖執行緒執行，直到有可用的鎖定為止。

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_nest_lock_t` 的類型變數，其已使用[omp_init_nest_lock](#omp-init-nest-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.3 omp_set_lock 和 omp_set_nest_lock 函數](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

如需使用 `omp_set_nest_lock`的範例，請參閱[omp_init_nest_lock](#omp-init-nest-lock) 。

## <a name="omp-set-nested"></a>omp_set_nested

啟用嵌套的平行處理原則。

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>參數

*val*<br/>
非零值會啟用嵌套平行處理原則，而零則會停用嵌套平行處理原則。

### <a name="remarks"></a>備註

您可以使用 `omp_set_nested`或藉由設定[OMP_NESTED](openmp-environment-variables.md#omp-nested)環境變數，來開啟 OMP 的嵌套平行處理原則。

`omp_set_nested` 的設定將會覆寫 `OMP_NESTED` 環境變數的設定。

啟用環境變數可能會中斷另一個操作程式，因為當嵌套平列區域時，執行緒數目會以指數方式增加。 例如，recurses 六次且 OMP 執行緒數目設定為4的函式，需要4096（4到6個）執行緒的乘冪。 除了 i/o 系結的應用程式，應用程式的效能通常會隨著執行緒數目超過處理器而降低。

使用 [ [omp_get_nested](#omp-get-nested) ] 顯示目前的 `omp_set_nested`設定。

如需詳細資訊，請參閱[3.1.9 omp_set_nested 函數](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。

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

## <a name="omp-set-num-threads"></a>omp_set_num_threads

設定近期平列區域中的執行緒數目，除非是由[num_threads](openmp-clauses.md#num-threads)子句覆寫。

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>參數

*num_threads*<br/>
平列區域中的執行緒數目。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.1.1 omp_set_num_threads 函數](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。

### <a name="example"></a>範例

如需使用 `omp_set_num_threads`的範例，請參閱[omp_get_num_threads](#omp-get-num-threads) 。

## <a name="omp-test-lock"></a>omp_test_lock

嘗試設定鎖定，但不會封鎖執行緒執行。

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_lock_t` 的類型變數，其已使用[omp_init_lock](#omp-init-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.5 omp_test_lock 和 omp_test_nest_lock 函數](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

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

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

嘗試設定 nestable 鎖定，但不會封鎖執行緒執行。

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_nest_lock_t` 的類型變數，其已使用[omp_init_nest_lock](#omp-init-nest-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.5 omp_test_lock 和 omp_test_nest_lock 函數](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

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

## <a name="omp-unset-lock"></a>omp_unset_lock

釋放鎖定。

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_lock_t` 類型的變數，其使用由執行緒所擁有並在函式中執行的[omp_init_lock](#omp-init-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函數](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

如需使用 `omp_unset_lock`的範例，請參閱[omp_init_lock](#omp-init-lock) 。

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

釋放 nestable 鎖定。

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
`omp_nest_lock_t` 類型的變數，其使用由執行緒所擁有並在函式中執行的[omp_init_nest_lock](#omp-init-nest-lock)初始化。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函數](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

如需使用 `omp_unset_nest_lock`的範例，請參閱[omp_init_nest_lock](#omp-init-nest-lock) 。
