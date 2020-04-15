---
title: unique_lock 類別
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 59201fbaba6f2e8ae0ed5f53925b287b4d33aab3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367263"
---
# <a name="unique_lock-class"></a>unique_lock 類別

表示可以具現化的範本，用來建立管理鎖定和解除鎖定 `mutex` 的物件。

## <a name="syntax"></a>語法

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>備註

範本引數 `Mutex` 必須指定一個「mutex 類型」**。

在內部,`unique_lock`儲存指向`mutex`關聯 物件的指標和指示當前線程是否擁有`mutex`的**bool。**

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`mutex_type`|與範本引數 `Mutex` 同義。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unique_lock](#unique_lock)|建構 `unique_lock` 物件。|
|[*unique_lock析構函數](#dtorunique_lock_destructor)|釋放任何與 `unique_lock` 物件相關聯的資源。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[鎖定](#lock)|封鎖呼叫的執行緒，直到執行緒取得相關聯 `mutex` 的擁有權。|
|[互斥](#mutex)|擷取相關聯 `mutex` 的已儲存指標。|
|[owns_lock](#owns_lock)|指定呼叫的執行緒是否擁有相關聯 `mutex`。|
|[釋放](#release)|從相關聯 `mutex` 物件解除 `unique_lock` 物件的關聯。|
|[交換](#swap)|交換指定物件的相關聯 `mutex` 和擁有權狀態。|
|[try_lock](#try_lock)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|
|[try_lock_for](#try_lock_for)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|
|[try_lock_until](#try_lock_until)|嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。|
|[解除鎖定](#unlock)|釋放相關聯 `mutex` 的擁有權。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算子布爾](#op_bool)|指定呼叫的執行緒是否有相關聯 `mutex` 的擁有權。|
|[運算子*](#op_eq)|複製指定物件的已儲存 `mutex` 指標和相關聯擁有權狀態。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

*unique_lock*

## <a name="requirements"></a>需求

**標題:**\<互斥>

**命名空間：** std

## <a name="lock"></a><a name="lock"></a>鎖

封鎖呼叫的執行緒，直到執行緒取得相關聯 `mutex` 的擁有權。

```cpp
void lock();
```

### <a name="remarks"></a>備註

如果儲存`mutex`的指標為 NULL,則此方法將引發一個錯誤代碼為`operation_not_permitted`的[system_error。](../standard-library/system-error-class.md)

如果呼叫的執行緒已經擁有相關聯 `mutex`，此方法會擲回錯誤碼為 `resource_deadlock_would_occur` 的 `system_error`。

否則,此方法將調用`lock`關聯`mutex`的 ,並將內部線程擁有權標誌設定為**true**。

## <a name="mutex"></a><a name="mutex"></a>互斥

擷取相關聯 `mutex` 的已儲存指標。

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="operator-bool"></a><a name="op_bool"></a>運算子布爾

指定呼叫的執行緒是否有相關聯 mutex 的擁有權。

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>傳回值

如果線程擁有互斥體,**則為 true;** 否則**錯誤**。

## <a name="operator"></a><a name="op_eq"></a>運算子*

複製指定物件的已儲存 `mutex` 指標和相關聯擁有權狀態。

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
`unique_lock` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

如果呼叫的執行緒擁有先前的相關聯 `mutex`，在此方法於 `mutex` 上呼叫 `unlock` 之前，它會指派新的值。

複製後,此方法將 *「其他」* 設定為預設構造狀態。

## <a name="owns_lock"></a><a name="owns_lock"></a>owns_lock

指定呼叫的執行緒是否擁有相關聯 `mutex`。

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>傳回值

如果線程擁有`mutex`,**則為 true。** 否則,**假**。

## <a name="release"></a><a name="release"></a>釋放

從相關聯 `mutex` 物件解除 `unique_lock` 物件的關聯。

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>傳回值

已儲存 `mutex` 指標先前的值。

### <a name="remarks"></a>備註

此方法將儲存`mutex`指標的值設定為 0,並將內部`mutex`擁有權旗標設定為**false**。

## <a name="swap"></a><a name="swap"></a>交換

交換指定物件的相關聯 `mutex` 和擁有權狀態。

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
`unique_lock` 物件。

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果儲存`mutex`的指標為 NULL,則該方法將引發一個錯誤代碼為`operation_not_permitted`的[system_error。](../standard-library/system-error-class.md)

如果呼叫的執行緒已經擁有 `mutex`，方法會擲回錯誤碼為 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>參數

*Rel_time*\
[chrono::duration](../standard-library/duration-class.md) 物件，此物件會指定方法嘗試取得 `mutex` 擁有權的時間上限。

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果儲存`mutex`的指標為 NULL,則該方法將引發一個錯誤代碼為`operation_not_permitted`的[system_error。](../standard-library/system-error-class.md)

如果呼叫的執行緒已經擁有 `mutex`，方法會擲回錯誤碼為 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

嘗試在不造成封鎖的情況下，取得關聯 `mutex` 的擁有權。

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>參數

*Abs_time*\
這個時間點所指定的臨界值一超過，方法就不再嘗試取得 `mutex` 的擁有權。

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果儲存`mutex`的指標為 NULL,則該方法將引發一個錯誤代碼為`operation_not_permitted`的[system_error。](../standard-library/system-error-class.md)

如果呼叫的執行緒已經擁有 `mutex`，方法會擲回錯誤碼為 `resource_deadlock_would_occur` 的 `system_error`。

## <a name="unique_lock-constructor"></a><a name="unique_lock"></a>unique_lock建構函數

建構 `unique_lock` 物件。

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>參數

*Mtx*\
mutex 類型物件。

*Rel_time*\
[chrono::duration](../standard-library/duration-class.md) 物件，此物件會指定方法嘗試取得 `mutex` 擁有權的時間上限。

*Abs_time*\
這個時間點所指定的臨界值一超過，方法就不再嘗試取得 `mutex` 的擁有權。

*其他*\
`unique_lock` 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構相關聯 mutex 指標值為 0 的物件。

第二個構造*函數從其他*移動關聯的互斥體狀態。 移動後,*其他*不再與互斥體關聯。

其餘的構造函數將& *Mtx*存儲`mutex`為存儲的指標。 `mutex` 的擁有權取決於第二個引數 (如果存在的話)。

|||
|-|-|
|`No argument`|擁有權是透過在相關聯 `mutex` 物件上呼叫 `lock` 方法來取得。|
|`Adopt`|取得擁有權。 呼叫建構函式時，必須鎖定 `Mtx`。|
|`Defer`|將假設呼叫的執行緒不擁有 `mutex` 物件。 當呼叫建構函式時，不能鎖定 `Mtx`。|
|`Try`|擁有權是透過在相關聯 `mutex` 物件上呼叫 `try_lock` 來決定。 建構函式不會擲回任何項目。|
|`Rel_time`|擁有權是透過呼叫 `try_lock_for(Rel_time)` 來決定。|
|`Abs_time`|擁有權是透過呼叫 `try_lock_until(Abs_time)` 來決定。|

## <a name="unique_lock-destructor"></a><a name="dtorunique_lock_destructor"></a>  ~unique_lock 解構函式

釋放任何與 `unique_lock` 物件相關聯的資源。

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>備註

如果呼叫的執行緒擁有相關聯 `mutex`，解構函式會透過在 `mutex` 物件上呼叫 unlock 來釋放擁有權。

## <a name="unlock"></a><a name="unlock"></a>解除鎖定

釋放相關聯 `mutex` 的擁有權。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

如果呼叫的執行緒不擁有相關聯 `mutex`，此方法會擲回錯誤碼為 `operation_not_permitted` 的 [system_error](../standard-library/system-error-class.md)。

否則,此方法將調用`unlock`關聯`mutex`的 ,並將內部線程擁有權標誌設置為**false**。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
