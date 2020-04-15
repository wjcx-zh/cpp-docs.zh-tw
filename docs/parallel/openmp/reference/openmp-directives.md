---
title: OpenMP 指示詞
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366438"
---
# <a name="openmp-directives"></a>OpenMP 指示詞

提供指向OpenMP API 中使用的指令的連結。

可視C++支援以下 OpenMP 指令。

對於並行工作共用:

|指示詞|描述|
|---------|-----------|
|[parallel](#parallel)|定義一個並行區域,即將由多個線程並行執行的代碼。|
|[for](#for-openmp)|導致在並行區域內的`for`迴圈中完成的工作在線程之間分配。|
|[sections](#sections-openmp)|標識要在所有線程之間劃分的代碼節。|
|[single](#single)|允許您指定應在單個線程(不一定是主線程)上執行代碼部分。|

對於主與同步:

|指示詞|描述|
|---------|-----------|
|[master](#master)|指定只有主線程應執行程式的一個部分。|
|[關鍵](#critical)|指定代碼一次僅在一個線程上執行。|
|[障礙](#barrier)|同步團隊中的所有線程;所有線程都在屏障處暫停,直到所有線程執行障礙。|
|[不可部分完成](#atomic)|指定將以原子方式更新的記憶體位置。|
|[沖洗](#flush-openmp)|指定所有線程對所有共用物件的記憶體視圖相同。|
|[命令](#ordered-openmp-directives)|指定並行`for`迴圈下的代碼應像順序循環一樣執行。|

對資料環境:

|指示詞|描述|
|---------|-----------|
|[threadprivate](#threadprivate)|指定變數是線程的私有變數。|

## <a name="atomic"></a><a name="atomic"></a>原子

指定將以原子方式更新的記憶體位置。

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>參數

*運算式*<br/>
具有*lvalue*的語句,您希望防止其記憶體位置對多個寫入進行保護。

### <a name="remarks"></a>備註

該`atomic`指令不支援任何子句。

有關詳細資訊,請參閱[2.6.4 原子建構](../../../parallel/openmp/2-6-4-atomic-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a>障礙

同步團隊中的所有線程;所有線程都在屏障處暫停,直到所有線程執行障礙。

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>備註

該`barrier`指令不支援任何子句。

有關詳細資訊,請參閱[2.6.3 障礙指令](../../../parallel/openmp/2-6-3-barrier-directive.md)。

### <a name="example"></a>範例

有關如何使用的範例`barrier`,請參閱[master](#master)。

## <a name="critical"></a><a name="critical"></a>關鍵

指定一次僅在一個線程上執行代碼。

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>參數

*名稱*<br/>
( 選擇性的 )用於標識關鍵代碼的名稱。 名稱必須包含在括弧中。

### <a name="remarks"></a>備註

該`critical`指令不支援任何子句。

有關詳細資訊,請參閱[2.6.2 關鍵構造](../../../parallel/openmp/2-6-2-critical-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a>沖洗

指定所有線程對所有共用物件的記憶體視圖相同。

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>參數

*無 功*<br/>
( 選擇性的 )表示要同步物件的由逗號分隔的變數清單。 如果未指定*var,* 則刷新所有記憶體。

### <a name="remarks"></a>備註

該`flush`指令不支援任何子句。

有關詳細資訊,請參閱[2.6.5 刷新指令](../../../parallel/openmp/2-6-5-flush-directive.md)。

### <a name="example"></a>範例

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a>對於

導致在並行區域內的`for`迴圈中完成的工作在線程之間分配。

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>參數

*第*<br/>
( 選擇性的 )零個或多個子句,請參閱**備註**部分。

*for_statement*<br/>
循環`for`。 如果迴圈中的使用者代碼更改索引變數,`for`則會導致未定義的行為。

### <a name="remarks"></a>備註

這個`for`指令支援以下子句:

- [私人](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [命令](openmp-clauses.md#ordered-openmp-clauses)
- [附表](openmp-clauses.md#schedule)
- [不要等待](openmp-clauses.md#nowait)

如果`parallel``clauses`也指定,可以`parallel`是`for`或指令接受的任何子句`nowait`,但 除外。

有關詳細資訊,請參閱[2.4.1 表示建構](../../../parallel/openmp/2-4-1-for-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a>主人

指定只有主線程應執行程式的一個部分。

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>備註

該`master`指令不支援任何子句。

單[一](#single)指令允許您指定應在單個線程(不一定是主線程)上執行代碼部分。

有關詳細資訊,請參閱[2.6.1 主構造](../../../parallel/openmp/2-6-1-master-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>命令

指定並行`for`迴圈下的代碼應像順序循環一樣執行。

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>備註

指令`ordered`必須[for](#for-openmp)在`parallel for`for 或`ordered`建構與子句的動態範圍內。

該`ordered`指令不支援任何子句。

有關詳細資訊,請參閱[2.6.6 有序建構](../../../parallel/openmp/2-6-6-ordered-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a>並行

定義一個並行區域,即將由多個線程並行執行的代碼。

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*第*<br/>
( 選擇性的 )零個或多個子句,請參閱**備註**部分。

### <a name="remarks"></a>備註

這個`parallel`指令支援以下子句:

- [if](openmp-clauses.md#if-openmp)
- [私人](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [共用](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`也可以與[for](#for-openmp)和[節](#sections-openmp)指令一起使用。

有關詳細資訊,請參閱[2.3 並行建構](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>範例

下面的範例展示如何設置線程數和定義並行區域。 默認情況下,線程數與計算機上的邏輯處理器數相等。 例如,如果電腦具有一個物理處理器,啟用了超線程,它將有兩個邏輯處理器和兩個線程。 不同機器的輸出順序可能有所不同。

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a>部分

標識要在所有線程之間劃分的代碼節。

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>參數

*第*<br/>
( 選擇性的 )零個或多個子句,請參閱**備註**部分。

### <a name="remarks"></a>備註

該`sections`指令可以包含零個或`section`多個 指令。

這個`sections`指令支援以下子句:

- [私人](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [不要等待](openmp-clauses.md#nowait)

如果`parallel``clauses`也指定,可以`parallel`是`sections`或指令接受的任何子句`nowait`,但 除外。

有關詳細資訊,請參閱[2.4.2 節構造](../../../parallel/openmp/2-4-2-sections-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a>單

允許您指定應在單個線程(不一定是主線程)上執行代碼部分。

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*第*<br/>
( 選擇性的 )零個或多個子句,請參閱**備註**部分。

### <a name="remarks"></a>備註

這個`single`指令支援以下子句:

- [私人](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [不要等待](openmp-clauses.md#nowait)

主[指令](#master)允許您指定代碼部分應僅在主線程上執行。

有關詳細資訊,請參閱[2.4.3 單建構](../../../parallel/openmp/2-4-3-single-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a>執行緒私有

指定變數是線程的私有變數。

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
要對線程進行私有的變數的逗號分隔清單。 *var*必須是全域或命名空間作用域變數或本地靜態變數。

### <a name="remarks"></a>備註

該`threadprivate`指令不支援任何子句。

該`threadprivate`指令基於使用[__declspec](../../../cpp/declspec.md)關鍵字的[線程](../../../cpp/thread.md)屬性;對`__declspec(thread)`的限制`threadprivate`適用於 。 例如,`threadprivate`變數將存在於進程中啟動的任何線程中,而不僅僅是由並行區域生成的線程團隊的線程的線程。 請注意此實現詳細資訊;您可能會注意到,`threadprivate`使用者定義的類型的建構函數調用的頻率比預期時要頻繁。

您可以在行程啟動`threadprivate`時靜態載入的 DLL 中使用,但是不能在將透過[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)載入`threadprivate`的任何 DLL 中使用,例如載入[/DELAYLOAD(延遲載入)的](../../../build/reference/delayload-delay-load-import.md)DLL,後者也使用`LoadLibrary`。

`threadprivate`*可析構*類型的變數不能保證調用其析構函數。 例如：

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

使用者無法控制構成並行區域的線程何時將終止。 如果行程退出時存在這些線程,則不會通知線程進程退出,並且除退出的線程(此處是主線程)之外的任何線程`threaded_var`上不會調用析構函數。 因此,代碼不應指望變數的正確`threadprivate`銷毀。

有關詳細資訊,請參閱[2.7.1 執行緒專用指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。

### <a name="example"></a>範例

有關`threadprivate`使用的範例,請參閱[私有](openmp-clauses.md#private-openmp)。
