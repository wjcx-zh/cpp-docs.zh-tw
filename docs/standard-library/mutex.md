---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: d5ff6f2a81a5caa564792e2c0cb43b7722c3e1dd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838543"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

包含標準標頭 \<mutex> ，以定義類別 `mutex` 、 `recursive_mutex` 、 `timed_mutex` 和 `recursive_timed_mutex` ; 範本 `lock_guard` 和 `unique_lock` ; 以及定義相互排除程式碼區域的支援類型和函式。

> [!WARNING]
> 從 Visual Studio 2015 開始，c + + 標準程式庫同步處理類型是以 Windows 同步處理原始物件為基礎，不再使用 ConcRT (，除非目標平臺是 Windows XP) 。 中定義的類型 \<mutex> 不應該與任何 ConcRT 類型或函式搭配使用。

## <a name="requirements"></a>規格需求

**標頭：**\<mutex>

**命名空間：** std

## <a name="remarks"></a>備註

> [!NOTE]
> 在使用 **/clr**編譯的程式碼中，此標頭會遭到封鎖。

類別 `mutex` 和 `recursive_mutex` 是 *mutex 類型*。 mutex 型別具有不會擲回例外狀況的預設建構函式和解構函式。 當多個執行緒嘗試鎖定相同物件時，這些物件具有可提供互斥功能的方法。 具體來說，mutex 型別包含方法 `lock`、`try_lock` 和 `unlock`：

- `lock` 方法會封鎖呼叫的執行緒，直到 mutex 取得擁有權。 它的傳回值會遭到忽略。

- `try_lock` 方法會嘗試在不造成封鎖的情況下取得 mutex 擁有權。 它的傳回型別可以轉換成， **`bool`** 而且 **`true`** 如果方法取得擁有權，則為，否則為 **`false`** 。

- `unlock` 方法會從呼叫的執行緒釋放 mutex 擁有權。

您也可以使用 mutex 型別作為型別引數，以具現化範本 `lock_guard` 和 `unique_lock`。 您可以使用這些類型的物件作為 [condition_variable_any](../standard-library/condition-variable-any-class.md) 範本中 wait 成員函式的 `Lock` 引數。

「計時 mutex 類型」** 可滿足 mutex 類型的需求。 此外，它具有 `try_lock_for` `try_lock_until` 必須可使用一個引數來呼叫的和方法，而且必須傳回可轉換成的型別 **`bool`** 。 計時 mutex 型別可以使用其他引數來定義這些函式，前提是這些所有其他引數都有預設值。

- `try_lock_for` 方法必須可使用一個引數 `Rel_time` 來呼叫，其類型是 [chrono::duration](../standard-library/duration-class.md) 的具現化。 此方法會嘗試取得 mutex 的擁有權，但會在 `Rel_time` 所指定的時間內傳回，無論是否成功。 如果方法取得擁有權，則傳回值會轉換為， **`true`** 否則，傳回值會轉換為 **`false`** 。

- `try_lock_until` 方法必須可使用一個引數 `Abs_time` 呼叫，其類型是 [chrono::time_point](../standard-library/time-point-class.md) 的具現化。 此方法會嘗試取得 mutex 的擁有權，但會在不晚於 `Abs_time` 所指定的時間內傳回，無論是否成功。 如果方法取得擁有權，則傳回值會轉換為， **`true`** 否則，傳回值會轉換為 **`false`** 。

mutex 類型也稱為「可鎖定類型」**。 如果它不提供成員函式 `try_lock`，它便是「基本可鎖定類型」**。 計時 mutex 類型也稱為「計時可鎖定類型」**。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[lock_guard 類別](../standard-library/lock-guard-class.md)|表示可以具現化的範本，用來建立解構函式會解除鎖定 `mutex` 的物件。|
|[mutex 類別 (c + + 標準程式庫) ](../standard-library/mutex-class-stl.md)|表示 mutex 型別。 使用這個型別的物件來強制程式內的互斥。|
|[recursive_mutex 類別](../standard-library/recursive-mutex-class.md)|表示 mutex 型別。 相較於 `mutex` 類別，針對已鎖定物件的呼叫鎖定方法行為已妥善定義。|
|[recursive_timed_mutex 類別](../standard-library/recursive-timed-mutex-class.md)|表示 計時 mutex 型別。 使用這個型別的物件來強制程式內限時的互斥。 不同於型別 `timed_mutex` 的物件，針對 `recursive_timed_mutex` 物件的呼叫鎖定方法效果已妥善定義。|
|[scoped_lock 類別](../standard-library/scoped-lock-class.md)||
|[timed_mutex 類別](../standard-library/timed-mutex-class.md)|表示 計時 mutex 型別。 使用這個型別的物件來強制程式內限時的互斥。|
|[unique_lock 類別](../standard-library/unique-lock-class.md)|表示可以具現化的範本，用來建立管理鎖定和解除鎖定 `mutex` 的物件。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|提供用來呼叫指定之可呼叫物件一次執行期間的機制。|
|[鎖](../standard-library/mutex-functions.md#lock)|會嘗試鎖定所有不包含死結的引數。|
|[交換](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>結構

|名稱|描述|
|-|-|
|[adopt_lock_t 結構](../standard-library/adopt-lock-t-structure.md)|表示用來定義 `adopt_lock` 的型別。|
|[defer_lock_t 結構](../standard-library/defer-lock-t-structure.md)|表示定義 `defer_lock` 物件的型別，該物件用來選取 `unique_lock` 的其中一個多載建構函式。|
|[once_flag 結構](../standard-library/once-flag-structure.md)|表示搭配樣板函式 **`struct`** 使用的， `call_once` 以確保初始化程式碼只會呼叫一次，即使有多個執行緒執行也一樣。|
|[try_to_lock_t 結構](../standard-library/try-to-lock-t-structure.md)|表示 **`struct`** ，它會定義 `try_to_lock` 物件，並且用來選取的其中一個多載的函式 `unique_lock` 。|

### <a name="variables"></a>變數

|名稱|描述|
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|表示可以針對 `lock_guard` 和 `unique_lock` 傳遞至建構函式的物件，指出也會傳遞至建構函式的 mutex 物件已鎖定。|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|表示可以針對 `unique_lock` 傳遞至建構函式的物件，指出建構函式不應鎖定也會傳遞至建構函式的 mutex 物件。|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|表示可以針對 `unique_lock` 傳遞至建構函式的物件，指出建構函式應嘗試解除鎖定也會未經封鎖傳遞至建構函式的 `mutex`。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
