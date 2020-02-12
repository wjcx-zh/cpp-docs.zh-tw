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
- ordered
- parallel
- section
- SECTIONS
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
ms.openlocfilehash: 4db341cf58884263e414e24aacf888c8c88e57cc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142022"
---
# <a name="openmp-directives"></a>OpenMP 指示詞

提供 OpenMP API 中使用的指示詞連結。

Visual C++支援下列 OpenMP 指示詞。

針對平行工作共用：

|Directive|描述|
|---------|-----------|
|[parallel](#parallel)|定義平列區域，這是將由多個執行緒平行執行的程式碼。|
|[for](#for-openmp)|造成在平列區域內的 `for` 迴圈中完成的工作，分割線上程之間。|
|[sections](#sections-openmp)|識別要在所有線程之間分割的程式碼區段。|
|[single](#single)|讓您指定應該在單一執行緒上執行程式碼區段，而不一定是主要執行緒。|

針對主要和同步處理：

|Directive|描述|
|---------|-----------|
|[master](#master)|指定只有主要執行緒才會執行程式的區段。|
|[critical](#critical)|指定一次只在一個執行緒上執行程式碼。|
|[barrier](#barrier)|同步處理小組中的所有線程;所有線程都會在屏障暫停，直到所有線程都執行屏障為止。|
|[atomic](#atomic)|指定將會以原子方式更新的記憶體位置。|
|[flush](#flush-openmp)|指定所有線程的所有共用物件都有相同的記憶體視圖。|
|[序](#ordered-openmp-directives)|指定平行處理 `for` 迴圈下的程式碼應執行，如同順序迴圈。|

針對資料環境：

|Directive|描述|
|---------|-----------|
|[threadprivate](#threadprivate)|指定變數是執行緒的私用。|

## <a name="atomic"></a>不可部分完成

指定將會以原子方式更新的記憶體位置。

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>參數

*expression*<br/>
具有*左*值的語句，其記憶體位置是您想要針對多個寫入而保護的。

### <a name="remarks"></a>備註

`atomic` 指示詞不支援子句。

如需詳細資訊，請參閱2.6.4 不可部分完成的[結構](../../../parallel/openmp/2-6-4-atomic-construct.md)。

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

## <a name="barrier"></a>屏障

同步處理小組中的所有線程;所有線程都會在屏障暫停，直到所有線程都執行屏障為止。

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>備註

`barrier` 指示詞不支援子句。

如需詳細資訊，請參閱[2.6.3 屏障](../../../parallel/openmp/2-6-3-barrier-directive.md)指示詞。

### <a name="example"></a>範例

如需如何使用 `barrier`的範例，請參閱[master](#master)。

## <a name="critical"></a>成

指定一次只在一個執行緒上執行程式碼。

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>參數

*name*<br/>
選擇性用來識別關鍵程式碼的名稱。 名稱必須括在括弧中。

### <a name="remarks"></a>備註

`critical` 指示詞不支援子句。

如需詳細資訊，請參閱[2.6.2 critical 結構](../../../parallel/openmp/2-6-2-critical-construct.md)。

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

## <a name="flush-openmp"></a>刷

指定所有線程的所有共用物件都有相同的記憶體視圖。

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>參數

*var*<br/>
選擇性以逗號分隔的變數清單，代表您想要同步處理的物件。 如果未指定*var* ，則會清除所有記憶體。

### <a name="remarks"></a>備註

`flush` 指示詞不支援子句。

如需詳細資訊，請參閱[2.6.5 flush](../../../parallel/openmp/2-6-5-flush-directive.md)指示詞。

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

## <a name="for-openmp"></a>對於

造成在平列區域內的 `for` 迴圈中完成的工作，分割線上程之間。

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>參數

*子句*<br/>
選擇性零或多個子句，請參閱**備註**一節。

*for_statement*<br/>
`for` 迴圈。 如果 `for` 迴圈中的使用者程式碼變更了索引變數，則會產生未定義的行為。

### <a name="remarks"></a>備註

`for` 指示詞支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [序](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

如果同時指定了 `parallel`，`clauses` 可以是 `parallel` 或 `for` 指示詞所接受的任何子句，但不包括 `nowait`。

如需詳細資訊，請參閱[2.4.1 for 結構](../../../parallel/openmp/2-4-1-for-construct.md)。

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

## <a name="master"></a>掌握

指定只有主要執行緒才會執行程式的區段。

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>備註

`master` 指示詞不支援子句。

[單一](#single)指示詞可讓您指定程式碼區段應該在單一執行緒上執行，而不一定是主要執行緒。

如需詳細資訊，請參閱[2.6.1 主要結構](../../../parallel/openmp/2-6-1-master-construct.md)。

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

## <a name="ordered-openmp-directives"></a>序

指定平行處理 `for` 迴圈下的程式碼應執行，如同順序迴圈。

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>備註

`ordered` 指示詞必須在[for](#for-openmp)的動態範圍內，或是使用 `ordered` 子句的 `parallel for` 結構。

`ordered` 指示詞不支援子句。

如需詳細資訊，請參閱[2.6.6 已排序的結構](../../../parallel/openmp/2-6-6-ordered-construct.md)。

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

## <a name="parallel"></a>並列

定義平列區域，這是將由多個執行緒平行執行的程式碼。

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*子句*<br/>
選擇性零或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`parallel` 指示詞支援下列子句：

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [共用](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` 也可以與[for](#for-openmp)和[sections](#sections-openmp)指示詞搭配使用。

如需詳細資訊，請參閱[2.3 平行結構](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>範例

下列範例顯示如何設定執行緒的數目，以及定義平列區域。 根據預設，執行緒的數目等於電腦上的邏輯處理器數目。 例如，如果您的電腦有一個已啟用超執行緒的實體處理器，則會有兩個邏輯處理器和兩個執行緒。 輸出的順序在不同的電腦上可能會有所不同。

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

## <a name="sections-openmp"></a>各節

識別要在所有線程之間分割的程式碼區段。

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

*子句*<br/>
選擇性零或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`sections` 指示詞可以包含零個或多個 `section` 指示詞。

`sections` 指示詞支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

如果同時指定了 `parallel`，`clauses` 可以是 `parallel` 或 `sections` 指示詞所接受的任何子句，但不包括 `nowait`。

如需詳細資訊，請參閱[2.4.2 區段結構](../../../parallel/openmp/2-4-2-sections-construct.md)。

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

## <a name="single"></a>單機

讓您指定應該在單一執行緒上執行程式碼區段，而不一定是主要執行緒。

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*子句*<br/>
選擇性零或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`single` 指示詞支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[主要](#master)指示詞可讓您指定只在主要執行緒上執行程式碼的區段。

如需詳細資訊，請參閱[2.4.3 單一結構](../../../parallel/openmp/2-4-3-single-construct.md)。

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

## <a name="threadprivate"></a>threadprivate

指定變數是執行緒的私用。

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>參數

*var*<br/>
您想要對執行緒設為私用的變數清單（以逗號分隔）。 *var*必須是全域或命名空間範圍的變數或本機靜態變數。

### <a name="remarks"></a>備註

`threadprivate` 指示詞不支援子句。

`threadprivate` 指示詞是以使用[__declspec](../../../cpp/declspec.md)關鍵字的[thread](../../../cpp/thread.md)屬性為基礎;`__declspec(thread)` 的限制適用于 `threadprivate`。 例如，`threadprivate` 變數會存在於進程中啟動的任何執行緒中，而不只是屬於平列區域所產生之執行緒小組一部分的執行緒。 請注意這項執行的詳細資料;您可能會注意到，`threadprivate` 的使用者定義型別的函式通常會被呼叫，而這是預期的情況。

您可以使用在進程啟動時靜態載入的 DLL 中的 `threadprivate`，不過，您無法在任何會透過[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)載入的 dll 中使用 `threadprivate`，例如以/DELAYLOAD 載入的 dll [（延遲載入匯入）](../../../build/reference/delayload-delay-load-import.md)，這也會使用 `LoadLibrary`。

*易損壞*類型的 `threadprivate` 變數不保證會呼叫其析構函式。 例如，

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

當平列區域構成的執行緒終止時，使用者不會有任何控制項。 如果這些執行緒在進程結束時存在，執行緒將不會收到進程結束的通知，而且不會針對任何執行緒上的 `threaded_var` 呼叫此析構函式（在此結束之前）（在此為主要執行緒）。 因此，程式碼不應該計算 `threadprivate` 變數的適當銷毀。

如需詳細資訊，請參閱[2.7.1 threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md)指示詞。

### <a name="example"></a>範例

如需使用 `threadprivate`的範例，請參閱[私](openmp-clauses.md#private-openmp)用。
