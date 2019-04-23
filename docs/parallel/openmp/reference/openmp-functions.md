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
ms.openlocfilehash: 1bf0e08f3b28368d9aea5438b3036ac8a0283735
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124976"
---
# <a name="openmp-functions"></a>OpenMP 函式

提供在 OpenMP API 中使用的函式連結。

視覺效果C++實作的 OpenMP 標準包含下列函式和資料類型。

環境執行：

|功能|描述|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|在即將推出的平行區域，設定執行緒數目，但覆寫[num_threads](openmp-clauses.md#num-threads)子句。|
|[omp_get_num_threads](#omp-get-num-threads)|傳回平行的區域中的執行緒數目。|
|[omp_get_max_threads](#omp-get-max-threads)|傳回一個整數，等於或大於會時才可用在平行區域，而不需要的執行緒數目[num_threads](openmp-clauses.md#num-threads)此時程式碼中定義。|
|[omp_get_thread_num](#omp-get-thread-num)|傳回其執行緒小組內的執行緒執行執行緒的數目。|
|[omp_get_num_procs](#omp-get-num-procs)|傳回可在呼叫函式的處理器數目。|
|[omp_in_parallel](#omp-in-parallel)|傳回非零值，如果從在平行區域內呼叫。|
|[omp_set_dynamic](#omp-set-dynamic)|表示執行階段可以調整即將推出的平行區域中可用的執行緒數目。|
|[omp_get_dynamic](#omp-get-dynamic)|傳回值，這個值，指出是否可以調整執行階段即將推出的平行區域中可用的執行緒數目。|
|[omp_set_nested](#omp-set-nested)|啟用巢狀平行處理原則。|
|[omp_get_nested](#omp-get-nested)|傳回值，這個值，指出是否已啟用巢狀平行處理原則。|

鎖定：

|功能|描述|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|初始化簡單的鎖定。|
|[omp_init_nest_lock](#omp-init-nest-lock)|初始化的鎖定。|
|[omp_destroy_lock](#omp-destroy-lock)|未初始化的鎖定。|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|取消初始化可巢狀鎖定。|
|[omp_set_lock](#omp-set-lock)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_set_nest_lock](#omp-set-nest-lock)|封鎖執行緒執行，直到鎖定可用為止。|
|[omp_unset_lock](#omp-unset-lock)|釋放鎖定。|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|釋出可巢狀鎖定。|
|[omp_test_lock](#omp-test-lock)|嘗試設定鎖定，但不會封鎖執行緒的執行。|
|[omp_test_nest_lock](#omp-test-nest-lock)|嘗試設定可巢狀鎖定，但不會封鎖執行緒的執行。|

|資料類型|描述|
|---------|-----------|
|`omp_lock_t`|保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。|
|`omp_nest_lock_t`|保留鎖定的相關資訊的下列項目之一的類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。|

計時常式：

|功能|描述|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|傳回值，以秒為單位的時間之間所經歷的某個時間點。|
|[omp_get_wtick](#omp-get-wtick)|傳回處理器時鐘刻度之間的秒數。|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

未初始化的鎖定。

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_lock_t`，初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_lock](#omp-init-lock)如需使用的範例`omp_destroy_lock`。

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

取消初始化可巢狀鎖定。

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_nest_lock_t`，初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_nest_lock](#omp-init-nest-lock)如需使用的範例`omp_destroy_nest_lock`。

## <a name="omp-get-dynamic"></a>omp_get_dynamic

傳回值，這個值，指出是否可以調整執行階段即將推出的平行區域中可用的執行緒數目。

```
int omp_get_dynamic();
```

### <a name="return-value"></a>傳回值

非零值表示執行緒將會以動態方式調整。

### <a name="remarks"></a>備註

使用指定的執行緒的動態調整[omp_set_dynamic](#omp-set-dynamic)並[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)。

如需詳細資訊，請參閱 < [3.1.7 omp_set_dynamic 函式](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

### <a name="example"></a>範例

請參閱[omp_set_dynamic](#omp-set-dynamic)如需使用的範例`omp_get_dynamic`。

## <a name="omp-get-max-threads"></a>omp_get_max_threads

傳回一個整數，等於或大於會時才可用在平行區域，而不需要的執行緒數目[num_threads](openmp-clauses.md#num-threads)此時程式碼中定義。

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.3 omp_get_max_threads 函式](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。

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

傳回值，這個值，指出是否已啟用巢狀平行處理原則。

```
int omp_get_nested( );
```

### <a name="return-value"></a>傳回值

非零值表示啟用巢狀平行處理原則。

### <a name="remarks"></a>備註

指定巢狀平行處理原則[omp_set_nested](#omp-set-nested)並[OMP_NESTED](openmp-environment-variables.md#omp-nested)。

如需詳細資訊，請參閱 < [3.1.10 omp_get_nested 函式](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。

### <a name="example"></a>範例

請參閱[omp_set_nested](#omp-set-nested)如需使用的範例`omp_get_nested`。

## <a name="omp-get-num-procs"></a>omp_get_num_procs

傳回可在呼叫函式的處理器數目。

```
int omp_get_num_procs();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.5 omp_get_num_procs 函式](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)。

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

傳回平行的區域中的執行緒數目。

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.2 omp_get_num_threads 函式](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)。

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

傳回其執行緒小組內的執行緒執行執行緒的數目。

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.4 omp_get_thread_num 函式](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)。

### <a name="example"></a>範例

請參閱[平行](openmp-directives.md#parallel)如需使用的範例`omp_get_thread_num`。

## <a name="omp-get-wtick"></a>omp_get_wtick

傳回處理器時鐘刻度之間的秒數。

```
double omp_get_wtick( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.3.2 omp_get_wtick 函式](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md)。

### <a name="example"></a>範例

請參閱[omp_get_wtime](#omp-get-wtime)如需使用的範例`omp_get_wtick`。

## <a name="omp-get-wtime"></a>omp_get_wtime

傳回值，以秒為單位的時間之間所經歷的某個時間點。

```
double omp_get_wtime( );
```

### <a name="return-value"></a>傳回值

傳回值，以秒為單位的時間過從一些任意的但一致的點。

### <a name="remarks"></a>備註

該時間點程式執行，因此可能會即將推出的比較都會保持一致。

如需詳細資訊，請參閱 < [3.3.1 omp_get_wtime 函式](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md)。

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

傳回非零值，如果從在平行區域內呼叫。

```
int omp_in_parallel( );
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.6 omp_in_parallel 函式](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md)。

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

初始化簡單的鎖定。

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型為 `omp_lock_t` 的變數。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.1 omp_init_lock 和 omp_init_nest_lock 函式](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

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

初始化的鎖定。

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型為 `omp_nest_lock_t` 的變數。

### <a name="remarks"></a>備註

初始的巢狀計數為零。

如需詳細資訊，請參閱 < [3.2.1 omp_init_lock 和 omp_init_nest_lock 函式](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。

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

表示執行階段可以調整即將推出的平行區域中可用的執行緒數目。

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>參數

*val*<br/>
值，指出是否可以調整執行階段即將推出的平行區域中可用的執行緒數目。 如果是非零值，執行階段可以調整執行緒數目，如果是零，執行階段不會動態調整執行緒數目。

### <a name="remarks"></a>備註

執行緒的數目絕對不會超過所設定的值[omp_set_num_threads](#omp-set-num-threads)或是[OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)。

使用[omp_get_dynamic](#omp-get-dynamic)要顯示的目前設定`omp_set_dynamic`。

設定`omp_set_dynamic`會覆寫的設定[OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)環境變數。

如需詳細資訊，請參閱 < [3.1.7 omp_set_dynamic 函式](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

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

封鎖執行緒執行，直到鎖定可用為止。

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_lock_t`，初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.3 omp_set_lock 和 omp_set_nest_lock 函式](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

請參閱[omp_init_lock](#omp-init-lock)如需使用的範例`omp_set_lock`。

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

封鎖執行緒執行，直到鎖定可用為止。

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_nest_lock_t`，初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.3 omp_set_lock 和 omp_set_nest_lock 函式](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。

### <a name="examples"></a>範例

請參閱[omp_init_nest_lock](#omp-init-nest-lock)如需使用的範例`omp_set_nest_lock`。

## <a name="omp-set-nested"></a>omp_set_nested

啟用巢狀平行處理原則。

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>參數

*val*<br/>
非零值可讓巢狀的平行處理原則，而 0 會停用巢狀平行處理原則。

### <a name="remarks"></a>備註

巢狀的 OMP 平行處理原則可以與開啟`omp_set_nested`，或藉由設定[OMP_NESTED](openmp-environment-variables.md#omp-nested)環境變數。

設定`omp_set_nested`會覆寫的設定`OMP_NESTED`環境變數。

啟用環境變數可能會中斷程式否則操作，因為巢狀平行區域時，執行緒的數目以指數方式增加。 例如，遞迴六倍 OMP 設為 4 的執行緒數目而產生的函式需要 4096 (4 到 6 乘) 執行緒。 除了繫結 I/O 的應用程式，應用程式的效能通常會降低有更多的執行緒比處理器。

使用[omp_get_nested](#omp-get-nested)要顯示的目前設定`omp_set_nested`。

如需詳細資訊，請參閱 < [3.1.9 omp_set_nested 函式](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。

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

在即將推出的平行區域，設定執行緒數目，但覆寫[num_threads](openmp-clauses.md#num-threads)子句。

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>參數

*num_threads*<br/>
在平行區域中的執行緒數目。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.1.1 omp_set_num_threads 函式](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。

### <a name="example"></a>範例

請參閱[omp_get_num_threads](#omp-get-num-threads)如需使用的範例`omp_set_num_threads`。

## <a name="omp-test-lock"></a>omp_test_lock

嘗試設定鎖定，但不會封鎖執行緒的執行。

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_lock_t`，初始化[omp_init_lock](#omp-init-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.5 omp_test_lock 和 omp_test_nest_lock 函式](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

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

嘗試設定可巢狀鎖定，但不會封鎖執行緒的執行。

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_nest_lock_t`，初始化[omp_init_nest_lock](#omp-init-nest-lock)。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.5 omp_test_lock 和 omp_test_nest_lock 函式](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。

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

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_lock_t`，初始化[omp_init_lock](#omp-init-lock)、 執行緒所擁有和函式中執行。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_lock](#omp-init-lock)如需使用的範例`omp_unset_lock`。

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

釋出可巢狀鎖定。

```
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數`omp_nest_lock_t`，初始化[omp_init_nest_lock](#omp-init-nest-lock)、 執行緒所擁有和函式中執行。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_nest_lock](#omp-init-nest-lock)如需使用的範例`omp_unset_nest_lock`。
