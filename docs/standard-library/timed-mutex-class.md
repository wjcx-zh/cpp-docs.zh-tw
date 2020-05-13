---
title: timed_mutex 類別
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 6c9840d9b8c00d4b03e6ea329c7707a0edff9512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368009"
---
# <a name="timed_mutex-class"></a>timed_mutex 類別

表示*時時多斥式*。 透過在程式內進行限時封鎖，可以使用這個類型的物件來強制執行互斥。

## <a name="syntax"></a>語法

```cpp
class timed_mutex;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|建構未鎖定的 `timed_mutex` 物件。|
|[timed_mutex:timed_mutex析構器](#dtortimed_mutex_destructor)|釋出 `timed_mutex` 物件所使用的任何資源。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[鎖定](#lock)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|
|[try_lock](#try_lock)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|
|[try_lock_for](#try_lock_for)|嘗試取得所指定時間間隔內 `mutex` 的所有權。|
|[try_lock_until](#try_lock_until)|嘗試取得所指定時間間隔之前 `mutex` 的所有權。|
|[解除鎖定](#unlock)|釋放 `mutex` 的擁有權。|

## <a name="requirements"></a>需求

**標題:**\<互斥>

**命名空間：** std

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex:鎖定

封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。

```cpp
void lock();
```

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex:timed_mutex構造函數

建構未鎖定的 `timed_mutex` 物件。

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex:timed_mutex析構器

釋出 `mutex` 物件所使用的任何資源。

```cpp
~timed_mutex();
```

### <a name="remarks"></a>備註

如果執行解構函式時物件已鎖定，則行為是未定義的。

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex:try_lock

嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex:try_lock_for

嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>參數

*Rel_time*\
[chrono::duration](../standard-library/duration-class.md) 物件，此物件會指定方法嘗試取得 `mutex` 擁有權的時間上限。

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex:try_lock_until

嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>參數

*Abs_time*\
這個時間點所指定的臨界值一超過，方法就不再嘗試取得 `mutex` 的擁有權。

### <a name="return-value"></a>傳回值

**如果**該方法成功獲得 的`mutex`擁有權,否則,**假**。

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex:解鎖

釋放 `mutex` 的擁有權。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
