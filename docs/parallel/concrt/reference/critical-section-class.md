---
title: critical_section 類別
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372684"
---
# <a name="critical_section-class"></a>critical_section 類別

其為並行執行階段明確察覺且不可重新進入的 Mutex。

## <a name="syntax"></a>語法

```cpp
class critical_section;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`native_handle_type`|`critical_section` 物件的參考。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[critical_section::scoped_lock 類別](#critical_section__scoped_lock_class)|`critical_section`對象的異常安全 RAII 包裝器。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[critical_section](#ctor)|構造新的關鍵部分。|
|[*critical_section析構函數](#dtor)|銷毀關鍵部分。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[鎖定](#lock)|獲取此關鍵部分。|
|[native_handle](#native_handle)|返回特定於平臺的本機句柄(如果存在)。|
|[try_lock](#try_lock)|嘗試在不阻塞的情況下獲取鎖。|
|[try_lock_for](#try_lock_for)|嘗試取得鎖定，而不進行特定毫秒數的封鎖。|
|[解除鎖定](#unlock)|解鎖關鍵部分。|

## <a name="remarks"></a>備註

有關詳細資訊,請參閱[同步資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`critical_section`

## <a name="requirements"></a>需求

**標題:** concrt.h

**命名空間:** 併發

## <a name="critical_section"></a><a name="ctor"></a>critical_section

構造新的關鍵部分。

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>*critical_section

銷毀關鍵部分。

```cpp
~critical_section();
```

### <a name="remarks"></a>備註

當析構函數運行時,預計鎖不再被持有。 允許關鍵部分在鎖定下進行析構會導致未定義的行為。

## <a name="lock"></a><a name="lock"></a>鎖

獲取此關鍵部分。

```cpp
void lock();
```

### <a name="remarks"></a>備註

利用[scoped_lock](#critical_section__scoped_lock_class)構造以異常安全的方式獲取和`critical_section`釋放 物件通常更安全。

如果調用上下文已持有鎖,將引發[improper_lock](improper-lock-class.md)異常。

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

返回特定於平臺的本機句柄(如果存在)。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

對關鍵部分的引用。

### <a name="remarks"></a>備註

物件`critical_section`不與 Windows 作業系統的特定平臺本機句柄相關聯。 該方法僅返回對物件本身的引用。

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section::scoped_lock類

`critical_section`對象的異常安全 RAII 包裝器。

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock:scoped_lock

建構`scoped_lock`對象並`critical_section``_Critical_section`獲取在參數中傳遞的物件。 如果關鍵部分由另一個線程持有,則此調用將阻止。

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>參數

*_Critical_section*<br/>
要鎖定的關鍵部分。

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock:~scoped_lock

銷毀`scoped_lock`物件並釋放其構造函數中提供的關鍵部分。

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

嘗試在不阻塞的情況下獲取鎖。

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

如果取得了鎖,則值**為 true**;否則,該值**為 false**。

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

嘗試取得鎖定，而不進行特定毫秒數的封鎖。

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>參數

*_Timeout*<br/>
在逾時前要等候的毫秒數。

### <a name="return-value"></a>傳回值

如果取得了鎖,則值**為 true**;否則,該值**為 false**。

## <a name="unlock"></a><a name="unlock"></a>解除鎖定

解鎖關鍵部分。

```cpp
void unlock();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[reader_writer_lock 類別](reader-writer-lock-class.md)
