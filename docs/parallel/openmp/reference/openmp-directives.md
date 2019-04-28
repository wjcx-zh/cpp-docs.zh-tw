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
ms.openlocfilehash: d644b612c0c326692786c94046d799163dfbce8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362682"
---
# <a name="openmp-directives"></a>OpenMP 指示詞

提供用於 OpenMP API 中的指示詞的連結。

視覺化C++支援下列的 OpenMP 指示詞。

平行工作共用：

|指示詞|描述|
|---------|-----------|
|[parallel](#parallel)|定義在平行區域，也就是將多個執行緒以平行方式執行的程式碼。|
|[for](#for-openmp)|會導致完成的工作`for`來分割於執行緒在平行區域內的迴圈。|
|[sections](#sections-openmp)|識別要被所有執行緒之間的程式碼區段。|
|[single](#single)|可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。|

Master 和同步處理：

|指示詞|描述|
|---------|-----------|
|[master](#master)|指定只在主要執行緒應該執行的程式區段。|
|[critical](#critical)|指定一次只在一個執行緒上執行的程式碼。|
|[barrier](#barrier)|同步處理的小組中的所有執行緒在屏障的所有執行緒都暫停，直到所有執行緒都執行的屏障為止。|
|[atomic](#atomic)|指定的記憶體位置會以不可分割方式更新。|
|[flush](#flush-openmp)|指定所有執行緒都有相同的檢視，所有的共用物件的記憶體。|
|[ordered](#ordered-openmp-directives)|指定在平行化程式碼`for`應該執行迴圈，例如循序迴圈。|

對於資料的環境：

|指示詞|描述|
|---------|-----------|
|[threadprivate](#threadprivate)|指定在執行緒私用變數。|

## <a name="atomic"></a>atomic

指定的記憶體位置會以不可分割方式更新。

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>參數

*expression*<br/>
具有陳述式*左值*，您想要防止多次寫入其記憶體位置。

### <a name="remarks"></a>備註

`atomic`指示詞支援任何子句。

如需詳細資訊，請參閱 < [2.6.4 atomic 建構](../../../parallel/openmp/2-6-4-atomic-construct.md)。

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

## <a name="barrier"></a>barrier

同步處理的小組中的所有執行緒在屏障的所有執行緒都暫停，直到所有執行緒都執行的屏障為止。

```
#pragma omp barrier
```

### <a name="remarks"></a>備註

`barrier`指示詞支援任何子句。

如需詳細資訊，請參閱 < [2.6.3 barrier 指示詞](../../../parallel/openmp/2-6-3-barrier-directive.md)。

### <a name="example"></a>範例

如需如何使用的範例`barrier`，請參閱 <<c2> [ 主要](#master)。

## <a name="critical"></a>重要

指定程式碼只執行一個執行緒上一次。

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>參數

*name*<br/>
（選擇性）要找出重要的程式碼的名稱。 名稱必須括在括號中。

### <a name="remarks"></a>備註

`critical`指示詞支援任何子句。

如需詳細資訊，請參閱 < [2.6.2 重要建構](../../../parallel/openmp/2-6-2-critical-construct.md)。

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

## <a name="flush-openmp"></a>flush

指定所有執行緒都有相同的檢視，所有的共用物件的記憶體。

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>參數

*var*<br/>
（選擇性）代表您想要同步處理的物件變數的逗號分隔清單。 如果*var*未指定，會在排清所有記憶體。

### <a name="remarks"></a>備註

`flush`指示詞支援任何子句。

如需詳細資訊，請參閱 < [2.6.5 flush 指示詞](../../../parallel/openmp/2-6-5-flush-directive.md)。

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

## <a name="for-openmp"></a>for

會導致完成的工作`for`來分割於執行緒在平行區域內的迴圈。

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>參數

*clauses*<br/>
（選擇性）零個或多個子句，請參閱**備註**一節。

*for_statement*<br/>
A`for`迴圈。 如果使用者程式碼中，將會產生未定義的行為`for`迴圈變更索引變數。

### <a name="remarks"></a>備註

`for`指示詞可支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [ordered](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

如果`parallel`同時指定，則`clauses`可以任何子句接受`parallel`或是`for`指示詞，除了`nowait`。

如需詳細資訊，請參閱 < [2.4.1 for 建構](../../../parallel/openmp/2-4-1-for-construct.md)。

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

## <a name="master"></a>master

指定只在主要執行緒應該執行的程式區段。

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>備註

`master`指示詞支援任何子句。

[單一](#single)指示詞可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。

如需詳細資訊，請參閱 < [2.6.1 master 建構](../../../parallel/openmp/2-6-1-master-construct.md)。

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

## <a name="ordered-openmp-directives"></a>ordered

指定在平行化程式碼`for`應該執行迴圈，例如循序迴圈。

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>備註

`ordered`指示詞必須是動態的範圍內[for](#for-openmp)或是`parallel for`建構包含`ordered`子句。

`ordered`指示詞支援任何子句。

如需詳細資訊，請參閱 < [2.6.6 ordered 建構](../../../parallel/openmp/2-6-6-ordered-construct.md)。

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

## <a name="parallel"></a>parallel

定義在平行區域，也就是將多個執行緒以平行方式執行的程式碼。

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*clauses*<br/>
（選擇性）零個或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`parallel`指示詞可支援下列子句：

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [shared](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` 也可與[for](#for-openmp)並[各節](#sections-openmp)指示詞。

如需詳細資訊，請參閱 < [2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>範例

下列範例示範如何設定的執行緒數目，以及定義在平行區域。 執行緒數目等於預設的電腦上的邏輯處理器數目。 例如，如果您有已啟用超執行緒的一個實體處理器的電腦時，它會有兩個邏輯處理器和兩個執行緒。 輸出的順序可能會不同，在不同電腦上。

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

## <a name="sections-openmp"></a>區段

識別要被所有執行緒之間的程式碼區段。

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>參數

*clauses*<br/>
（選擇性）零個或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`sections`指示詞可以包含零或多個`section`指示詞。

`sections`指示詞可支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

如果`parallel`同時指定，則`clauses`可以任何子句接受`parallel`或是`sections`指示詞，除了`nowait`。

如需詳細資訊，請參閱 < [2.4.2 sections 建構](../../../parallel/openmp/2-4-2-sections-construct.md)。

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

## <a name="single"></a>single

可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。

```
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>參數

*clauses*<br/>
（選擇性）零個或多個子句，請參閱**備註**一節。

### <a name="remarks"></a>備註

`single`指示詞可支援下列子句：

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[主要](#master)指示詞可讓您指定一段程式碼，應該只在主要執行緒上執行。

如需詳細資訊，請參閱 < [2.4.3 單一建構](../../../parallel/openmp/2-4-3-single-construct.md)。

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

指定在執行緒私用變數。

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>參數

*var*<br/>
您想要的執行緒設為私用變數的逗號分隔清單。 *var*必須是全域或命名空間-範圍變數或靜態區域變數。

### <a name="remarks"></a>備註

`threadprivate`指示詞支援任何子句。

`threadprivate`指示詞根據[執行緒](../../../cpp/thread.md)屬性使用[__declspec](../../../cpp/declspec.md)關鍵字; 限制`__declspec(thread)`套用至`threadprivate`。 比方說，`threadprivate`變數會存在於任何啟動程序，不只是屬於執行緒小組在平行區域所繁衍的執行緒的執行緒。 請注意，此實作詳細資料;您可能會注意到，建構函式`threadprivate`詳細通常則應該呼叫使用者定義型別。

您可以使用`threadprivate`在處理序啟動時以靜態方式載入的 dll，但是您無法使用`threadprivate`中將會透過載入的任何 DLL [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)如所載入的 Dll [/DELAYLOAD （延遲載入匯入）](../../../build/reference/delayload-delay-load-import.md)，這也會使用`LoadLibrary`。

A`threadprivate`的變數*易損壞*型別不一定能夠呼叫其解構函式。 例如: 

```
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

使用者擁有並構成平行區域的執行緒將會結束時沒有任何控制項。 如果執行緒存在於，當處理序結束時，執行緒不會通知程序結束時，而不會呼叫解構函式，如`threaded_var`結束以外的任何執行緒上 (主執行緒中的 這裡）。 因此程式碼不應該仰賴適當解構`threadprivate`變數。

如需詳細資訊，請參閱 < [2.7.1 threadprivate 指示詞](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。

### <a name="example"></a>範例

如需使用的範例`threadprivate`，請參閱 <<c2> [ 私人](openmp-clauses.md#private-openmp)。
