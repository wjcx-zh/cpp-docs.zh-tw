---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: d13b58fc05055ceecb6472003d7682c41c76e23d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222533"
---
# <a name="ltcondition_variablegt"></a>&lt;condition_variable&gt;

定義 [condition_variable](../standard-library/condition-variable-class.md) 和 [condition_variable_any](../standard-library/condition-variable-any-class.md) 類別，以用來建立等候條件為 True 時的物件。

此標頭使用「並行執行階段」(ConcRT)，因此您可以將它與其他 ConcRT 機制搭配使用。 如需有關 ConcRT 的詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。

## <a name="requirements"></a>需求

**標頭：**\<condition_variable>

**命名空間：** std

> [!NOTE]
> 在使用 **/clr**編譯的程式碼中，此標頭會遭到封鎖。

### <a name="remarks"></a>備註

等候條件變數的程式碼也必須使用 `mutex`。 呼叫端執行緒必須先鎖定 `mutex` 之後，才能呼叫等候條件變數的函數。 傳回呼叫的函數時，便會鎖定 `mutex`。 當執行緒等候條件為 True 時，不會鎖定 `mutex`。 由於每個等候條件變數的執行緒皆必須使用相同的 `mutex` 物件，因此不會發生未預期的結果。

任何類型的 Mutex 皆可搭配使用 `condition_variable_any` 類型的物件。 所使用的 Mutex 類型不需要提供 `try_lock` 方法。 `unique_lock<mutex>` 類型的 Mutex 僅可搭配使用 `condition_variable` 類型的物件。 此類型的物件可能會比 `condition_variable_any<unique_lock<mutex>>` 類型的物件更快。

若要等候事件，請先鎖定 Mutex，然後呼叫條件變數上的其中一個 `wait` 方法。 `wait` 呼叫會受到封鎖，直到其他執行緒通知條件變數為止。

未經適當通知就解除封鎖等候條件變數的執行緒時，會發生「假喚醒」** 的情況。 若要辨識這類假喚醒，等候條件為 True 的程式碼應在 wait 函式傳回程式碼時，明確檢查該項條件。 上述作業通常是透過使用迴圈來完成，因此您可以使用 `wait(unique_lock<mutex>& lock, Predicate pred)` 來執行這個迴圈。

```cpp
while (condition is false)
    wait for condition variable;
```

`condition_variable_any` 和 `condition_variable` 類別都有三種等候條件的方法。

- `wait` 會等候無限制的時間週期。

- `wait_until` 會等候到指定的 `time` 為止。

- `wait_for` 會等候指定的 `time interval`。

每種方法皆有兩個多載的版本。 其中一個只會等待，並可能會假喚醒。 另一個則會使用述詞中定義的其他範本引數。 在述詞為之前，方法不會傳回 **`true`** 。

每個類別也有兩個方法，可用來通知條件變數其條件為 **`true`** 。

- `notify_one` 會喚醒正在等候條件變數的其中一個執行緒。

- `notify_all` 會喚醒正在等候條件變數的所有執行緒。

## <a name="functions-and-enums"></a>函數和列舉

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[condition_variable 類別](../standard-library/condition-variable-class.md)\
[condition_variable_any 類別](../standard-library/condition-variable-any-class.md)
