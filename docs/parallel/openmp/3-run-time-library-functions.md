---
title: 3. 執行階段程式庫函式
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 6155eb87bd7a1a0533caf99afb3db8417854df30
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882849"
---
# <a name="3-run-time-library-functions"></a>3. 執行時間程式庫函式

本節說明 OpenMP C 和C++執行時間程式庫函數。 **\<> omp**的標頭會宣告兩種類型、數個可用來控制和查詢平行執行環境的函式，以及可用來同步存取資料的鎖定函數。

型別 `omp_lock_t` 是一種物件型別，可以代表有可用的鎖定，或是執行緒擁有鎖定。 這些鎖定稱為*簡單鎖定*。

型別 `omp_nest_lock_t` 是一種物件型別，可以代表有可用的鎖定，或是擁有鎖定之執行緒的識別和一個*嵌套計數*（如下所述）。 這些鎖定稱為*nestable 鎖定*。

程式庫函式是具有 "C" 連結的外部函式。

本章中的描述分為下列主題：

- [執行環境函數](#31-execution-environment-functions)
- [鎖定函式](#32-lock-functions)
- [計時常式](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 執行環境函數

本節所述的函數會影響和監視執行緒、處理器和平行環境：

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads 函式

`omp_set_num_threads` 函式會設定預設的執行緒數目，以用於未指定 `num_threads` 子句的之後平列區域。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

參數*num_threads*的值必須是正整數。 其效果取決於是否已啟用執行緒數目的動態調整。 如需有關 `omp_set_num_threads` 函式與動態調整執行緒之間互動的一組完整規則，請參閱[2.3 區段](2-directives.md#23-parallel-construct)。

從程式的一部分呼叫（其中 `omp_in_parallel` 函式傳回零）時，此函式具有上述效果。 如果是從程式的一部分呼叫，其中 `omp_in_parallel` 函式傳回非零值，則此函式的行為是未定義的。

此呼叫的優先順序高於 `OMP_NUM_THREADS` 環境變數。 執行緒數目的預設值（可以藉由呼叫 `omp_set_num_threads` 或藉由設定 `OMP_NUM_THREADS` 環境變數來建立），可以藉由指定 `num_threads` 子句，在單一 `parallel` 指示詞上明確覆寫。

如需詳細資訊，請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交互參考

- [omp_set_dynamic](#317-omp_set_dynamic-function)函式
- [omp_get_dynamic](#318-omp_get_dynamic-function)函式
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數
- [num_threads](2-directives.md#23-parallel-construct)子句

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads 函式

`omp_get_num_threads` 函式會傳回目前在小組中的執行緒數目，其會執行其呼叫所在的平列區域。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads` 子句、`omp_set_num_threads` 函數和 `OMP_NUM_THREADS` 環境變數會控制小組中的執行緒數目。

如果使用者尚未明確設定執行緒數目，則預設值為「執行定義」。 此函式會系結至最接近的封閉式 `parallel` 指示詞。 如果從程式的序列部分或已序列化的嵌套平列區域呼叫，此函數會傳回1。

如需詳細資訊，請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交互參考

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads 函式

`omp_get_max_threads` 函式會傳回一個整數，保證在程式碼中，如果沒有 `num_threads` 子句的平列區域被看到，就會將它的大小至少與用來組成小組的執行緒數目相同。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

以下表示 `omp_get_max_threads`值的下限：

> *執行緒-用於下一個-team* <= `omp_get_max_threads`

請注意，如果另一個平列區域使用 `num_threads` 子句來要求特定數目的執行緒，則在 `omp_get_max_threads` 的結果下限上的保證不會再保留。

`omp_get_max_threads` 函式的傳回值可用來為小組中的所有線程，以動態方式配置足夠的儲存空間，並在下一個平列區域形成。

#### <a name="cross-references"></a>交互參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num 函式

`omp_get_thread_num` 函式會傳回執行函式之執行緒的執行緒號碼（在其小組內）。 執行緒數目介於0和 `omp_get_num_threads()`-1 之間（含）。 小組的主要執行緒是執行緒0。

其格式如下所示：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果從序欄區域呼叫，`omp_get_thread_num` 會傳回0。 如果從已序列化的嵌套平列區域內呼叫，此函數會傳回0。

#### <a name="cross-references"></a>交互參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)函式

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs 函式

`omp_get_num_procs` 函式會傳回呼叫函式時可供程式使用的處理器數目。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel 函式

如果在平行執行的平列區域的動態範圍內呼叫，則 `omp_in_parallel` 函式會傳回非零值;否則，它會傳回0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

從平行執行的區域內呼叫時，此函式會傳回非零值，包括已序列化的嵌套區域。

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic 函式

`omp_set_dynamic` 函式會啟用或停用可執行平列區域之執行緒數目的動態調整。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*評估為非零值，則執行時間環境會自動調整用來執行即將到來的平列區域的執行緒數目，以充分利用系統資源。 因此，使用者所指定的執行緒數目就是執行緒計數的最大值。 執行平列區域之小組中的執行緒數目，在該平列區域的持續時間內會保持固定狀態，並由 `omp_get_num_threads` 函式報告。

如果*dynamic_threads*評估為0，則會停用動態調整。

從程式的一部分呼叫（其中 `omp_in_parallel` 函式傳回零）時，此函式具有上述效果。 如果是從程式的一部分呼叫，其中 `omp_in_parallel` 函式傳回非零值，則此函式的行為是未定義的。

`omp_set_dynamic` 的呼叫優先順序高於 `OMP_DYNAMIC` 環境變數。

執行緒動態調整的預設值是「執行定義」。 因此，依賴特定執行緒數目進行正確執行的使用者程式碼應該明確停用動態執行緒。 不需要執行來提供動態調整執行緒數目的功能，但它們必須提供介面來支援所有平臺的可攜性。

#### <a name="microsoft-specific"></a>Microsoft 專有

`omp_get_dynamic` 和 `omp_set_dynamic` 目前的支援如下所示：

`omp_set_dynamic` 的輸入參數不會影響執行緒原則，而且不會變更執行緒的數目。 `omp_get_num_threads` 一律會傳回使用者定義的數位（如果已設定）或預設的執行緒數目。 在目前的 Microsoft 執行中，`omp_set_dynamic(0)` 關閉動態執行緒，讓現有的執行緒集可以重複用於下列平列區域。 `omp_set_dynamic(1)` 會藉由捨棄現有的執行緒集，並為即將推出的平列區域建立新的集合，來開啟動態執行緒。 新集合中的執行緒數目與舊的集合相同，而且是以 `omp_get_num_threads`的傳回值為基礎。 因此，為了達到最佳效能，請使用 `omp_set_dynamic(0)` 來重複使用現有的執行緒。

#### <a name="cross-references"></a>交互參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic 函式

如果已啟用執行緒的動態調整，`omp_get_dynamic` 函數會傳回非零值，否則會傳回0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果執行不會執行執行緒數目的動態調整，則此函式一律會傳回0。 如需詳細資訊，請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交互參考

- 如需動態執行緒調整的說明，請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested 函式

`omp_set_nested` 函數會啟用或停用嵌套的平行處理原則。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*nested*會評估為0，則會停用嵌套的平行處理原則，這是預設值，而且會由目前的執行緒序列化和執行嵌套的平列區域。 否則，會啟用嵌套的平行處理原則，而已嵌套的平列區域則可能會部署額外的執行緒來形成嵌套的小組。

從程式的一部分呼叫（其中 `omp_in_parallel` 函式傳回零）時，此函式具有上述效果。 如果是從程式的一部分呼叫，其中 `omp_in_parallel` 函式傳回非零值，則此函式的行為是未定義的。

此呼叫的優先順序高於 `OMP_NESTED` 環境變數。

啟用「嵌套平行處理原則」時，用來執行「嵌套平列區域」的執行緒數目是實值定義。 如此一來，即使啟用了嵌套的平行處理原則，OpenMP 相容的執行還是可以序列化嵌套的平列區域。

#### <a name="cross-references"></a>交互參考

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested 函式

如果已啟用嵌套平行處理原則，`omp_get_nested` 函式會傳回非零值，如果已停用，則會傳回0。 如需有關嵌套平行處理原則的詳細資訊，請參閱[omp_set_nested](#319-omp_set_nested-function)。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果執行不會執行嵌套的平行處理原則，則此函式一律會傳回0。

## <a name="32-lock-functions"></a>3.2 鎖定函式

本節所述的函數會操控用於同步處理的鎖定。

針對下列函數，鎖定變數必須有類型 `omp_lock_t`。 這個變數必須只能透過這些函式來存取。 所有的鎖定函式都需要具有 `omp_lock_t` 類型之指標的引數。

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函式會初始化簡單鎖定。
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函式會移除簡單的鎖定。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函式會等候，直到有簡單的鎖定可用為止。
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函式會釋放簡單的鎖定。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函數會測試簡單的鎖定。

針對下列函數，鎖定變數必須有類型 `omp_nest_lock_t`。  這個變數必須只能透過這些函式來存取。 所有的 nestable 鎖定函式都需要具有 `omp_nest_lock_t` 類型之指標的引數。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函式會初始化 nestable 鎖定。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函式會移除 nestable 鎖定。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函式會等候，直到有可用的 nestable 鎖定為止。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函式會釋放 nestable 鎖定。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函數會測試 nestable 鎖定。

OpenMP 鎖定函式會以永遠讀取及更新鎖定變數最新值的方式來存取鎖定變數。 因此，OpenMP 程式不需要包含明確的 `flush` 指示詞，以確保鎖定變數的值在不同的執行緒之間是一致的。 （可能需要 `flush` 指示詞，讓其他變數的值保持一致）。

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函式

這些函式提供初始化鎖定的唯一方法。 每個函式都會初始化與參數*鎖定*相關聯的鎖定，以便在即將進行的呼叫中使用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始狀態為 [已解除鎖定] （也就是沒有任何執行緒擁有鎖定）。 若為 nestable 鎖定，初始的嵌套計數為零。 以已初始化的鎖定變數呼叫其中一個常式並不符合規範。

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函數

這些函式可確保指向鎖定變數*鎖定*的會未初始化。 其格式如下所示：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

使用未初始化或已解除鎖定的鎖定變數呼叫其中一個常式是不相容的。

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函數

所有這些函式都會封鎖執行函式的執行緒，直到指定的鎖定可用為止，然後再設定鎖定。 如果已解除鎖定，就可以使用簡單的鎖定。 如果 nestable 鎖定已解除鎖定，或其已由執行函式的執行緒所擁有，則可以使用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

對於簡單的鎖定，`omp_set_lock` 函式的引數必須指向初始化的鎖定變數。 鎖定的擁有權會授與執行函數的執行緒。

若為 nestable 鎖定，`omp_set_nest_lock` 函式的引數必須指向已初始化的鎖定變數。 此嵌套計數會遞增，而執行緒會被授與或保留鎖定的擁有權。

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函數

這些函式提供釋放鎖定擁有權的方法。 其格式如下所示：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

這些函式的每一個引數都必須指向執行函數的執行緒所擁有的初始化鎖定變數。 如果執行緒不擁有該鎖定，則行為是未定義的。

針對簡單的鎖定，`omp_unset_lock` 函式會從鎖定的擁有權釋放執行函式的執行緒。

若為 nestable 鎖定，`omp_unset_nest_lock` 函式會遞減嵌套計數，並在產生的計數為零時，從鎖定的擁有權釋放執行函數的執行緒。

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函數

這些函式會嘗試設定鎖定，但不會封鎖執行緒的執行。 其格式如下所示：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

引數必須指向初始化的鎖定變數。 這些函式會嘗試使用與 `omp_set_lock` 和 `omp_set_nest_lock`相同的方式來設定鎖定，不同之處在于它們不會封鎖執行緒的執行。

對於簡單的鎖定，如果成功設定鎖定，`omp_test_lock` 函數會傳回非零值;否則，它會傳回零。

針對 nestable 鎖定，如果成功設定鎖定，`omp_test_nest_lock` 函數會傳回新的嵌套計數;否則，它會傳回零。

## <a name="33-timing-routines"></a>3.3 計時常式

本節中所述的函式支援可移植的時鐘計時器：

- [Omp_get_wtime](#331-omp_get_wtime-function)函數會傳回已耗用的時鐘時間。
- [Omp_get_wtick](#332-omp_get_wtick-function)函數會傳回連續時鐘刻度之間的秒數。

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime 函式

`omp_get_wtime` 函式會傳回雙精確度浮點數，此值等於經過一段時間後的時鐘時間（以秒為單位）。  實際的「過去時間」是任意的，但保證不會在應用程式執行期間變更。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

預期函式會用來測量經過的時間，如下列範例所示：

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

傳回的時間是「每個執行緒的時間」，這表示它們不需要在參與應用程式的所有線程之間進行全域一致。

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick 函式

`omp_get_wtick` 函式會傳回雙精確度浮點數，此值等於連續時鐘刻度之間的秒數。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
