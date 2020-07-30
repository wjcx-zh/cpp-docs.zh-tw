---
title: condition_variable_any 類別
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 9187bddef456f131982d39fd64dacea5953b959b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222559"
---
# <a name="condition_variable_any-class"></a>condition_variable_any 類別

使用 `condition_variable_any` 類別，以等候具有任何 `mutex` 類型的事件。

## <a name="syntax"></a>語法

```cpp
class condition_variable_any;
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[condition_variable_any](#condition_variable_any)|建構 `condition_variable_any` 物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[notify_all](#notify_all)|解除封鎖所有等候 `condition_variable_any` 物件的執行緒。|
|[notify_one](#notify_one)|解除封鎖其中一個等候 `condition_variable_any` 物件的執行緒。|
|[等候](#wait)|封鎖執行緒。|
|[wait_for](#wait_for)|封鎖執行緒，並設定要在多久時間間隔之後解除封鎖執行緒。|
|[wait_until](#wait_until)|封鎖執行緒，並設定要解除封鎖執行緒的時間點上限。|

## <a name="condition_variable_any"></a><a name="condition_variable_any"></a>condition_variable_any

建構 `condition_variable_any` 物件。

```cpp
condition_variable_any();
```

### <a name="remarks"></a>備註

如果可用的記憶體不足，建構函式會擲回具有 `not_enough_memory` 錯誤碼的 [system_error](../standard-library/system-error-class.md) 物件。 如果因為無法使用其他部分資源，而無法建構物件，建構函式會擲回具有 `resource_unavailable_try_again` 錯誤碼的 `system_error` 物件。

## <a name="notify_all"></a><a name="notify_all"></a>notify_all

解除封鎖所有等候 `condition_variable_any` 物件的執行緒。

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a><a name="notify_one"></a>notify_one

解除封鎖其中一個等候 `condition_variable_any` 物件的執行緒。

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a><a name="wait"></a>等候

封鎖執行緒。

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*\
任何類型的 `mutex` 物件。

*Pred*\
傳回或的任何 **`true`** 運算式 **`false`** 。

### <a name="remarks"></a>備註

系統會封鎖第一個方法，直到 `condition_variable_any` 物件收到 [notify_one](../standard-library/condition-variable-class.md#notify_one) 或 [notify_all](../standard-library/condition-variable-class.md#notify_all) 的呼叫訊號為止。 它也可能會假性喚醒。

第二種方法則會執行下列程式碼。

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a><a name="wait_for"></a>wait_for

封鎖執行緒，並設定要在多久時間間隔之後解除封鎖執行緒。

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*\
任何類型的 `mutex` 物件。

*Rel_time*\
`chrono::duration` 物件，指定喚醒執行緒之前的時間。

*Pred*\
傳回或的任何 **`true`** 運算式 **`false`** 。

### <a name="return-value"></a>傳回值

`cv_status::timeout`如果*Rel_time*已過，則第一個方法會傳回。 否則，方法會傳回 `cv_status::no_timeout`。

第二個方法會傳回*Pred*的值。

### <a name="remarks"></a>備註

第一個方法 `condition_variable_any` 會封鎖，直到呼叫[notify_one](../standard-library/condition-variable-class.md#notify_one)或[notify_all](../standard-library/condition-variable-class.md#notify_all)，或直到時間間隔*Rel_time*經過通知為止。 它也可能會假性喚醒。

第二種方法則會執行下列程式碼。

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a><a name="wait_until"></a>wait_until

封鎖執行緒，並設定要解除封鎖執行緒的時間點上限。

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>參數

*Lck*\
Mutex 物件。

*Abs_time*\
[chrono::time_point](../standard-library/time-point-class.md) 物件。

*Pred*\
傳回或的任何 **`true`** 運算式 **`false`** 。

### <a name="return-value"></a>傳回值

`cv_status` `cv_status::timeout` 如果*Abs_time*超過時，則傳回類型的方法會傳回。 否則，方法會傳回 `cv_status::no_timeout`。

傳回的方法會傳回 **`bool`** *Pred*的值。

### <a name="remarks"></a>備註

第一個方法 `condition_variable` 會封鎖，直到物件被呼叫[notify_one](../standard-library/condition-variable-class.md#notify_one)或[notify_all](../standard-library/condition-variable-class.md#notify_all)，或直到*Abs_time*為止。 它也可能會假性喚醒。

第二種方法則會執行下列程式碼。

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

第三個和第四個方法會使用 `xtime` 類型的物件指標來取代 `chrono::time_point` 物件。 `xtime` 物件可指定等待訊號的時間量上限。
