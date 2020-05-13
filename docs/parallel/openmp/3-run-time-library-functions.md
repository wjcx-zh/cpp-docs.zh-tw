---
title: 3. 執行階段程式庫函式
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370277"
---
# <a name="3-run-time-library-functions"></a>3. 執行時庫功能

本節介紹 OpenMP C 和C++運行時庫函數。 標頭**\<omp.h>** 聲明兩種類型,多個函數可用於控制和查詢並行執行環境,以及鎖定可用於同步存取數據的函數。

類型`omp_lock_t`是一種對象類型,能夠表示鎖可用或線程擁有鎖。 這些鎖被稱為*簡單的鎖*。

類型`omp_nest_lock_t`是一種對象類型,能夠表示鎖可用,或者同時表示擁有鎖的線程的標識和*嵌套計數*(如下所述)。 這些鎖稱為*可嵌so鎖*。

庫函數是具有"C"連結的外部函數。

這個章中的描述分為以下主題:

- [執行環境函數](#31-execution-environment-functions)
- [鎖定功能](#32-lock-functions)
- [計時常式](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 執行環境函式

本節中描述的函數影響和監視線程、處理器和並行環境:

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

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads功能

函數`omp_set_num_threads`設置預設的線程數,用於未`num_threads`指定 子句的更高版本的並行區域。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

參數*num_threads*的值必須為正整數。 其效果取決於是否啟用了線程數的動態調整。 有關`omp_set_num_threads`函數與線程動態調整之間的交互的一套全面規則,請參閱[第 2.3 節](2-directives.md#23-parallel-construct)。

當從程式返回零的部分調用時,`omp_in_parallel`此功能具有上述效果。 如果從程式的一部分調用函數`omp_in_parallel`返回非零值,則此函數的行為未定義。

此調用優先於`OMP_NUM_THREADS`環境變數。 可以通過調`omp_set_num_threads`用`OMP_NUM_THREADS`或設置 環境變數在`parallel`單個 指令上顯式覆蓋線程數的預設值,該`num_threads`值可以通過指定 子句來顯式覆蓋。

有關詳細資訊,請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉參考

- [omp_set_dynamic](#317-omp_set_dynamic-function)功能
- [omp_get_dynamic](#318-omp_get_dynamic-function)功能
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數
- [num_threads](2-directives.md#23-parallel-construct)條款

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads功能

函數`omp_get_num_threads`返回團隊中當前執行調用它的並行區域的線程數。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

子`num_threads`句`omp_set_num_threads`、`OMP_NUM_THREADS`函數 和環境變數控制團隊中的線程數。

如果使用者尚未顯式設置線程數,則預設值為實現定義。 此函數綁定到最近的封閉`parallel`指令。 如果從程式的串列部分或序列化的嵌套並行區域調用,則此函數返回 1。

有關詳細資訊,請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉參考

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads功能

函數`omp_get_max_threads`傳回整數,該整數保證至少與用於組建團隊的線程數一樣大,如果代碼中此時可以看到沒有子句的`num_threads`並行區域。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

下面表示對的值的下`omp_get_max_threads`限:

> *執行緒使用到下一個團隊* <= `omp_get_max_threads`

請注意,如果另一個並行區域`num_threads`使用子句請求特定數量的線程,則下限上的`omp_get_max_threads`保證 不再保留。

函數`omp_get_max_threads`的返回值可用於動態分配在下一個並行區域形成的團隊中的所有線程的足夠存儲。

#### <a name="cross-references"></a>交叉參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num功能

函數`omp_get_thread_num`返回執行其函數的線程的線程編號(在其團隊中)。 線程數介於 0`omp_get_num_threads()`和 -1 之間,包括。 團隊的主線程是線程 0。

其格式如下所示：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果從串列區域調用,`omp_get_thread_num`則返回 0。 如果從序列化的嵌套並行區域內調用,則此函數返回 0。

#### <a name="cross-references"></a>交叉參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)功能

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs功能

函數`omp_get_num_procs`返回調用函數時程式可用的處理器數。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel功能

`omp_in_parallel`如果函數在並行區域的動態範圍內調用,則返回非零值;否則,它返回 0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

當從並行執行的區域內調用時,此函數返回非零值,包括序列化的嵌套區域。

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic功能

該`omp_set_dynamic`函數啟用或禁用可用於執行並列區域的線程數的動態調整。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*計算為非零值,則運行時環境可能會自動調整用於執行即將到來的並行區域的線程數,以最佳使用系統資源。 因此,使用者指定的線程數是最大線程計數。 執行並列區域的團隊中的線程數在該並行區域的持續時間內保持不變,`omp_get_num_threads`並由函數報告。

如果*dynamic_threads*計算為 0,則禁用動態調整。

當從程式返回零的部分調用時,`omp_in_parallel`此功能具有上述效果。 如果從程式的一部分調用函數`omp_in_parallel`返回非零值,則此函數的行為未定義。

對的`omp_set_dynamic`調用優先於`OMP_DYNAMIC`環境變數。

線程動態調整的預設值是實現定義的。 因此,依賴於特定數量的線程進行正確執行的用戶代碼應顯式禁用動態線程。 實現不需要提供動態調整線程數的能力,但它們需要提供介面來支援跨所有平臺的可移植性。

#### <a name="microsoft-specific"></a>Microsoft 專有

目前的支援`omp_get_dynamic``omp_set_dynamic`:

要`omp_set_dynamic`的輸入參數不會影響線程策略,也不會更改線程數。 `omp_get_num_threads`始終返回使用者定義的編號(如果已設置)或預設線程號。 在當前 Microsoft`omp_set_dynamic(0)`實現中 ,關閉動態線程,以便現有線程集可以重新用於以下並行區域。 `omp_set_dynamic(1)`通過放棄現有線程集並為即將到來的並行區域創建新集來打開動態線程。 新集中的線程數與舊集相同,並且根據的`omp_get_num_threads`傳回值 。 因此,為了獲得最佳性能,請使用`omp_set_dynamic(0)`重用現有線程。

#### <a name="cross-references"></a>交叉參考

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic功能

如果`omp_get_dynamic`啟用了線程的動態調整,則函數返回非零值,否則返回 0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果實現不實現線程數的動態調整,則此函數始終返回 0。 有關詳細資訊,請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉參考

- 有關動態線程調整的說明,請參閱[omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested功能

該`omp_set_nested`函數啟用或禁用嵌套並行性。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*嵌套*計算為 0,則禁用嵌套並行性(這是預設值),嵌套並行區域由當前線程式列化並執行。 否則,將啟用嵌套並行性,嵌套的並行區域可能會部署其他線程以形成嵌套團隊。

當從程式返回零的部分調用時,`omp_in_parallel`此功能具有上述效果。 如果從程式的一部分調用函數`omp_in_parallel`返回非零值,則此函數的行為未定義。

此調用優先於`OMP_NESTED`環境變數。

啟用嵌套並行性后,用於執行嵌套並行區域的線程數將定義實現。 因此,即使啟用嵌套並行性,也允許符合 OpenMP 的實現序列化嵌套並行區域。

#### <a name="cross-references"></a>交叉參考

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested功能

如果`omp_get_nested`啟用嵌套並行性,則函數返回非零值;如果禁用,則返回 0。 有關嵌套並行性的詳細資訊,請參閱[omp_set_nested](#319-omp_set_nested-function)。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果實現不實現嵌套並行性,則此函數始終返回 0。

## <a name="32-lock-functions"></a>3.2 鎖定功能

本節中描述的函數操作用於同步的鎖。

對於以下函數,鎖變數必須具有類型`omp_lock_t`。 只能通過這些函數訪問此變數。 所有鎖函數都需要具有指向`omp_lock_t`類型的指標的參數。

- [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函數初始化一個簡單的鎖。
- [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函數刪除一個簡單的鎖。
- [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函數等待,直到一個簡單的鎖可用。
- [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函數釋放一個簡單的鎖。
- [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函數測試一個簡單的鎖。

對於以下函數,鎖變數必須具有類型`omp_nest_lock_t`。  只能通過這些函數訪問此變數。 所有可嵌套鎖函數都需要具有指向`omp_nest_lock_t`類型的指標的參數。

- [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函數初始化可嵌套鎖。
- [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函數刪除可嵌套鎖。
- [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函數等待,直到可嵌套鎖可用。
- [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函數釋放可嵌套鎖。
- [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函數測試可嵌套鎖。

OpenMP 鎖函數存取鎖變數的方式始終讀取和更新鎖變數的最新版本。 因此,OpenMP 程式不需要包含顯`flush`式 指令,以確保鎖變數的值在不同的線程之間一致。 (可能需要指令`flush`來使其他變數的值保持一致。

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock和omp_init_nest_lock功能

這些函數提供了初始化鎖的唯一方法。 每個函數初始化與參數*鎖*關聯的鎖,以便在即將到來的調用中使用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始狀態解鎖(即,沒有線程擁有鎖)。 對於可嵌套鎖,初始嵌套計數為零。 使用已初始化的鎖變數調用這些例程中的任何一個都不符合要求。

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock和omp_destroy_nest_lock功能

這些函式可確保未初始化指向鎖定變數*鎖定*。 其格式如下所示：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

使用未初始化或解鎖的鎖變數調用這些例程中的任何一個是不合規的。

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock和omp_set_nest_lock功能

這些函數中的每一個都會阻止執行函數的線程,直到指定的鎖可用,然後設置鎖。 如果未鎖定,則提供簡單的鎖。 如果可嵌套鎖已解鎖,或者該鎖已歸執行該函數的線程所有,則該鎖可用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

對於簡單鎖,函數的`omp_set_lock`參數必須指向初始化鎖變數。 鎖的所有權授予執行函數的線程。

對於可嵌套鎖,函數的`omp_set_nest_lock`參數必須指向初始化鎖變數。 嵌套計數遞增,線程被授予或保留鎖的擁有權。

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock和omp_unset_nest_lock功能

這些函數提供了釋放鎖擁有權的方法。 其格式如下所示：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

每個函數的參數必須指向執行函數的線程擁有的初始化鎖變數。 如果線程不擁有該鎖,則該行為未定義。

對於簡單鎖,`omp_unset_lock`函數釋放從鎖的擁有權中執行函數的線程。

對於可嵌套鎖,`omp_unset_nest_lock`函數將釋放嵌套計數,並在生成的計數為零時釋放從鎖的所有權執行函數的線程。

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock和omp_test_nest_lock功能

這些函數嘗試設置鎖,但不阻止線程的執行。 其格式如下所示：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

參數必須指向初始化鎖變數。 這些函數嘗試以與`omp_set_lock``omp_set_nest_lock`和相同的方式設置鎖,只不過它們不會阻止線程的執行。

對於簡單鎖,如果成功`omp_test_lock`設置鎖,函數將返回非零值;對於簡單鎖,函數將返回非零值。否則,它將返回零。

對於可嵌套鎖,如果成功`omp_test_nest_lock`設置鎖,函數將返回新的嵌套計數;否則,它將返回零。

## <a name="33-timing-routines"></a>3.3 計時程式程

本節中描述的功能支援便攜式掛鐘計時器:

- [omp_get_wtime](#331-omp_get_wtime-function)函數返回已經過的掛鐘時間。
- [omp_get_wtick](#332-omp_get_wtick-function)函數在連續時鐘刻度之間返回秒。

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime功能

該`omp_get_wtime`函數返回一個雙精度浮點值,該值等於經過的掛鐘時間(以秒為單位),因為"過去的某個時間"。  實際的「過去時間」是任意的,但保證在應用程式執行期間不會更改。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

預計該函數將用於測量已用時間,如以下範例所示:

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返回的時間是"每個線程時間",這意味著它們不需要在參與應用程式的所有線程之間全域一致。

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick功能

函數`omp_get_wtick`返回一個雙精度浮點值,等於連續時鐘刻度之間的秒數。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
