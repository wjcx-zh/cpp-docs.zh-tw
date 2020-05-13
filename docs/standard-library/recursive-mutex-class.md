---
title: recursive_mutex 類別
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320211"
---
# <a name="recursive_mutex-class"></a>recursive_mutex 類別

表示*互斥類型*。 相較於 [mutex](../standard-library/mutex-class-stl.md)，已針對已經鎖定的物件妥善定義呼叫鎖定方法的行為。

## <a name="syntax"></a>語法

```cpp
class recursive_mutex;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|建構 `recursive_mutex` 物件。|
|[~recursive_mutex 解構函式](#dtorrecursive_mutex_destructor)|釋出 `recursive_mutex` 物件所使用的任何資源。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[鎖定](#lock)|在呼叫執行緒取得 mutex 的擁有權之前，封鎖該執行緒。|
|[try_lock](#try_lock)|嘗試在不封鎖 mutex 的情況下，取得它的擁有權。|
|[解除鎖定](#unlock)|釋放 mutex 的擁有權。|

## <a name="requirements"></a>需求

**標題:**\<互斥>

**命名空間：** std

## <a name="lock"></a><a name="lock"></a>鎖

封鎖呼叫的執行緒，直到執行緒取得 `mutex` 的擁有權。

```cpp
void lock();
```

### <a name="remarks"></a>備註

如果呼叫執行緒已經擁有 `mutex`，方法會立即傳回，而先前的鎖定仍持續有效。

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

建構未鎖定的 `recursive_mutex` 物件。

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

釋放物件使用的所有資源。

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>備註

如果執行解構函式時物件已鎖定，則行為是未定義的。

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

嘗試在不造成封鎖的情況下，取得 `mutex` 的擁有權。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>傳回值

如果該方法成功獲得`mutex`或調用線程已擁有`mutex**; otherwise, **false`,**則為 true。**

### <a name="remarks"></a>備註

如果呼叫線程已擁有,`mutex`則函數將立即返回**true,** 並且以前的鎖仍然有效。

## <a name="unlock"></a><a name="unlock"></a>解除鎖定

釋放 mutex 的擁有權。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

這個方法只會在呼叫它的次數與在 `recursive_mutex` 物件上成功呼叫 [lock](#lock) 和 [try_lock](#try_lock) 的次數一樣多之後，才會釋放 `mutex` 的擁有權。

如果呼叫的執行緒未擁有 `mutex`，則行為是未定義的。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
