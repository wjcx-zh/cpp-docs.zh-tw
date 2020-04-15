---
title: OpenMP 子句
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 1c4c7961a173eb47394d03e9aabdd14574e62b08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363888"
---
# <a name="openmp-clauses"></a>OpenMP 子句

提供指向OpenMP API 中使用的子句的連結。

可視C++支援以下 OpenMP 子句。

對一般屬性:

|子句|描述|
|------|-----------|
|[if](#if-openmp)|指定迴圈是並行執行還是串行執行。|
|[num_threads](#num-threads)|設置線程團隊中的線程數。|
|[命令](#ordered-openmp-clauses)|如果要在迴圈中使用[有序](openmp-directives.md#ordered-openmp-directives)指令,則需要[對語句的](openmp-directives.md#for-openmp)並行。|
|[附表](#schedule)|適用於[for](openmp-directives.md#for-openmp)指令。|
|[不要等待](#nowait)|覆蓋指令中隱含的障礙。|

對資料共享屬性:

|子句|描述|
|------|-----------|
|[私人](#private-openmp)|指定每個線程應具有其自己的變數實例。|
|[firstprivate](#firstprivate)|指定每個線程應具有其自己的變數實例,並且變數應使用變數的值初始化,因為它存在於並行構造之前。|
|[lastprivate](#lastprivate)|指定封閉上下文的變數版本設置為等於執行最終反覆運算(for-迴圈構造)或最後一節(#pragma节)的線程的私有版本。|
|[共用](#shared-openmp)|指定應在所有線程之間共用一個或多個變數。|
|[default](#default-openmp)|指定並行區域中未示鏡變數的行為。|
|[reduction](#reduction)|指定每個線程專用的一個或多個變數是並行區域末尾的縮減操作的主題。|
|[copyin](#copyin)|允許線程訪問主線程的值,用於[線程專用](openmp-directives.md#threadprivate)變數。|
|[copyprivate](#copyprivate)|指定應在所有線程之間共用一個或多個變數。|

## <a name="copyin"></a><a name="copyin"></a>copyin

允許線程訪問主線程的值,用於[線程專用](openmp-directives.md#threadprivate)變數。

```cpp
copyin(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
將在`threadprivate`主線程中使用變數的值初始化的變數,因為它存在於並行構造之前。

### <a name="remarks"></a>備註

`copyin`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.7.2.7 副本](../../../parallel/openmp/2-7-2-7-copyin.md)。

### <a name="example"></a>範例

有關`copyin`使用的範例,請參閱[執行緒專用](openmp-directives.md#threadprivate)。

## <a name="copyprivate"></a><a name="copyprivate"></a>複製私有

指定應在所有線程之間共用一個或多個變數。

```cpp
copyprivate(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
要共用的一個或多個變數。 如果指定了多個變數,則使用逗號分隔變數名稱。

### <a name="remarks"></a>備註

`copyprivate`適用於[單一](openmp-directives.md#single)指令。

有關詳細資訊,請參閱[2.7.2.8 複製私有](../../../parallel/openmp/2-7-2-8-copyprivate.md)。

### <a name="example"></a>範例

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default"></a><a name="default-openmp"></a>預設

指定並行區域中未示鏡變數的行為。

```cpp
default(shared | none)
```

### <a name="remarks"></a>備註

`shared`如果未指定子句,`default`則該值有效,這意味著並行區域中的任何變數將被視為使用[共用](#shared-openmp)子句指定該變數。 `none`意味著在並行區域中使用的任何變數,這些變數未與[私有](#private-openmp)、[共用](#shared-openmp)、[縮減](#reduction)、[第一私有](#firstprivate)或[最後一個私有](#lastprivate)子句進行限定,都將導致編譯器錯誤。

`default`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.7.2.5 預設值](../../../parallel/openmp/2-7-2-5-default.md)。

### <a name="example"></a>範例

有關[private](#private-openmp)`default`使用的示例,請參閱私有。

## <a name="firstprivate"></a><a name="firstprivate"></a>第一私人

指定每個線程應具有其自己的變數實例,並且變數應使用變數的值初始化,因為它存在於並行構造之前。

```cpp
firstprivate(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
變數在每個線程中具有實例,該變數將用變數的值初始化,因為它存在於並行構造之前。 如果指定了多個變數,則使用逗號分隔變數名稱。

### <a name="remarks"></a>備註

`firstprivate`適用於以下指令:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

有關詳細資訊,請參閱[2.7.2.2 第一私有](../../../parallel/openmp/2-7-2-2-firstprivate.md)。

### <a name="example"></a>範例

有關`firstprivate`使用的示例,請參閱[私有](#private-openmp)中的示例。

## <a name="if-openmp"></a><a name="if-openmp"></a>開啟 MP

指定迴圈是並行執行還是串行執行。

```cpp
if(expression)
```

### <a name="parameters"></a>參數

*運算式*<br/>
積分運算式,如果計算為 true(非零),則會導致並行區域中的代碼並行執行。 如果表達式計算為 false(零),則並行區域以串列方式執行(由單個線程執行)。

### <a name="remarks"></a>備註

`if`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.3 並行建構](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a><a name="lastprivate"></a>最後私人

指定封閉上下文的變數版本設置為等於執行最終反覆運算(for-迴圈構造)或最後一節(#pragma节)的線程的私有版本。

```cpp
lastprivate(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
設置為等於執行最終反覆運算(for-迴圈構造)或最後一節(#pragma节)的私有版本的變數。

### <a name="remarks"></a>備註

`lastprivate`適用於以下指令:

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.7.2.3 最後私有](../../../parallel/openmp/2-7-2-3-lastprivate.md)。

### <a name="example"></a>範例

有關[schedule](#schedule)`lastprivate`使用子句的示例,請參閱計劃。

## <a name="nowait"></a><a name="nowait"></a>不要等待

覆蓋指令中隱含的障礙。

```cpp
nowait
```

### <a name="remarks"></a>備註

`nowait`適用於以下指令:

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

有關詳細資訊,請參閱[2.4.1 表示建構](../../../parallel/openmp/2-4-1-for-construct.md) [、2.4.2 節構造](../../../parallel/openmp/2-4-2-sections-construct.md)和[2.4.3 單個構造](../../../parallel/openmp/2-4-3-single-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num_threads"></a><a name="num-threads"></a>num_threads

設置線程團隊中的線程數。

```cpp
num_threads(num)
```

### <a name="parameters"></a>參數

*num*<br/>
執行緒數

### <a name="remarks"></a>備註

子`num_threads`句具有與[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函數相同的功能。

`num_threads`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.3 並行建構](../../../parallel/openmp/2-3-parallel-construct.md)。

### <a name="example"></a>範例

有關[parallel](openmp-directives.md#parallel)`num_threads`使用子句的示例,請參閱並行。

## <a name="ordered"></a><a name="ordered-openmp-clauses"></a>命令

如果要在迴圈中使用[有序](openmp-directives.md#ordered-openmp-directives)指令,則需要[對語句的](openmp-directives.md#for-openmp)並行。

```cpp
ordered
```

### <a name="remarks"></a>備註

`ordered`適用於[for](openmp-directives.md#for-openmp)指令。

有關詳細資訊,請參閱[2.4.1 表示建構](../../../parallel/openmp/2-4-1-for-construct.md)。

### <a name="example"></a>範例

有關[ordered](openmp-directives.md#ordered-openmp-directives)`ordered`使用子句的示例,請參閱排序。

## <a name="private"></a><a name="private-openmp"></a>私人

指定每個線程應具有其自己的變數實例。

```cpp
private(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
每個線程中要具有實例的變數。

### <a name="remarks"></a>備註

`private`適用於以下指令:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

有關詳細資訊,請參閱[2.7.2.1 私有](../../../parallel/openmp/2-7-2-1-private.md)。

### <a name="example"></a>範例

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a><a name="reduction"></a>減少

指定每個線程專用的一個或多個變數是並行區域末尾的縮減操作的主題。

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>參數

*操作*<br/>
操作的運算符,用於在並行區域末尾的變數*var*上執行。

*無 功*<br/>
一個或多個變數,在其中做標量減少。 如果指定了多個變數,則使用逗號分隔變數名稱。

### <a name="remarks"></a>備註

`reduction`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.7.2.6 還原](../../../parallel/openmp/2-7-2-6-reduction.md)。

### <a name="example"></a>範例

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a><a name="schedule"></a>附表

適用於[for](openmp-directives.md#for-openmp)指令。

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>參數

*型別*<br/>
計畫型`dynamic`態 ,或`guided``runtime`、`static`或或 。

*大小*<br/>
( 選擇性的 )指定反覆運算的大小。 *大小*必須為整數。 *當類型*`runtime`為時無效。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[2.4.1 表示建構](../../../parallel/openmp/2-4-1-for-construct.md)。

### <a name="example"></a>範例

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared"></a><a name="shared-openmp"></a>共用

指定應在所有線程之間共用一個或多個變數。

```cpp
shared(var)
```

### <a name="parameters"></a>參數

*無 功*<br/>
要共用的一個或多個變數。 如果指定了多個變數,則使用逗號分隔變數名稱。

### <a name="remarks"></a>備註

線程之間共用變數的另一種方法是[使用複製專用](#copyprivate)子句。

`shared`適用於以下指令:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

有關詳細資訊,請參閱[2.7.2.4 共用](../../../parallel/openmp/2-7-2-4-shared.md)。

### <a name="example"></a>範例

有關[private](#private-openmp)`shared`使用的示例,請參閱私有。
