---
title: mutex 類別 (C++ 標準程式庫)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 20e2165a70dec8a3d3918eece6cb78057ac19138
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233037"
---
# <a name="mutex-class-c-standard-library"></a>mutex 類別 (C++ 標準程式庫)

表示*mutex 類型*。 這個類型的物件可以用來強制程式內的互斥。

## <a name="syntax"></a>語法

```cpp
class mutex;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[量](#mutex)|建構 `mutex` 物件。|
|[mutex::~mutex 解構函式](#dtormutex_destructor)|釋放 `mutex` 物件使用的所有資源。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[狀](#lock)|封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。|
|[native_handle](#native_handle)|傳回表示 mutex 控制代碼的實作特定類型。|
|[try_lock](#try_lock)|嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。|
|[解除鎖定](#unlock)|釋放 `mutex` 的擁有權。|

## <a name="requirements"></a>需求

**標頭：**\<mutex>

**命名空間：** std

## <a name="mutexlock"></a><a name="lock"></a>mutex：： lock

封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。

```cpp
void lock();
```

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>mutex：： mutex 函數

建構未鎖定的 `mutex` 物件。

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>mutex：： ~ mutex 析構函式

釋出 `mutex` 物件所使用的任何資源。

```cpp
~mutex();
```

### <a name="remarks"></a>備註

如果執行解構函式時物件已鎖定，則行為是未定義的。

## <a name="mutexnative_handle"></a><a name="native_handle"></a>mutex：： native_handle

傳回表示 mutex 控制代碼的實作特定類型。 您可以利用實作特定的方式來使用 mutex 控制代碼。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

`native_handle_type` 會定義為 `Concurrency::critical_section *`，這會轉換為 `void *`。

## <a name="mutextry_lock"></a><a name="try_lock"></a>mutex：： try_lock

嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

**`true`** 如果方法成功取得的擁有權，則為 `mutex` ，否則為 **`false`** 。

### <a name="remarks"></a>備註

如果呼叫的執行緒已經擁有 `mutex`，則行為是未定義的。

## <a name="mutexunlock"></a><a name="unlock"></a>mutex：： unlock

釋放 `mutex` 的擁有權。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
