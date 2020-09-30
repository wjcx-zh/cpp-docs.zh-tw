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
ms.openlocfilehash: 21270e8cdeb17b6d06d903d328962435c627759f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503829"
---
# <a name="openmp-directives"></a>OpenMP 指示詞

提供 OpenMP API 中使用之指示詞的連結。

Visual C++ 支援下列 OpenMP 指示詞。

針對平行工作共用：

|指示詞|描述|
|---------|-----------|
|[並行](#parallel)|定義平列區域，也就是多個執行緒會平行執行的程式碼。|
|[for](#for-openmp)|使平列區域內的迴圈中完成的工作在 `for` 執行緒之間分割。|
|[部分](#sections-openmp)|識別要在所有線程之間劃分的程式碼區段。|
|[single](#single)|讓您指定應該在單一線程上執行一段程式碼，而不一定要在主要執行緒上執行。|

針對 master 和同步處理：

|指示詞|描述|
|---------|-----------|
|[master](#master)|指定只有主要執行緒應執行程式的某個區段。|
|[關鍵](#critical)|指定程式碼一次只在一個執行緒上執行。|
|[障礙](#barrier)|同步處理小組中的所有線程;所有線程都會在關卡上暫停，直到所有線程都執行屏障為止。|
|[原子](#atomic)|指定將以不可部分完成的方式更新的記憶體位置。|
|[沖洗](#flush-openmp)|指定所有線程都有相同的記憶體，可供所有共用的物件使用。|
|[命令](#ordered-openmp-directives)|指定平行化迴圈下的程式碼 `for` 應執行，就像順序迴圈一樣。|

針對資料環境：

|指示詞|描述|
|---------|-----------|
|[threadprivate](#threadprivate)|指定變數對執行緒是私用的。|

## <a name="atomic"></a><a name="atomic"></a> 原子

指定將以不可部分完成的方式更新的記憶體位置。

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>參數

*expression*<br/>
具有 *左*值的語句，您想要針對多個寫入來保護它的記憶體位置。

### <a name="remarks"></a>備註

指示詞 `atomic` 不支援任何子句。

如需詳細資訊，請參閱2.6.4 不可部分完成的 [結構](../2-directives.md#264-atomic-construct)。

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

## <a name="barrier"></a><a name="barrier"></a> 障礙

同步處理小組中的所有線程;所有線程都會在關卡上暫停，直到所有線程都執行屏障為止。

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>備註

指示詞 `barrier` 不支援任何子句。

如需詳細資訊，請參閱 [2.6.3 關卡](../2-directives.md#263-barrier-directive)指示詞。

### <a name="example"></a>範例

如需如何使用的範例 `barrier` ，請參閱 [master](#master)。

## <a name="critical"></a><a name="critical"></a> 關鍵

指定程式碼一次只能在一個執行緒上執行。

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>參數

*name*<br/>
 (選擇性) 用來識別重要程式碼的名稱。 名稱必須以括弧括住。

### <a name="remarks"></a>備註

指示詞 `critical` 不支援任何子句。

如需詳細資訊，請參閱 [2.6.2 重要結構](../2-directives.md#262-critical-construct)。

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

## <a name="flush"></a><a name="flush-openmp"></a> 沖洗

指定所有線程都有相同的記憶體，可供所有共用的物件使用。

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>參數

*無 功*<br/>
 (選擇性) 以逗號分隔的變數清單，這些變數代表您要同步處理的物件。 如果未指定 *var* ，則會清除所有記憶體。

### <a name="remarks"></a>備註

指示詞 `flush` 不支援任何子句。

如需詳細資訊，請參閱 [2.6.5 flush](../2-directives.md#265-flush-directive)指示詞。

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

## <a name="for"></a><a name="for-openmp"></a> 出於

使平列區域內的迴圈中完成的工作在 `for` 執行緒之間分割。

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>參數

*第*<br/>
 (選擇性) 零個或多個子句，請參閱「 **備註** 」一節。

*for_statement*<br/>
`for`迴圈。 如果迴圈中的使用者程式碼 `for` 變更索引變數，則會產生未定義的行為。

### <a name="remarks"></a>備註

指示詞 `for` 支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [減少](openmp-clauses.md#reduction)
- [命令](openmp-clauses.md#ordered-openmp-clauses)
- [附表](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

如果 `parallel` 也指定， `clauses` 可以是或指示詞接受的任何 `parallel` 子句 `for` ，但除外 `nowait` 。

如需詳細資訊，請參閱 [2.4.1 for 結構](../2-directives.md#241-for-construct)。

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

## <a name="master"></a><a name="master"></a> 主人

指定只有主要執行緒應執行程式的某個區段。

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>備註

指示詞 `master` 不支援任何子句。

[單一](#single)指示詞可讓您指定要在單一執行緒上執行一段程式碼，而不一定要在主要執行緒上執行。

如需詳細資訊，請參閱 [2.6.1 主結構](../2-directives.md#261-master-construct)。

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

## <a name="ordered"></a><a name="ordered-openmp-directives"></a> 命令

指定平行化迴圈下的程式碼 `for` 應執行，就像順序迴圈一樣。

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>備註

指示詞 `ordered` 必須在的動態範圍內，或[for](#for-openmp) `parallel for` 使用子句進行結構化 `ordered` 。

指示詞 `ordered` 不支援任何子句。

如需詳細資訊，請參閱 [2.6.6 已排序的結構](../2-directives.md#266-ordered-construct)。

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

## <a name="parallel"></a><a name="parallel"></a> 並行

定義平列區域，也就是多個執行緒會平行執行的程式碼。

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*第*<br/>
 (選擇性) 零個或多個子句，請參閱「 **備註** 」一節。

### <a name="remarks"></a>備註

指示詞 `parallel` 支援下列子句：

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [預設值](openmp-clauses.md#default-openmp)
- [共用](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [減少](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` 也可以搭配 [for](#for-openmp) 和 [sections](#sections-openmp) 指示詞使用。

如需詳細資訊，請參閱 [2.3 平行結構](../2-directives.md#23-parallel-construct)。

### <a name="example"></a>範例

下列範例示範如何設定執行緒的數目，並定義平列區域。 執行緒的數目預設會等於電腦上的邏輯處理器數目。 例如，如果您的電腦具有一個已啟用超執行緒的實體處理器，則會有兩個邏輯處理器和兩個執行緒。 輸出的順序在不同的電腦上可能會有所不同。

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

## <a name="sections"></a><a name="sections-openmp"></a> 部分

識別要在所有線程之間劃分的程式碼區段。

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
 (選擇性) 零個或多個子句，請參閱「 **備註** 」一節。

### <a name="remarks"></a>備註

指示詞 `sections` 可以包含零或多個指示詞 `section` 。

指示詞 `sections` 支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [減少](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

如果 `parallel` 也指定， `clauses` 可以是或指示詞接受的任何 `parallel` 子句 `sections` ，但除外 `nowait` 。

如需詳細資訊，請參閱 [2.4.2 章節結構](../2-directives.md#242-sections-construct)。

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

## <a name="single"></a><a name="single"></a> 單

讓您指定應該在單一線程上執行一段程式碼，而不一定要在主要執行緒上執行。

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*第*<br/>
 (選擇性) 零個或多個子句，請參閱「 **備註** 」一節。

### <a name="remarks"></a>備註

指示詞 `single` 支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[Master](#master)指示詞可讓您指定只在主要執行緒上執行一段程式碼。

如需詳細資訊，請參閱 [2.4.3 單一結構](../2-directives.md#243-single-construct)。

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

## <a name="threadprivate"></a><a name="threadprivate"></a> threadprivate

指定變數對執行緒是私用的。

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
要對執行緒進行私用之變數的逗號分隔清單。 *var* 必須是全域或命名空間範圍的變數或本機靜態變數。

### <a name="remarks"></a>備註

指示詞 `threadprivate` 不支援任何子句。

指示詞 `threadprivate` 是以使用[__declspec](../../../cpp/declspec.md)關鍵字的[thread](../../../cpp/thread.md)屬性為基礎; apply 的限制為 `__declspec(thread)` `threadprivate` 。 例如， `threadprivate` 變數會存在於進程中啟動的任何執行緒中，而不只是屬於平列區域所產生之執行緒小組的執行緒。 請注意此執行詳細資料;您可能會注意到， `threadprivate` 使用者自訂類型的函式會被呼叫得更頻繁。

您可以 `threadprivate` 在進程啟動時靜態載入的 dll 中使用，不過，您無法 `threadprivate` 在任何將透過 [LOADLIBRARY](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 載入的 dll 中使用，例如使用/DELAYLOAD 載入的 dll [ (延遲載入匯入) ](../../../build/reference/delayload-delay-load-import.md)，也會使用這些 dll `LoadLibrary` 。

`threadprivate`*易損壞*型別的變數不保證會呼叫它的函式。 例如：

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

使用者無法控制何時會終止構成平列區域的執行緒。 當進程結束時，如果這些執行緒存在，執行緒將不會收到進程結束的通知，而且在任何執行緒上都不會呼叫該函式， `threaded_var` 除了 (此處離開的主執行緒之外，主要執行緒) 。 因此，程式碼不應該在適當的變數損毀時計算 `threadprivate` 。

如需詳細資訊，請參閱 [2.7.1 threadprivate](../2-directives.md#271-threadprivate-directive)指示詞。

### <a name="example"></a>範例

如需使用的範例 `threadprivate` ，請參閱 [私](openmp-clauses.md#private-openmp)用。
