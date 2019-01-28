---
title: 答： 範例
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087297"
---
# <a name="a-examples"></a>答： 範例

以下是本文件中所定義的建構的範例。 指示詞後面的陳述式是只在必要時，複合和非複合陳述式會從在它前面的指示詞來進行縮排。

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 平行的簡單迴圈

下列範例示範如何平行處理迴圈，使用[平行的](2-directives.md#251-parallel-for-construct)指示詞。 迴圈反覆項目變數是預設的情況下，私人的因此不需要明確指定 private 子句中。

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A.2 條件式編譯

下列範例說明使用使用 OpenMP 巨集的條件式編譯[已新增 _OPENMP](2-directives.md#22-conditional-compilation)。 使用 /openmp 編譯`_OPENMP`會變成已定義巨集。

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

已定義的前置處理器運算子可讓測試在單一的指示詞中的多個巨集。

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 平行區域

[平行](2-directives.md#23-parallel-construct)指示詞可用於粗略平行處理程式。 在下列範例中，每個執行緒在平行區域決定全域陣列的哪個部分`x`作，根據執行緒數目：

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 nowait 子句

如果有許多的獨立迴圈的平行區域內，您可以使用[nowait](2-directives.md#241-for-construct)子句，以避免隱含的屏障結尾`for`指示詞，如下所示：

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 critical 指示詞

下列範例包含數個[重要](2-directives.md#262-critical-construct)指示詞。 此範例說明工作是從佇列中清除並處理的佇列模型。 若要防範清除佇列中的相同工作的執行緒數目，清除佇列作業必須是在`critical`一節。 兩個佇列，在此範例中是獨立的因為它們受到`critical`指示詞，以不同的名稱， *xaxis*並*yaxis*。

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 lastprivate 子句

有時候使用正確的執行取決於迴圈的最後一個反覆項目指派給變數的值。 這種程式都必須列出所有這類變數做為引數[lastprivate](2-directives.md#2723-lastprivate)子句，讓變數的值會與迴圈執行時以循序方式相同。

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

在上述範例中，值`i`結尾的平行區域將會等於`n-1`，如所示的循序的情況。

## <a name="a7-the-reduction-clause"></a>A.7 reduction 子句

下列範例示範[減少](2-directives.md#2726-reduction)子句：

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 平行處理區段

在下列範例中 (如[區段 2.4.2](2-directives.md#242-sections-construct))，函式*xaxis*， *yaxis*，以及*zaxis*可以並行執行。 第一個`section`指示詞是選擇性的。  所有`section`指示詞需要的語彙範圍中出現`parallel sections`建構。

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 Single 指示詞

下列範例示範[單一](2-directives.md#243-single-construct)指示詞。 在範例中，只有一個執行緒 (通常發生在第一個執行緒`single`指示詞) 會列印進度訊息。 使用者必須要執行哪一個執行緒將不做任何假設`single`一節。 所有其他執行緒會略過`single`區段，並在結尾的屏障停止`single`建構。 如果其他執行緒可以繼續進行，而不需等待執行的執行緒`single`區段中，`nowait`子句上指定`single`指示詞。

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 循序排序

[排序區段](2-directives.md#266-ordered-construct)適合用於循序排序的輸出，以平行方式完成。 下列程式會列印出循序的索引：

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 的固定執行緒的數目

有些程式會依賴固定、 預先指定的數字，要正確執行的執行緒。  因為動態調整的執行緒數目的預設值是由實作定義，這類程式可以選擇關閉動態執行緒功能，並設定明確地將可攜性的執行緒數目。 下列範例示範如何使用執行此動作[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)，並[omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

在此範例中，正確的程式執行只有當它由 16 的執行緒執行。 如果實作不支援執行緒 16，此範例中的行為是由實作定義。

執行平行區域的執行緒數目在平行區域，無論設定的動態執行緒期間維持不變。 動態執行緒機制會決定要在平行區域開始使用的執行緒數目，並讓它常數期間的區域。

## <a name="a12-the-atomic-directive"></a>A.12 不可部分完成的指示詞

下列範例可避免競爭情形 (同時更新項目的*x*許多執行緒) 使用[不可部分完成](2-directives.md#264-atomic-construct)指示詞：

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

使用的優點`atomic`指示詞在此範例中是它可讓兩個不同的項目平行 x 的更新。 如果[重大](2-directives.md#262-critical-construct)指示詞改為使用，則所有更新的項目*x*執行循序 （但不在任何保證順序）。

`atomic`指示詞只適用於 C 或 c + + 陳述式緊接著下。  如此一來，項目*y*不在此範例中會以不可分割方式更新。

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 並 A 清單的 flush 指示詞

下列範例會使用`flush`點對點同步處理的執行緒配對之間的特定物件的指示詞：

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 搭配 A 沒有清單的 flush 指示詞

下列範例 (如[區段 2.6.5](2-directives.md#265-flush-directive)) 會區分共用受影響的物件`flush`指示詞搭配任何不受影響的共用物件的清單：

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 使用的執行緒數目

請考慮下列不正確的範例 (如[第 3.1.2 節](3-run-time-library-functions.md#312-omp_get_num_threads-function)):

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`序列一節的程式碼，呼叫傳回 1，因此*np*一律會等於前一個範例 1。 若要判斷將會針對平行區域部署的執行緒數目，請呼叫應該在平行區域內。

下列範例示範如何重寫此程式，但不包含查詢的執行緒數目：

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 鎖定

在下列範例中 (如[區段 3.2](3-run-time-library-functions.md#32-lock-functions))，鎖定函式的引數應該有型別`omp_lock_t`，以及是否有不需要清除它。  鎖定函式會造成執行緒等候第一個重要區段中，項目處於閒置狀態，但執行其他工作在等候第二個項目時。  `omp_set_lock`函式區塊，但`omp_test_lock`函式，並不允許在工作`skip()`完成。

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17 可巢狀鎖定

下列範例 (如[一節 3.2](3-run-time-library-functions.md#32-lock-functions)) 示範如何使用可巢狀鎖定同步處理更新至整個結構和其成員的其中一個。

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>A.18 使用巢狀指示詞

下列範例`for`[指示詞的巢狀](2-directives.md#29-directive-nesting)是相容，因為內部和外部`for`指示詞將繫結至不同的平行區域：

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

上述範例中的下列變化也是符合規範的：

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 範例巢狀使用工作共用指示詞

在本節中的範例將說明[指示詞的巢狀](2-directives.md#29-directive-nesting)規則。

下列範例是不符合規範因為內部和外部`for`指示詞為巢狀，並繫結至相同`parallel`指示詞：

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

上述範例中的下列動態巢狀的版本為不相容：

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

下列範例是不符合規範因為`for`和`single`指示詞為巢狀，並繫結到同一個平行區域：

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

下列範例是不符合規範因為`barrier`指示詞內`for`可能會導致死結：

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

下列範例是不符合規範因為`barrier`導致死結，因為，一次只有一個執行緒可以進入重要區段：

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

下列範例是不符合規範因為`barrier`導致死結，因為，只有一個執行緒執行`single`區段：

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>A.20 繫結 barrier 指示詞

指示詞的繫結規則呼叫`barrier`指示詞以繫結至最接近的封閉式`parallel`指示詞。 如需詳細指示詞繫結的詳細資訊，請參閱[一節 2.8](2-directives.md#28-directive-binding)。

在下列範例中，從呼叫*主要*要*sub2*相容因為`barrier`(中*sub3*) 繫結至在平行區域*sub2*. 接到*主要*要*sub1*相容因為`barrier`繫結至在副程式中的平行區域*sub2*。  接到*主要*要*sub3*相容因為`barrier`不繫結至任何平行區域，且會被忽略。 此外，`barrier`只會同步處理之封入的平行區域中的執行緒和中建立的不是所有執行緒小組*sub1*。

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 使用 private 子句的範圍變數

值`i`和`j`在下列範例中並未定義在平行區域從結束：

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

如需詳細資訊`private`子句，請參閱 <<c2> [ 一節 2.7.2.1](2-directives.md#2721-private)。

## <a name="a22-the-defaultnone-clause"></a>A.22 default （none） 子句

下列範例會區分受到變數`default(none)`子句未使用的變數中：

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

如需詳細資訊`default`子句，請參閱 <<c2> [ 一節 2.7.2.5](2-directives.md#2725-default)。

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 ordered 指示詞範例

很可能有許多使用的排序的區段`for`指定與`ordered`子句。 第一個範例是不符合規範，因為 API 會指定下列規則：

「 使用迴圈的反覆項目`for`建構必須執行相同`ordered`指示詞超過一次，而且只能執行一個以上的`ordered`指示詞。 」 (請參閱[一節 2.6.6](2-directives.md#266-ordered-construct)。)

在此不相容的範例中，所有的反覆項目會執行兩個已排序的區段：

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

下列符合規範的範例所示`for`與一個以上的排序區段：

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 private 子句範例

[私人](2-directives.md#2721-private)子句在平行區域才會生效的語彙範圍的區域，而非區域的動態範圍。  因此，在範例中，變數的任何用法內`for`常式中的迴圈*f*指的私用複本，而中的使用方式常式*g*參考到全域。

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 copyprivate 資料屬性子句範例

**範例 1：**[Copyprivate](2-directives.md#2728-copyprivate)子句可以用來廣播由單一執行緒直接在其他執行緒的私用變數的所有執行個體所取得的值。

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

如果是例行*init*稱為從序列的區域，其行為不會受到指示詞出現與否。 若要在呼叫之後*get_values*常式已執行一個執行緒，沒有任何執行緒所指定的私用物件之前離開建構， *b*， *x*，並*y*所有執行緒中變成以定義讀取的值。

**範例 2：** 相較於先前的範例，假設讀取只能由特定的執行緒，假設主要執行緒。 在此情況下，`copyprivate`子句不能直接進行廣播，但它可以用來提供暫時的共用物件的存取權。

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**範例 3︰** 假設在平行區域內所需的鎖定物件的數目不容易判斷之前輸入它。 `copyprivate`子句可以用來提供配置該平行區域內的共用的鎖定物件的存取權。

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 threadprivate 指示詞

下列範例示範如何使用[threadprivate](2-directives.md#271-threadprivate-directive)指示詞，以向各執行緒提供不同的計數器。

### <a name="example-1"></a>範例 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>範例 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A.27 C99 可變長度陣列

下列範例會示範如何使用 C99 可變長度陣列 (Vla) 中[firstprivate](2-directives.md#2722-firstprivate)指示詞。

> [!NOTE]
> Visual c + + 目前不支援可變長度陣列。

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 num_threads 子句

下列範例示範[num_threads](2-directives.md#23-parallel-construct)子句。 平行區域最多 10 個執行緒的執行。

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 在 critical 建構工作共用建構

下列範例示範如何使用工作共用建構內`critical`建構。 這個範例是符合規範，因為工作共用建構和`critical`建構未繫結到同一個平行區域。

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A.30 Reprivatization

下列範例會示範 reprivatization 的變數。 可以標示為私用變數`private`一次在巢狀指示詞。 您不需要共用這些變數在封入的平行區域中。

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 安全執行緒鎖定函式

下列 c + + 範例示範如何使用來初始化陣列的平行區域中的鎖定[omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)。

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
