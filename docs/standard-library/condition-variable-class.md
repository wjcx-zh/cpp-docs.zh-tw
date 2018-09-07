---
title: condition_variable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
dev_langs:
- C++
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4d31a93ac8e0f7785ea567821c0ac6b0ad6a58
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109832"
---
# <a name="conditionvariable-class"></a>condition_variable 類別

當您具有 `unique_lock<mutex>` 類型的 `mutex` 時，可使用 `condition_variable` 類別來等候事件。 此類型的物件可能比 [condition_variable_any<unique_lock\<mutex>>](../standard-library/condition-variable-any-class.md) 類型的物件效能更好。

## <a name="syntax"></a>語法

```cpp
class condition_variable;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[condition_variable](#condition_variable)|建構 `condition_variable` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[native_handle](#native_handle)|傳回代表 condition_variable 控制代碼的實作特定類型。|
|[notify_all](#notify_all)|解除封鎖所有等候 `condition_variable` 物件的執行緒。|
|[notify_one](#notify_one)|解除封鎖其中一個等候 `condition_variable` 物件的執行緒。|
|[等候](#wait)|封鎖執行緒。|
|[wait_for](#wait_for)|封鎖執行緒，並設定要在多久時間間隔之後解除封鎖執行緒。|
|[wait_until](#wait_until)|封鎖執行緒，並設定要解除封鎖執行緒的時間點上限。|

## <a name="requirements"></a>需求

**標頭：** \<condition_variable >

**命名空間：** std

## <a name="condition_variable"></a>  condition_variable::condition_variable 建構函式

建構 `condition_variable` 物件。

```cpp
condition_variable();
```

### <a name="remarks"></a>備註

如果可用的記憶體不足，建構函式會擲回具有 `not_enough_memory` 錯誤碼的 [system_error](../standard-library/system-error-class.md) 物件。 如果因為無法使用其他部分資源，而無法建構物件，建構函式會擲回具有 `resource_unavailable_try_again` 錯誤碼的 `system_error` 物件。

## <a name="native_handle"></a>  condition_variable::native_handle

傳回代表 condition_variable 控制代碼的實作特定類型。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

系統會將 `native_handle_type` 定義為並行執行階段內部資料結構的指標。

## <a name="notify_all"></a>  condition_variable::notify_all

解除封鎖所有等候 `condition_variable` 物件的執行緒。

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable::notify_one

解除封鎖其中一個等候 `condition_variable` 物件的執行緒。

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable::wait

封鎖執行緒。

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*<br/>
[unique_lock\<mutex>](../standard-library/unique-lock-class.md) 物件。

*預測*<br/>
傳回的任何運算式 **，則為 true**或是**false**。

### <a name="remarks"></a>備註

系統會封鎖第一個方法，直到 `condition_variable` 物件收到 [notify_one](#notify_one) 或 [notify_all](#notify_all) 的呼叫訊號為止。 它也可能會假性喚醒。

而第二種方法會執行下列程式碼。

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable::wait_for

封鎖執行緒，並設定要在多久時間間隔之後解除封鎖執行緒。

```cpp
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time,
    Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*<br/>
[unique_lock\<mutex>](../standard-library/unique-lock-class.md) 物件。

*Rel_time*<br/>
`chrono::duration` 物件，指定喚醒執行緒之前的時間。

*預測*<br/>
傳回的任何運算式 **，則為 true**或是**false**。

### <a name="return-value"></a>傳回值

第一種方法會傳回`cv_status::timeout`而等候終止時，如果*Rel_time*已過。 否則，方法會傳回 `cv_status::no_timeout`。

第二個方法會傳回值*Pred*。

### <a name="remarks"></a>備註

第一種方法會封鎖直到`condition_variable`物件的呼叫所收到[notify_one](#notify_one)或[notify_all](#notify_all)或之前的時間間隔*Rel_time*經過。 它也可能會假性喚醒。

而第二種方法會執行下列程式碼。

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable::wait_until

封鎖執行緒，並設定要解除封鎖執行緒的時間點上限。

```cpp
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*<br/>
[unique_lock\<mutex>](../standard-library/unique-lock-class.md) 物件。

*Abs_time*<br/>
[chrono::time_point](../standard-library/time-point-class.md) 物件。

*預測*<br/>
傳回的任何運算式 **，則為 true**或是**false**。

### <a name="return-value"></a>傳回值

方法會傳回`cv_status`類型傳回`cv_status::timeout`而等候終止時，如果*Abs_time*耗盡。 否則，方法會傳回 `cv_status::no_timeout`。

方法會傳回**bool**傳回的值*Pred*。

### <a name="remarks"></a>備註

系統會封鎖第一個方法，直到 `condition_variable` 物件收到 [notify_one](#notify_one) 或 [notify_all](#notify_all) 的呼叫訊號，或直到 `Abs_time` 為止。 它也可能會假性喚醒。

而第二種方法會執行下列程式碼。

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

第三個和第四個方法會使用 `xtime` 類型的物件指標來取代 `chrono::time_point` 物件。 `xtime` 物件可指定等待訊號的時間量上限。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
