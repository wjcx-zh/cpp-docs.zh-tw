---
title: reader_writer_lock 類別
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376247"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock 類別

以寫入器偏好設定佇列為基礎且只能本機微調的讀取器-寫入器鎖定。 鎖定會授與寫入器先進先出 (FIFO) 存取權，並在連續載入寫入器的情況下影響讀取器。

## <a name="syntax"></a>語法

```cpp
class reader_writer_lock;
```

## <a name="members"></a>成員

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[reader_writer_lock::scoped_lock 類別](#scoped_lock_class)|可用於作為編寫器獲取`reader_writer_lock`鎖物件的異常安全 RAII 包裝器。|
|[reader_writer_lock::scoped_lock_read 類別](#scoped_lock_read_class)|可用於獲取`reader_writer_lock`鎖定物件作為讀取器的異常安全 RAII 包裝器。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[reader_writer_lock](#ctor)|建構新的 `reader_writer_lock` 物件。|
|[*reader_writer_lock析構函數](#dtor)|銷毀`reader_writer_lock`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[鎖定](#lock)|以編寫器身份獲取讀取器-寫入器鎖。|
|[lock_read](#lock_read)|獲取讀寫器鎖作為讀取器。 如果有作者,活躍的讀者必須等待,直到他們完成。 讀取器只需註冊對鎖的興趣,然後等待編寫器釋放它。|
|[try_lock](#try_lock)|嘗試取得讀取器-寫入器鎖作為編寫器而不阻塞。|
|[try_lock_read](#try_lock_read)|嘗試取得讀取器-寫入器鎖作為讀取器而不阻塞。|
|[解除鎖定](#unlock)|根據鎖定者、讀取器或編寫器來解鎖讀取器-寫入器鎖。|

## <a name="remarks"></a>備註

有關詳細資訊,請參閱[同步資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`reader_writer_lock`

## <a name="requirements"></a>需求

**標題:** concrt.h

**命名空間:** 併發

## <a name="lock"></a><a name="lock"></a>鎖

以編寫器身份獲取讀取器-寫入器鎖。

```cpp
void lock();
```

### <a name="remarks"></a>備註

利用[scoped_lock](#scoped_lock_class)建構以異常安全的方式獲取`reader_writer_lock`和釋放 物件作為編寫器通常更安全。

寫入器嘗試取得鎖定後，後續任何讀取器都會封鎖，直到寫入器成功取得及釋放鎖定為止。 這個鎖偏向於作家,在不斷的作家負載下,讀者可能餓死。

編寫器被連結,以便退出鎖的編寫器釋放行下一個寫入器。

如果調用上下文已持有鎖,將引發[improper_lock](improper-lock-class.md)異常。

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

獲取讀寫器鎖作為讀取器。 如果有作者,活躍的讀者必須等待,直到他們完成。 讀取器只需註冊對鎖的興趣,然後等待編寫器釋放它。

```cpp
void lock_read();
```

### <a name="remarks"></a>備註

利用[scoped_lock_read](#scoped_lock_read_class)構造以異常安全的方式獲取`reader_writer_lock`和釋放 物件作為讀取器通常更安全。

如果有寫入器等待鎖,讀取器將等待,直到所有行的寫入器都獲取並釋放鎖。 這個鎖偏向於作家,在不斷的作家負載下,讀者可能餓死。

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

建構新的 `reader_writer_lock` 物件。

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>*reader_writer_lock

銷毀`reader_writer_lock`物件。

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>備註

當析構函數運行時,預計鎖不再被持有。 允許讀取器編寫器鎖在鎖仍持有時析構會導致未定義的行為。

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock::scoped_lock類

可用於作為編寫器獲取`reader_writer_lock`鎖物件的異常安全 RAII 包裝器。

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock:scoped_lock

建構`scoped_lock`物件並獲取作為編寫器`reader_writer_lock`在`_Reader_writer_lock`參數中 傳遞的物件。 如果鎖由另一個線程持有,此調用將阻止。

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
作為`reader_writer_lock`編寫器獲取的物件。

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock:~scoped_lock

銷毀`reader_writer_lock`物件並釋放其構造函數中提供的鎖。

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock::scoped_lock_read類

可用於獲取`reader_writer_lock`鎖定物件作為讀取器的異常安全 RAII 包裝器。

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read:scoped_lock_read

建構`scoped_lock_read`物件並獲取作為讀取器`reader_writer_lock`在`_Reader_writer_lock`參數中 傳遞的物件。 如果鎖被另一個線程作為編寫器持有,或者存在掛起的寫入器,則此調用將阻止。

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>參數

*_Reader_writer_lock*<br/>
作為`reader_writer_lock`讀取器獲取的物件。

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock:::scoped_lock_read:*scoped_lock_read析構器

銷毀`scoped_lock_read`物件並釋放其構造函數中提供的鎖。

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

嘗試取得讀取器-寫入器鎖作為編寫器而不阻塞。

### <a name="syntax"></a>語法

```cpp
bool try_lock();
```

### <a name="return-value"></a>傳回值

如果取得了鎖,則值**為 true**;否則,該值**為 false**。

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

嘗試取得讀取器-寫入器鎖作為讀取器而不阻塞。

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>傳回值

如果取得了鎖,則值**為 true**;否則,該值**為 false**。

## <a name="unlock"></a><a name="unlock"></a>解除鎖定

根據鎖定者、讀取器或編寫器來解鎖讀取器-寫入器鎖。

```cpp
void unlock();
```

### <a name="remarks"></a>備註

如果有寫入器等待鎖,鎖的釋放將始終按 FIFO 順序轉到下一個寫入器。 這個鎖偏向於作家,在不斷的作家負載下,讀者可能餓死。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[critical_section 類別](critical-section-class.md)
