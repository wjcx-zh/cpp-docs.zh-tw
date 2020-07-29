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
ms.openlocfilehash: f7df639a879bad7af1b4de401460ff298e466c78
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215812"
---
# <a name="critical_section-class"></a>critical_section 類別

其為並行執行階段明確察覺且不可重新進入的 Mutex。

## <a name="syntax"></a>語法

```cpp
class critical_section;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`native_handle_type`|`critical_section` 物件的參考。|

### <a name="public-classes"></a>公用類別

|名稱|說明|
|----------|-----------------|
|[critical_section::scoped_lock 類別](#critical_section__scoped_lock_class)|物件的例外狀況安全 RAII 包裝函式 `critical_section` 。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[critical_section](#ctor)|構造新的重要區段。|
|[~ critical_section 的析構函式](#dtor)|終結重要區段。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[狀](#lock)|取得這個重要區段。|
|[native_handle](#native_handle)|傳回平臺特定的原生控制碼（如果有的話）。|
|[try_lock](#try_lock)|嘗試取得鎖定而不封鎖。|
|[try_lock_for](#try_lock_for)|嘗試取得鎖定，而不進行特定毫秒數的封鎖。|
|[解除鎖定](#unlock)|解除鎖定重要區段。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`critical_section`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** 並行

## <a name="critical_section"></a><a name="ctor"></a>critical_section

構造新的重要區段。

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>~ critical_section

終結重要區段。

```cpp
~critical_section();
```

### <a name="remarks"></a>備註

在執行函式時，預期不會再保留鎖定。 允許「關鍵」區段的鎖定仍然保留，會導致未定義的行為。

## <a name="lock"></a><a name="lock"></a>狀

取得這個重要區段。

```cpp
void lock();
```

### <a name="remarks"></a>備註

使用[scoped_lock](#critical_section__scoped_lock_class)結構通常是以例外狀況安全的方式來取得和釋放物件，是比較安全的作法 `critical_section` 。

如果呼叫內容已持有鎖定，就會擲回[improper_lock](improper-lock-class.md)例外狀況。

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

傳回平臺特定的原生控制碼（如果有的話）。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

重要區段的參考。

### <a name="remarks"></a>備註

`critical_section`物件未與 Windows 作業系統的平臺特定原生控制碼建立關聯。 方法只會傳回物件本身的參考。

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section：： scoped_lock 類別

物件的例外狀況安全 RAII 包裝函式 `critical_section` 。

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock：： scoped_lock

會建立 `scoped_lock` 物件，並取得 `critical_section` 傳入參數的物件 `_Critical_section` 。 如果關鍵區段由另一個執行緒持有，此呼叫將會封鎖。

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>參數

*_Critical_section*<br/>
要鎖定的重要區段。

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock：： ~ scoped_lock

終結 `scoped_lock` 物件，並釋放其函式中所提供的重要區段。

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

嘗試取得鎖定而不封鎖。

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

如果已取得鎖定，則為值， **`true`** 否則為值 **`false`** 。

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

嘗試取得鎖定，而不進行特定毫秒數的封鎖。

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>參數

*_Timeout*<br/>
在逾時前要等候的毫秒數。

### <a name="return-value"></a>傳回值

如果已取得鎖定，則為值， **`true`** 否則為值 **`false`** 。

## <a name="unlock"></a><a name="unlock"></a>解除鎖定

解除鎖定重要區段。

```cpp
void unlock();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[reader_writer_lock 類別](reader-writer-lock-class.md)
