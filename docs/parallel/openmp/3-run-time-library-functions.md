---
title: 3. 執行階段程式庫函式
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 4e72d2d74bb26f8eeeb422881cabf92630cced43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363228"
---
# <a name="3-run-time-library-functions"></a>3.執行階段程式庫函式

本章節描述 OpenMP C 和C++執行階段程式庫函式。 標頭 **\<omp.h >** 會宣告兩種類型，可用來控制和查詢平行執行環境，並鎖定函式，可用來同步處理資料的存取權的數個函式。

型別`omp_lock_t`是物件類型可代表鎖定可供使用，或執行緒擁有鎖定。 這些鎖定指*簡單鎖定*。

型別`omp_nest_lock_t`是物件類型可代表任一的鎖定，或者擁有鎖定這兩個執行緒的身分識別以及*巢狀計數*（如下所述）。 這些鎖定指*可巢狀鎖定*。

外部"C"連結函式是程式庫函式。

這一章中的說明可分成下列主題：

- [執行環境函式](#31-execution-environment-functions)
- [鎖定函式](#32-lock-functions)
- [計時常式](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 執行環境函式

在本節中所述的函式會影響，並監視執行緒、 處理器和平行的環境：

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函式

`omp_set_num_threads`函式會設定預設要用於未指定，稍後平行的區域的執行緒數目`num_threads`子句。 格式如下：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Hodnota parametru *num_threads*必須是正整數。 其效果取決於是否已啟用動態調整執行緒數目。 針對一組完整的規則之間的互動`omp_set_num_threads`函式，並動態調整的執行緒，請參閱 <<c2> [ 一節 2.3](2-directives.md#23-parallel-construct)。

此函式已從程式的一部分呼叫時，上面所述的效果，`omp_in_parallel`函式會傳回零。 如果它從程式的一部分來呼叫其中`omp_in_parallel`函式會傳回非零值，這個函式的行為是未定義。

這個呼叫的優先順序高於`OMP_NUM_THREADS`環境變數。 可能會藉由呼叫建立的執行緒數目的預設值`omp_set_num_threads`或藉由設定`OMP_NUM_THREADS`環境變數，您可以明確覆寫單一`parallel`藉由指定指示詞`num_threads`子句。

#### <a name="cross-references"></a>交互參照

- [omp_set_dynamic](#317-omp_set_dynamic-function) function
- [omp_get_dynamic](#318-omp_get_dynamic-function) function
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數
- [num_threads](2-directives.md#23-parallel-construct)子句

### <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 函式

`omp_get_num_threads`函式傳回的執行緒數目目前在小組執行平行從中呼叫它的區域中。 格式如下：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads`子句`omp_set_num_threads`函式，而`OMP_NUM_THREADS`環境變數來控制小組中的執行緒數目。

如果使用者尚未明確設定的執行緒數目，預設值是由實作定義。 此函式繫結至最接近的封閉式`parallel`指示詞。 如果呼叫從序列一部分的程式，或在已序列化的巢狀平行區域，則此函數會傳回 1。

#### <a name="cross-references"></a>交互參照

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函式

`omp_get_max_threads`函式傳回一個整數，具有保證至少會用來組成一個小組，如果在平行區域，而不需要的執行緒數目一樣大`num_threads`子句已在該點出現在程式碼。 格式如下：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

下列的值表示下限`omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

請注意，是否另一個平行區域就會使用`num_threads`子句來要求特定數目的執行緒上下限的結果保證`omp_get_max_threads`不長的保留。

`omp_get_max_threads`函式的傳回值可用來動態配置足夠的儲存體小組在下一個平行區域中的所有執行緒。

#### <a name="cross-references"></a>交互參照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函式

`omp_get_thread_num`函式會傳回執行緒數目，其小組中，執行函式的執行緒。 執行緒數字介於 0 和`omp_get_num_threads()`-1，（含)。 小組的主要執行緒是執行緒 0。

格式如下：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果序列的區域中，從呼叫`omp_get_thread_num`會傳回 0。 如果從序列化巢狀平行區域內呼叫，此函式會傳回 0。

#### <a name="cross-references"></a>交互參照

- [omp_get_num_threads](#312-omp_get_num_threads-function)函式

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs 函式

`omp_get_num_procs`函式會傳回呼叫的函式的時間位於程式可以使用的處理器數目。 格式如下：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函式

`omp_in_parallel`函式會傳回非零值，如果它動態程度以平行方式執行的平行區域內呼叫; 否則它會傳回 0。 格式如下：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

此函數會傳回非零值，以平行方式，包括序列化的巢狀的區域執行的區域中呼叫時。

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函式

`omp_set_dynamic`函式啟用或停用動態調整的執行緒可供執行的平行區域數目。 格式如下：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*會評估為非零的值，用於執行即將推出的平行區域的執行緒數目可能會自動調整執行階段環境，以最佳方式使用系統資源。 如此一來，使用者所指定的執行緒數目會是最大執行緒計數。 小組執行平行的區域中的執行緒數目會保持固定的平行區域的持續時間，以及回報`omp_get_num_threads`函式。

如果*dynamic_threads*會評估為 0，已停用動態調整。

此函式已從程式的一部分呼叫時，上面所述的效果，`omp_in_parallel`函式會傳回零。 如果它從程式的一部分來呼叫其中`omp_in_parallel`函式會傳回非零值，這個函式的行為是未定義。

呼叫`omp_set_dynamic`優先順序高於`OMP_DYNAMIC`環境變數。

執行緒的動態調整的預設值是由實作定義。 如此一來，使用者程式碼相依於特定數目的執行緒有正確的執行應該明確地停用動態的執行緒。 實作不需要提供的功能，以動態調整執行緒數目，但需要他們以提供介面，以支援跨所有平台的可攜性。

#### <a name="cross-references"></a>交互參照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函式

`omp_get_dynamic`函式會傳回非零值，如果執行緒的動態調整已啟用，否則傳回 0。 格式如下：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果實作無法實作動態調整執行緒數目，此函式一律會傳回 0。

#### <a name="cross-references"></a>交互參照

- 如需執行緒的動態調整的說明，請參閱 < [omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函式

`omp_set_nested`函式啟用或停用巢狀平行處理原則。 格式如下：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*巢狀*判斷值為 0，巢狀平行處理原則已停用，這是預設值，以及巢狀平行區域會經過序列化，並由目前的執行緒執行。 否則，啟用巢狀平行處理原則時，和巢狀平行區域可以部署額外的執行緒，以形成巢狀的小組。

此函式已從程式的一部分呼叫時，上面所述的效果，`omp_in_parallel`函式會傳回零。 如果它從程式的一部分來呼叫其中`omp_in_parallel`函式會傳回非零值，這個函式的行為是未定義。

這個呼叫的優先順序高於`OMP_NESTED`環境變數。

啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義。 如此一來，OpenMP 相容的實作都可以序列化巢狀平行區域，即使已啟用巢狀平行處理原則。

#### <a name="cross-references"></a>交互參照

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函式

`omp_get_nested`函式會傳回非零值，如果巢狀平行處理原則已啟用而 0 會停用。 如需有關巢狀平行處理原則的詳細資訊，請參閱 < [omp_set_nested](#319-omp_set_nested-function)。 格式如下：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果實作不實作巢狀平行處理原則，則此函式一律會傳回 0。

## <a name="32-lock-functions"></a>3.2 鎖定函式

這一節所述的函式來處理用於同步處理的鎖定。

下列函式中，鎖定變數必須具有型別`omp_lock_t`。 透過這些函式時，必須只能存取此變數。 所有的鎖定函式需要的引數，有一個指標指向`omp_lock_t`型別。

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函式會初始化簡單的鎖定。
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函式會移除簡單的鎖定。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函式會等候直到有簡單的鎖定可用為止。
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函式會釋放簡單的鎖定。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函式會測試簡單的鎖定。

下列函式中，鎖定變數必須具有型別`omp_nest_lock_t`。  透過這些函式時，必須只能存取此變數。 所有可巢狀鎖定函式需要的引數，有一個指標指向`omp_nest_lock_t`型別。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函式會初始化可巢狀鎖定。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函式會移除可巢狀鎖定。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函式會等候，直到可巢狀鎖定可用為止。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函式會釋放可巢狀鎖定。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函式會測試可巢狀鎖定。

OpenMP 鎖定函式會存取鎖定變數的方式表示它們一律在閱讀，並更新鎖定變數的最新的值。 因此，不需要包含明確的 OpenMP 程式`flush`指示詞，並確定鎖定變數的值是在不同執行緒之間一致。 (可能需要`flush`指示詞，以便其他變數的值一致。)

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函式

這些函式提供初始化鎖定的唯一方法。 每個函式會初始化參數相關聯鎖定*鎖定*即將推出的呼叫中使用。 格式如下：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

已解除鎖定的初始狀態 （也就是沒有任何執行緒擁有鎖定）。 可巢狀鎖定中，初始的巢狀計數為零。 它是呼叫其中一個已經初始化的鎖定變數的這些常式不相容。

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式

這些函式，確定鎖定變數所指*鎖定*未初始化。 格式如下：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

這是呼叫其中一個這些常式使用具有未初始化的鎖定變數不相容或解除鎖定。

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函式

所有這些函式會封鎖執行此函式，直到指定的鎖定可用，然後設定 鎖定的執行緒。 簡單的鎖定時才可以使用它會解除鎖定。 它是否可以使用可巢狀鎖定，則解除鎖定或已由執行緒執行函式所擁有。 格式如下：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

簡單的鎖定，以引數`omp_set_lock`函式必須指向未初始化的鎖定的變數。 鎖定擁有權會授與執行函式的執行緒。

可巢狀鎖定的引數`omp_set_nest_lock`函式必須指向未初始化的鎖定的變數。 巢狀的計數會遞增，而執行緒會授與存取，或會保留的鎖定擁有權。

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式

這些函式會提供方法釋放的鎖定擁有權。 格式如下：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

所有這些函式的引數必須指向執行函式的執行緒所擁有的初始化的鎖定變數。 如果執行緒不擁有該鎖定，則行為是未定義。

簡單的鎖定，`omp_unset_lock`函式會釋放鎖定的擁有權從執行函式的執行緒。

可巢狀的鎖定，`omp_unset_nest_lock`函式會遞減的巢狀的計數和釋放鎖定的擁有權從執行函式，如果得出的計數為零的執行緒。

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函式

這些函式會嘗試設定鎖定，但不會封鎖執行緒的執行。 格式如下：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

引數必須指向未初始化的鎖定的變數。 這些函式會嘗試在相同的方式來設定鎖定`omp_set_lock`和`omp_set_nest_lock`，不同之處在於它們不會封鎖執行緒的執行。

簡單的鎖定，`omp_test_lock`函式會傳回非零值，如果鎖定已成功設定; 否則它會傳回零。

可巢狀的鎖定，`omp_test_nest_lock`函式會傳回新的巢狀計數，如果鎖定已成功設定; 否則它會傳回零。

## <a name="33-timing-routines"></a>3.3 計時常式

在本節中所述的函式支援可攜式時鐘計時器：

- [Omp_get_wtime](#331-omp_get_wtime-function)函式會傳回 24 小時制的時鐘時間。
- [Omp_get_wtick](#332-omp_get_wtick-function)函式會傳回連續的時鐘刻度之間的秒數。

### <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 函式

`omp_get_wtime`函式會傳回雙精度浮點數值等於 24 小時制的時鐘時間 （秒），因為某些 「 時間在過去 」。  實際 「 過去的時間 」 是任意的但它有保證不會在應用程式執行期間變更。 格式如下：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

預期的函式，將會用來測量已耗用時間，如下列範例所示：

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

傳回的時間都 「 每個執行緒 times"這表示不需要是全域一致的多個參與的應用程式中的所有執行緒。

### <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 函式

`omp_get_wtick`函式會傳回雙精度浮點數值的秒數為後續的時鐘刻度之間。 格式如下：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
